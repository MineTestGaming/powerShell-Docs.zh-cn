---
ms.date: 07/17/2020
keywords: dsc,powershell,配置,安装程序
title: GetConfigurationStatus 方法
ms.openlocfilehash: c2c478151428052d656832fb4079f12d666a910d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464038"
---
# <a name="getconfigurationstatus-method"></a>GetConfigurationStatus 方法

获取配置状态历史记录。

## <a name="syntax"></a>语法

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>参数

All  \[in\]：如果此方法应返回计算机上运行的所有配置的相关信息（包括配置应用程序和一致性检查），则为 true  。

configurationStatus  \[out\]：返回响应时，包含定义设置的 MSFT_DSCConfigurationStatus  类的嵌入实例。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
