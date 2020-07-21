---
title: IClientVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: この記事では、IClientVirtualDeviceSet2::SignalAbort コマンドのリファレンスを提供します。
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ec46b61b89f19c568dc924f5651e9bb544a63ca9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896844"
---
# <a name="iclientvirtualdeviceset2signalabort-vdi"></a>IClientVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

**SignalAbort** 関数は、異常終了が発生することを通知するために使用されます。

## <a name="syntax"></a>構文

```c
HRESULT IClientVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>戻り値

メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 NOERROR は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。

## <a name="remarks"></a>解説

クライアントでは、バックアップ操作または復元操作をいつでも中止できます。 このルーチンは、すべての操作を中止する必要があることを通知するものです。 仮想デバイス セット全体の状態が、中止状態になります。 後続のコマンドは、いずれのデバイスについても返されません。 未完了のコマンドはすべて自動的に完了し、完了コードとして ERROR_OPERATION_ABORTED が返されます。 クライアントでは、クライアントに提供されたバッファーの未処理の使用を安全に終了した後、IClientVirtualDeviceSet2::Close を呼び出す必要があります。 詳細については、「異常終了」に関する記事を参照してください。

## <a name="next-steps"></a>次のステップ

詳細については、[SQL Server 仮想デバイス インターフェイス リファレンスの概要](reference-virtual-device-interface.md)に関するページを参照してください。