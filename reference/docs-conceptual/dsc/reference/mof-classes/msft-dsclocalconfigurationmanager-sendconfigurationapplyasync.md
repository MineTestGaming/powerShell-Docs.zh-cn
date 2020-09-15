---
ms.date: 07/17/2020
keywords: dsc,powershell,配置,安装程序
title: SendConfigurationApplyAsync 方法
ms.openlocfilehash: 4cfac5edb5fed94ee69deb98d7aa6be56b51c5b3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463731"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync 方法

将配置文档异步发送到托管节点，并使用配置代理应用配置。

## <a name="syntax"></a>语法

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>参数

ConfigurationData  \[in\]：配置的环境数据。

force  \[in\]：若为 true  ，则强制停止配置。

jobId  \[in\]：为其发送配置的作业的 ID。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
