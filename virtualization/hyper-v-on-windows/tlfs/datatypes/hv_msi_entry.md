---
title: HV_MSI_ENTRY
description: HV_MSI_ENTRY
keywords: hyper-v
author: alexgrest
ms.author: alegre
ms.date: 10/15/2020
ms.topic: reference
ms.prod: windows-10-hyperv
ms.openlocfilehash: c58917eec730f41a1c986d04115f1a7c8037734b
ms.sourcegitcommit: d43632e3dc22e2b7a256b5c15fbb665c047de286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2020
ms.locfileid: "92121150"
---
# <a name="hv_msi_entry"></a>HV_MSI_ENTRY

## <a name="syntax"></a>構文

 ```c
typedef union
{
    UINT64 AsUINT64;
    struct
    {
        UINT32 Address;
        UINT32 Data;
    };
} HV_MSI_ENTRY;
 ```