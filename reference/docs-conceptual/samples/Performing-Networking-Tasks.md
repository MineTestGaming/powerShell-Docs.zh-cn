---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 执行网络任务
description: 本文介绍如何使用 PowerShell 中的 WMI 类来管理 Windows 中的网络配置设置。
ms.openlocfilehash: 95b05c193f4168cdcdf8414399c4f8c569bff754
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500243"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="c2992-104">执行网络任务</span><span class="sxs-lookup"><span data-stu-id="c2992-104">Performing Networking Tasks</span></span>

<span data-ttu-id="c2992-105">由于 TCP/IP 是最常用的网络协议，因此大多数低级别网络协议管理任务都涉及 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="c2992-105">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="c2992-106">在本部分中，我们使用 PowerShell 和 WMI 来执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="c2992-106">In this section, we use PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="c2992-107">列出计算机的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="c2992-107">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="c2992-108">若要获取本地计算机上使用的所有 IP 地址，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="c2992-108">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

<span data-ttu-id="c2992-109">此命令的输出与大多数属性列表不同，因为值括在大括号中：</span><span class="sxs-lookup"><span data-stu-id="c2992-109">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

<span data-ttu-id="c2992-110">若要了解大括号出现的原因，请使用 `Get-Member` cmdlet 检查 IPAddress  属性：</span><span class="sxs-lookup"><span data-stu-id="c2992-110">To understand why the braces appear, use the `Get-Member` cmdlet to examine the **IPAddress** property:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

<span data-ttu-id="c2992-111">每个网络适配器的 IPAddress 属性实际上是一个数组。</span><span class="sxs-lookup"><span data-stu-id="c2992-111">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="c2992-112">定义中的大括号指示 **IPAddress** 不是 **System.String** 值，而是由 **System.String** 值组成的数组。</span><span class="sxs-lookup"><span data-stu-id="c2992-112">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="c2992-113">列出 IP 配置数据</span><span class="sxs-lookup"><span data-stu-id="c2992-113">Listing IP Configuration Data</span></span>

<span data-ttu-id="c2992-114">若要显示每个网络适配器的详细 IP 配置数据，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="c2992-114">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

<span data-ttu-id="c2992-115">网络适配器配置对象的默认显示为一组非常精简的可用信息。</span><span class="sxs-lookup"><span data-stu-id="c2992-115">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="c2992-116">对于深入检查和疑难解答，请使用 `Select-Object` 或格式设置 cmdlet（例如 `Format-List`）来指定要显示的属性。</span><span class="sxs-lookup"><span data-stu-id="c2992-116">For in-depth inspection and troubleshooting, use `Select-Object` or a formatting cmdlet, such as `Format-List`, to specify the properties to be displayed.</span></span>

<span data-ttu-id="c2992-117">在新式 TCP/IP 网络中，你可能对 IPX 或 WINS 属性不感兴趣。</span><span class="sxs-lookup"><span data-stu-id="c2992-117">In modern TCP/IP networks you are probably not interested in IPX or WINS properties.</span></span> <span data-ttu-id="c2992-118">可以使用 `Select-Object` 的 ExcludeProperty  参数隐藏以“WINS”或“IPX”名称开头的属性。</span><span class="sxs-lookup"><span data-stu-id="c2992-118">You can use the **ExcludeProperty** parameter of `Select-Object` to hide properties with names that begin with "WINS" or "IPX".</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="c2992-119">此命令返回有关 DHCP、DNS、路由以及其他次要 IP 配置属性的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c2992-119">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="c2992-120">Ping 计算机</span><span class="sxs-lookup"><span data-stu-id="c2992-120">Pinging Computers</span></span>

<span data-ttu-id="c2992-121">你可以使用 **Win32_PingStatus** 对计算机执行简单的 Ping 操作。</span><span class="sxs-lookup"><span data-stu-id="c2992-121">You can perform a simple ping against a computer using by **Win32_PingStatus** .</span></span> <span data-ttu-id="c2992-122">下面的命令执行 Ping 操作，但返回冗长的输出：</span><span class="sxs-lookup"><span data-stu-id="c2992-122">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

<span data-ttu-id="c2992-123">摘要信息是更为有用的形式，它显示下面的命令生成的 Address、ResponseTime 以及 StatusCode 属性。</span><span class="sxs-lookup"><span data-stu-id="c2992-123">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="c2992-124">`Format-Table` 的 Autosize  参数调整表列的大小，以使其正确显示在 PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="c2992-124">The **Autosize** parameter of `Format-Table` resizes the table columns so that they display properly in PowerShell.</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="c2992-125">如果 StatusCode 为 0，指明 ping 操作成功。</span><span class="sxs-lookup"><span data-stu-id="c2992-125">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="c2992-126">你可以使用数组借助单个命令对计算机执行 Ping 操作。</span><span class="sxs-lookup"><span data-stu-id="c2992-126">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="c2992-127">由于存在多个地址，因此请使用 `ForEach-Object` 单独对每个地址执行 Ping 操作：</span><span class="sxs-lookup"><span data-stu-id="c2992-127">Because there is more than one address, use the `ForEach-Object` to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

<span data-ttu-id="c2992-128">可以使用相同的命令格式对一个子网（例如使用网络号码 (192.168.1.0) 和标准 C 类子网掩码 (255.255.255.0) 的专用网）上的所有计算机执行 Ping 操作。仅在 192.168.1.1 到 192.168.1.254 范围内的地址为合法本地地址（0 始终为网络号码保留，255 是子网广播地址）。</span><span class="sxs-lookup"><span data-stu-id="c2992-128">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="c2992-129">若要在 PowerShell 中表示从 1 到 254 范围内的数字数组，请使用语句 **1..254** 。</span><span class="sxs-lookup"><span data-stu-id="c2992-129">To represent an array of the numbers from 1 through 254 in PowerShell, use the statement **1..254.**</span></span>
<span data-ttu-id="c2992-130">可以通过生成数组，然后将值添加到 ping 语句中的部分地址上，执行完整的子网 Ping 操作：</span><span class="sxs-lookup"><span data-stu-id="c2992-130">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="c2992-131">请注意，这一用于生成一系列地址的方法也可用于其他地方。</span><span class="sxs-lookup"><span data-stu-id="c2992-131">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="c2992-132">你可以使用以下方式生成完整的地址集：</span><span class="sxs-lookup"><span data-stu-id="c2992-132">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="c2992-133">检索网络适配器属性</span><span class="sxs-lookup"><span data-stu-id="c2992-133">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="c2992-134">在前面部分中，我们提到过你可以使用 Win32_NetworkAdapterConfiguration  类来检索常规配置属性。</span><span class="sxs-lookup"><span data-stu-id="c2992-134">Earlier, we mentioned that you could retrieve general configuration properties using the **Win32_NetworkAdapterConfiguration** class.</span></span> <span data-ttu-id="c2992-135">尽管不是严格的 TCP/IP 信息，但网络适配器信息（例如 MAC 地址和适配器类型）也可用于了解计算机的运行情况。</span><span class="sxs-lookup"><span data-stu-id="c2992-135">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="c2992-136">若要获取此信息的摘要，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="c2992-136">To get a summary of this information, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="c2992-137">为网络适配器分配 DNS 域</span><span class="sxs-lookup"><span data-stu-id="c2992-137">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="c2992-138">若要分配 DNS 域以便进行自动名称解析，请使用 Win32_NetworkAdapterConfiguration  的 SetDNSDomain  方法。</span><span class="sxs-lookup"><span data-stu-id="c2992-138">To assign the DNS domain for automatic name resolution, use the **SetDNSDomain** method of the **Win32_NetworkAdapterConfiguration** .</span></span> <span data-ttu-id="c2992-139">由于你单独为每个网络适配器配置分配 DNS 域，因此需要使用 `ForEach-Object` 语句将域分配给每个适配器：</span><span class="sxs-lookup"><span data-stu-id="c2992-139">Because you assign the DNS domain for each network adapter configuration independently, you need to use a `ForEach-Object` statement to assign the domain to each adapter:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="c2992-140">筛选语句 `IPEnabled=$true` 是必需的，因为即使是在仅使用 TCP/IP 的网络上，计算机上的多个网络适配器配置也不是真正的 TCP/IP 适配器；它们是支持 RAS、PPTP、QoS 和其他适用于所有适配器的服务的常规软件元素，因此没有自己的地址。</span><span class="sxs-lookup"><span data-stu-id="c2992-140">The filtering statement `IPEnabled=$true` is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="c2992-141">可以使用 `Where-Object` cmdlet，而不是使用 `Get-CimInstance` 筛选器筛选命令。</span><span class="sxs-lookup"><span data-stu-id="c2992-141">You can filter the command by using the `Where-Object` cmdlet, instead of using the `Get-CimInstance` filter.</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="c2992-142">执行 DHCP 配置任务</span><span class="sxs-lookup"><span data-stu-id="c2992-142">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="c2992-143">修改 DHCP 详细信息需处理一组网络适配器，与 DNS 配置的操作相同。</span><span class="sxs-lookup"><span data-stu-id="c2992-143">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="c2992-144">你可通过使用 WMI 执行多种不同的操作，我们将逐步介绍一些常见操作。</span><span class="sxs-lookup"><span data-stu-id="c2992-144">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="c2992-145">确定启用 DHCP 的适配器</span><span class="sxs-lookup"><span data-stu-id="c2992-145">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="c2992-146">若要查找计算机上启用了 DHCP 的适配器，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="c2992-146">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

<span data-ttu-id="c2992-147">若要排除有IP 配置问题的适配器，可以仅检索已启用 IP 的适配器：</span><span class="sxs-lookup"><span data-stu-id="c2992-147">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="c2992-148">检索 DHCP 属性</span><span class="sxs-lookup"><span data-stu-id="c2992-148">Retrieving DHCP Properties</span></span>

<span data-ttu-id="c2992-149">因为适配器的 DHCP 相关属性通常以“`DHCP`”开头，所以你可使用 `Format-Table` 的 Property 参数来仅显示那些属性：</span><span class="sxs-lookup"><span data-stu-id="c2992-149">Because DHCP-related properties for an adapter generally begin with `DHCP`, you can use the Property parameter of `Format-Table` to display only those properties:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="c2992-150">在每个适配器上启用 DHCP</span><span class="sxs-lookup"><span data-stu-id="c2992-150">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="c2992-151">若要在所有适配器上启用 DHCP，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="c2992-151">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="c2992-152">可以使用 Filter  语句“`IPEnabled=$true and DHCPEnabled=$false`”来避免在已启用 DHCP 的适配器上再次启用，但忽略此步骤不会导致出现错误。</span><span class="sxs-lookup"><span data-stu-id="c2992-152">You can use the **Filter** statement `IPEnabled=$true and DHCPEnabled=$false` to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="c2992-153">释放和续订特定适配器上的 DHCP 租约</span><span class="sxs-lookup"><span data-stu-id="c2992-153">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="c2992-154">**Win32_NetworkAdapterConfiguration** 类具有 **ReleaseDHCPLease** 和 **RenewDHCPLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="c2992-154">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="c2992-155">这两种方法的使用方式相同。</span><span class="sxs-lookup"><span data-stu-id="c2992-155">Both are used in the same way.</span></span> <span data-ttu-id="c2992-156">一般情况下，在仅需释放或续订特定子网上的适配器地址时使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="c2992-156">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="c2992-157">在子网上筛选器适配器的最简单方法是仅选择使用该子网的网关的适配器配置。</span><span class="sxs-lookup"><span data-stu-id="c2992-157">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="c2992-158">例如，下面的命令释放本地计算机上适配器上的所有 DHCP 租约，这些适配器正在从 192.168.1.254 获得 DHCP 租约：</span><span class="sxs-lookup"><span data-stu-id="c2992-158">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="c2992-159">续订 DHCP 租约的唯一更改是使用 **RenewDHCPLease** 方法，而不是 **ReleaseDHCPLease** 方法：</span><span class="sxs-lookup"><span data-stu-id="c2992-159">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="c2992-160">在远程计算机上使用这些方法时，请注意，如果你通过已释放或已续订租约的适配器连接到远程系统，则可能会失去对该系统的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c2992-160">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="c2992-161">释放和续订所有适配器上的 DHCP 租约</span><span class="sxs-lookup"><span data-stu-id="c2992-161">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="c2992-162">可以通过使用 **Win32_NetworkAdapterConfiguration** 方法、 **ReleaseDHCPLeaseAll** 和 **RenewDHCPLeaseAll** 对所有适配器指定全局 DHCP 地址释放或续订。</span><span class="sxs-lookup"><span data-stu-id="c2992-162">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll** .</span></span>
<span data-ttu-id="c2992-163">但是，该命令必须适用于 WMI 类，而不是特定的适配器，因为全局释放和续订租约是对该类执行的，而不是对特定适配器执行的。</span><span class="sxs-lookup"><span data-stu-id="c2992-163">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="c2992-164">可以通过列出所有 WMI 类，然后按名称仅选择所需类来获取对 WMI 类而不是类实例的引用。</span><span class="sxs-lookup"><span data-stu-id="c2992-164">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="c2992-165">例如，下面的命令将返回 Win32_NetworkAdapterConfiguration  类：</span><span class="sxs-lookup"><span data-stu-id="c2992-165">For example, the following command returns the **Win32_NetworkAdapterConfiguration** class:</span></span>

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="c2992-166">可以将整个命令视为类，并在其上调用 **ReleaseDHCPAdapterLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="c2992-166">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="c2992-167">在下面的命令中，`Get-CimInstance` 和 `Where-Object` 管道元素两边的括号指示 PowerShell 先对其进行评估：</span><span class="sxs-lookup"><span data-stu-id="c2992-167">In the following command, the parentheses surrounding the `Get-CimInstance` and `Where-Object` pipeline elements direct PowerShell to evaluate them first:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="c2992-168">可以使用相同的命令格式来调用 **RenewDHCPLeaseAll** 方法：</span><span class="sxs-lookup"><span data-stu-id="c2992-168">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="c2992-169">创建网络共享</span><span class="sxs-lookup"><span data-stu-id="c2992-169">Creating a Network Share</span></span>

<span data-ttu-id="c2992-170">若要创建网络共享，请使用 Win32_Share  的 Create  方法：</span><span class="sxs-lookup"><span data-stu-id="c2992-170">To create a network share, use the **Create** method of **Win32_Share** :</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

<span data-ttu-id="c2992-171">还可以在 Windows 上的 PowerShell 中使用 `net share` 来创建共享：</span><span class="sxs-lookup"><span data-stu-id="c2992-171">You can also create the share by using `net share` in PowerShell on Windows:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="c2992-172">删除网络共享</span><span class="sxs-lookup"><span data-stu-id="c2992-172">Removing a Network Share</span></span>

<span data-ttu-id="c2992-173">可以使用 **Win32_Share** 删除网络共享，但是该过程与创建共享略有不同，因为需要检索要删除的特定共享，而不是 **Win32_Share** 类。</span><span class="sxs-lookup"><span data-stu-id="c2992-173">You can remove a network share with **Win32_Share** , but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="c2992-174">下面的语句删除共享 TempShare  ：</span><span class="sxs-lookup"><span data-stu-id="c2992-174">The following statement deletes the share **TempShare** :</span></span>

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="c2992-175">在 Windows 中，`net share` 也可实现此操作：</span><span class="sxs-lookup"><span data-stu-id="c2992-175">In Windows, `net share` works as well:</span></span>

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="c2992-176">连接 Windows 可访问网络驱动器</span><span class="sxs-lookup"><span data-stu-id="c2992-176">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="c2992-177">`New-PSDrive` cmdlet 可创建 PowerShell 驱动器，但使用这种方法创建的驱动器仅适用于 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c2992-177">The `New-PSDrive` cmdlets creates a PowerShell drive, but drives created this way are available only to PowerShell.</span></span> <span data-ttu-id="c2992-178">若要创建新的联网驱动器，可以使用 **WScript.Network** COM 对象。</span><span class="sxs-lookup"><span data-stu-id="c2992-178">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="c2992-179">下面的命令将共享 `\\FPS01\users` 映射到本地驱动器 `B:`，</span><span class="sxs-lookup"><span data-stu-id="c2992-179">The following command maps the share `\\FPS01\users` to local drive `B:`,</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="c2992-180">在 Windows 上，`net use` 命令也可实现此操作：</span><span class="sxs-lookup"><span data-stu-id="c2992-180">On Windows, the `net use` command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="c2992-181">使用 WScript.Network  或 `net use` 映射的驱动器可立即用于 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c2992-181">Drives mapped with either **WScript.Network** or `net use` are immediately available to PowerShell.</span></span>
