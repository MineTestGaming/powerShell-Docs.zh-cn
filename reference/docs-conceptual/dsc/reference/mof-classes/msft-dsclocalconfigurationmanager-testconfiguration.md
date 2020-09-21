---
ms.date: 07/17/2020
keywords: dsc,powershell,配置,安装程序
title: TestConfiguration 方法
ms.openlocfilehash: 0611c4d5543c49b879bef9b60cafdd0b055c9b86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464292"
---
# <a name="testconfiguration-method"></a>TestConfiguration 方法

将配置文档发送到托管节点并针对该文档验证当前配置。

## <a name="syntax"></a>语法

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>参数

**configurationData** \[in\] 配置的环境数据。

InDesiredState  \[out\]：返回响应时，指定托管节点是否处于配置文档指定的状态。

ResourcesInDesiredState  \[out\]：返回响应时，包含 MSFT_ResourceInDesiredState  类的嵌入实例，此类指定处于所需状态的资源。

ResourcesNotInDesiredState  \[out\]：返回响应时，包含 MSFT_ResourceNotInDesiredState  类的嵌入实例，此类指定不处于所需状态的资源。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
