---
ms.date: 07/17/2020
keywords: dsc,powershell,配置,安装程序
title: SendConfigurationApply 方法
ms.openlocfilehash: 9b684790e5a7d6c7bdf074caca6040e13807f1ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464309"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="43982-103">SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="43982-103">SendConfigurationApply method</span></span>

<span data-ttu-id="43982-104">将配置文档发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="43982-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="43982-105">语法</span><span class="sxs-lookup"><span data-stu-id="43982-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="43982-106">参数</span><span class="sxs-lookup"><span data-stu-id="43982-106">Parameters</span></span>

<span data-ttu-id="43982-107">ConfigurationData  \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="43982-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="43982-108">force  \[in\]：若为 true  ，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="43982-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="43982-109">返回值</span><span class="sxs-lookup"><span data-stu-id="43982-109">Return value</span></span>

<span data-ttu-id="43982-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="43982-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="43982-111">备注</span><span class="sxs-lookup"><span data-stu-id="43982-111">Remarks</span></span>

<span data-ttu-id="43982-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="43982-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="43982-113">要求</span><span class="sxs-lookup"><span data-stu-id="43982-113">Requirements</span></span>

<span data-ttu-id="43982-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="43982-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="43982-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="43982-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="43982-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43982-116">See also</span></span>

[<span data-ttu-id="43982-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="43982-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
