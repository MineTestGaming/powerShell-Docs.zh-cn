---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理服务
description: PowerShell 提供了多个 cmdlet，可帮助管理本地和远程计算机上的服务。
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500345"
---
# <a name="managing-services"></a>管理服务

有八个专为各种服务任务设计的核心 Service cmdlet。 我们仅会列出和更改服务的运行状态，但你可以使用 `Get-Help \*-Service` 获取服务 cmdlet 列表并通过使用 `Get-Help <Cmdlet-Name>`（例如 `Get-Help New-Service`）找到每个服务 cmdlet 的相关信息。

## <a name="getting-services"></a>获取服务

可以通过使用 `Get-Service` cmdlet 获取本地或远程计算机上的服务。 与使用 `Get-Process` 相同，使用不带参数的 `Get-Service` 命令将返回所有服务。 你可以按名称进行筛选，甚至可以使用星号作为通配符：

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

因为服务的真实名称并不总是可见，所以你可能会发现你需要按显示名称查找服务。 可以按特定名称（使用通配符或使用显示名称的列表）执行此操作：

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

可以使用 Get-Service cmdlet 的 ComputerName 参数获取远程计算机上的服务。 ComputerName 参数接受多个值和通配符，因此你可以使用单个命令获取多台计算机上的服务。 例如，下面的命令获取 Server01 远程计算机上的服务。

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>获取必需和从属服务

Get-Service cmdlet 具有两个在服务管理中非常有用的参数。 DependentServices 参数获取依赖于该服务的服务。 RequiredServices 参数获取此服务所依赖的服务。

这些参数只显示 Get-Service 返回的 System.ServiceProcess.ServiceController 对象的 DependentServices 和 ServicesDependedOn (alias=RequiredServices) 属性的值，但是它们可简化命令，使获取此信息更加简单。

下面的命令获取 LanmanWorkstation 服务需要的服务。

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

下面的命令获取需要 LanmanWorkstation 服务的服务。

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

你甚至可以获取所有具有依赖关系的服务。 下面的命令所做的就是这些，然后使用 Format-Table cmdlet 来显示计算机上服务的 Status、Name、RequiredServices 和 DependentServices 属性。

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>停止、启动、暂停和重启服务

所有 Service cmdlet 都具有相同的一般形式。 可以按公用名或显示名称指定服务，并使用列表和通配符作为值。 若要停止打印后台处理程序，请使用：

```powershell
Stop-Service -Name spooler
```

若要在停止后启动打印后台处理程序，请使用：

```powershell
Start-Service -Name spooler
```

若要暂停打印后台处理程序，请使用：

```powershell
Suspend-Service -Name spooler
```

虽然 `Restart-Service` cmdlet 的操作方式与其他 Service cmdlet 的操作方式相同，但是我们将针对它列举一些更复杂的示例。 使用最简单的方式指定服务的名称：

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

你将注意到你收到了有关打印后台处理程序启动的重复警告消息。 执行需要耗费一些时间的服务操作时，Windows PowerShell 将通知你它仍在尝试执行该任务。

如果想要重启多个服务，则可获取服务列表，并对其进行筛选，然后执行重启操作：

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

虽然这些 Service cmdlet 没有 ComputerName 参数，但是你可通过使用 Invoke-Command cmdlet 在远程计算机上运行它们。 例如，下面的命令在 Server01 远程计算机上重启后台打印程序服务。

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>设置服务属性

`Set-Service` cmdlet 更改本地或远程计算机上服务的属性。 因为服务状态是一种属性，所以你可以使用此 cmdlet 来启动、停止和暂停服务。
Set-Service cmdlet 还有一个 StartupType 参数，可让你更改服务启动类型。

若要在 Windows Vista 和 Windows 的更高版本上使用 `Set-Service`，请使用“以管理员身份运行”选项打开 Windows PowerShell。

有关详细信息，请参阅 [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)

## <a name="see-also"></a>另请参阅

- [Get-Service](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [Restart-Service](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [Suspend-Service](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
