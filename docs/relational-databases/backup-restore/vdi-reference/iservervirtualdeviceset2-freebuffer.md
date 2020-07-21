---
title: IServerVirtualDeviceSet2::FreeBuffer
titlesuffix: SQL Server VDI reference
description: この記事では、IServerVirtualDeviceSet2::FreeBuffer コマンドのリファレンスを提供します。
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1e7ac18a3a16d860b3fda7cfc26b0ab6733be4d0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895261"
---
# <a name="iservervirtualdeviceset2freebuffer-vdi"></a>IServerVirtualDeviceSet2::FreeBuffer (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

**FreeBuffer** 関数は、仮想デバイス セットから共有メモリ バッファーを取得します。

## <a name="syntax"></a>構文

```c
HRESULT IServerVirtualDeviceSet2::FreeBuffer (
   LPVOID   pBuffer,
   UINT32   dwSize
);
```

## <a name="parameters"></a>パラメーター

*pBuffer*: これは、IServerVirtualDeviceSet2::AllocateBuffer によって返されるバッファーを返します。

*dwSize*: これは、バッファーのサイズを取得します (バイト単位)。 これには、クライアントによって要求されたプレフィックス ゾーンは含まれません。 このようなゾーンはサーバーに表示されず、バッファー アドレスが返される前に使用可能な領域があります。

## <a name="return-value"></a>戻り値

|戻り値 | 説明 |
|---|---|
| NOERROR | バッファーが返されます。 |
| VD_E_INVALID | パラメーターが無効でした。 |

## <a name="next-steps"></a>次のステップ

詳細については、[SQL Server 仮想デバイス インターフェイス リファレンスの概要](reference-virtual-device-interface.md)に関するページを参照してください。