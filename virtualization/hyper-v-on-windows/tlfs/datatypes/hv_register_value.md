---
title: HV_REGISTER_VALUE
description: HV_REGISTER_VALUE
keywords: hyper-v
author: alexgrest
ms.author: alegre
ms.date: 10/15/2020
ms.topic: reference
ms.prod: windows-10-hyperv
ms.openlocfilehash: 6f83aec87169c2a6902bd8b8b361cd1a93c70b3b
ms.sourcegitcommit: d43632e3dc22e2b7a256b5c15fbb665c047de286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2020
ms.locfileid: "92121137"
---
# <a name="hv_register_value"></a>HV_REGISTER_VALUE

仮想プロセッサのレジスタ値のサイズはすべて128ビットです。 完全な128ビットを使用しない値は、128ビット全体を埋めるためにゼロ拡張されます。

## <a name="syntax"></a>構文

```c
typedef union
{
    UINT128 Reg128;
    UINT64 Reg64;
    UINT32 Reg32;
    UINT16 Reg16;
    UINT8 Reg8;
    HV_X64_FP_REGISTER Fp;
    HV_X64_FP_CONTROL_STATUS_REGISTER FpControlStatus;
    HV_X64_XMM_CONTROL_STATUS_REGISTER XmmControlStatus;
    HV_X64_SEGMENT_REGISTER Segment;
    HV_X64_TABLE_REGISTER Table;
    HV_EXPLICIT_SUSPEND_REGISTER ExplicitSuspend;
    HV_INTERCEPT_SUSPEND_REGISTER InterceptSuspend;
    HV_X64_INTERRUPT_STATE_REGISTER InterruptState;
    HV_X64_PENDING_INTERRUPTION_REGISTER PendingInterruption;
    HV_X64_MSR_NPIEP_CONFIG_CONTENTS NpiepConfig;
    HV_X64_PENDING_EXCEPTION_EVENT PendingExceptionEvent;
} HV_REGISTER_VALUE, *PHV_REGISTER_VALUE;
 ```