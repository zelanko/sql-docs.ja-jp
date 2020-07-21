---
title: IServerVirtualDevice::CloseDevice
titlesuffix: SQL Server VDI reference
description: この記事では、IServerVirtualDevice::CloseDevice コマンドのリファレンスを提供します。
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3e9ff54c500b626d667622105a39e742c5e2a339
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896831"
---
# <a name="iservervirtualdeviceclosedevice-vdi"></a>IServerVirtualDevice::CloseDevice (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

**CloseDevice** 関数は、IServerVirtualDeviceSet2::OpenDevice で開かれた仮想デバイスを閉じます。

## <a name="syntax"></a>構文

```c
HRESULT IServerVirtualDevice::CloseDevice ();
```

## <a name="return-value"></a>戻り値

|戻り値 | 説明 |
|---|---|
| VD_E_CLOSE | デバイスは既に閉じられています。 |
| VD_E_ABORT | インターフェイスは中止状態です。 |

## <a name="remarks"></a>解説

異常終了を強制するために SignalAbort を使用すると、CloseDevice は不要になります。 SignalAbort が使用された後に CloseDevice が呼び出された場合、何のアクションも実行されません。

## <a name="next-steps"></a>次のステップ

詳細については、[SQL Server 仮想デバイス インターフェイス リファレンスの概要](reference-virtual-device-interface.md)に関するページを参照してください。