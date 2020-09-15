---
ms.date: 07/17/2020
keywords: dsc,powershell,配置,安装程序
title: GetMetaConfiguration 方法
ms.openlocfilehash: 5111cb3b15e0fba0bf71b412580efdd3cd95b2dc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463969"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="8f56a-103">GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="8f56a-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="8f56a-104">获取用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="8f56a-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f56a-105">语法</span><span class="sxs-lookup"><span data-stu-id="8f56a-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="8f56a-106">参数</span><span class="sxs-lookup"><span data-stu-id="8f56a-106">Parameters</span></span>

<span data-ttu-id="8f56a-107">MetaConfiguration  \[out\]：返回响应时，包含定义设置的 MSFT_DSCMetaConfiguration  类的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="8f56a-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f56a-108">返回值</span><span class="sxs-lookup"><span data-stu-id="8f56a-108">Return value</span></span>

<span data-ttu-id="8f56a-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="8f56a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f56a-110">备注</span><span class="sxs-lookup"><span data-stu-id="8f56a-110">Remarks</span></span>

<span data-ttu-id="8f56a-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="8f56a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f56a-112">要求</span><span class="sxs-lookup"><span data-stu-id="8f56a-112">Requirements</span></span>

<span data-ttu-id="8f56a-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8f56a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8f56a-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f56a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8f56a-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f56a-115">See also</span></span>

[<span data-ttu-id="8f56a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8f56a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
