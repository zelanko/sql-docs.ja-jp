---
title: IClientVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: この記事では、IClientVirtualDeviceSet2::GetConfiguration コマンドのリファレンスを提供します。
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 52dcbd2e2218da289d447b16d29460ff3f5af977
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896885"
---
# <a name="iclientvirtualdeviceset2getconfiguration-vdi"></a>IClientVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

**GetConfiguration** 関数は、サーバーによって仮想デバイス セットが構成されるのを待機するために使用されます。

## <a name="syntax"></a>構文

```c
HRESULT IClientVirtualDeviceSet2::GetConfiguration (
   DWORD         dwTimeOut,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>パラメーター

*DwTimeOut*: これはミリ秒単位のタイムアウト値です。 タイムアウトを防ぐには、INFINITE を使用します。

*pCfg*: 正常に実行されると、サーバーによって選択された構成がこの引数に格納されます。 詳細については、「構成」に関する記事を参照してください。

## <a name="return-value"></a>戻り値

|戻り値 | 説明 |
|---|---|
| NOERROR | 構成が返されました。 |
| VD_E_ABORT | SignalAbort が呼び出されました。 |
| VD_E_TIMEOUT | 関数がタイムアウトしました。 |

## <a name="remarks"></a>解説

この関数は、警告可能な状態でブロックします。 呼び出しが正常に終了すると、仮想デバイス セット内のデバイスを開くことができます。

## <a name="next-steps"></a>次のステップ

詳細については、[SQL Server 仮想デバイス インターフェイス リファレンスの概要](reference-virtual-device-interface.md)に関するページを参照してください。