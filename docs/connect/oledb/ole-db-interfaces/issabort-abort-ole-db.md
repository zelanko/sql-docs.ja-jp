---
title: Issabort::abort (OLE DB) |Microsoft ドキュメント
description: ISSAbort::Abort (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0c7d30e8132d245958e7ef6f7f09e642a2da960c
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305381"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
**ISSAbort**が公開する OLE DB Driver for SQL Server、インターフェイスを提供、 **issabort::abort**コマンドを使用して、現在の行セットとどのようなコマンドをキャンセルに使用するメソッドがバッチ処理最初に、行セットを生成してをまだ完了していない実行します。  
  
 **ISSAbort**を使用して、OLE DB Driver for SQL Server に固有のインターフェイスがある**QueryInterface**上、 **IMultipleResults**によって返されるオブジェクト**icommand::execute**または**iopenrowset::openrowset**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>コメント  
 中止中のコマンドは、ストアド プロシージャでは、コマンドのバッチ、ストアド プロシージャ呼び出しを含むだけでなく、ストアド プロシージャ (およびそのプロシージャでは、そのプロシージャを呼び出す必要がある) の実行が終了されます。 サーバーがクライアントに結果セットを転送中の場合は、転送が停止されます。 クライアントがいない場合、結果セットを使用する、呼び出し**issabort::abort**行セットの解放を高速化は、行セットを解放する前に、トランザクションはロールバックされます、開いているトランザクションが存在しないと、XACT_ABORT が ON、ときにコールバック**issabort::abort**は呼び出されます  
  
 後に**issabort::abort** 、関連付けられている S_OK を返す**IMultipleResults**インターフェイスが使用できない状態になるし、すべてのメソッド呼び出しに DB_E_CANCELED が返されます (、によって定義されたメソッドを除く**IUnknown**インターフェイス) が解放されるまでです。 場合、 **IRowset**から取得されていた**IMultipleResults**呼び出しの前に**中止**、また使用不可の状態を入力し、すべてのメソッド呼び出しに DB_E_CANCELED が返されます (によって定義されたメソッドを除く、 **IUnknown**インターフェイスと**irowset::releaserows**) に正常な呼び出しの後に解放されるまで**issabort::abort**です。  
  
> [!NOTE]  
>  以降で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]サーバーの XACT_ABORT 状態を実行する場合は、 **issabort::abort**が終了しに接続しているときに現在暗黙的または明示的なトランザクションはロールバック[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。  
  
## <a name="arguments"></a>引数  
 [なし] :  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 **Issabort::abort**メソッドを返します db_e_cantcancel、バッチが取り消された場合は S_OK、それ以外の場合。 バッチが既に取り消されている場合は、DB_E_CANCELED を返します。  
  
 DB_E_CANCELED  
 バッチは既に取り消されています。  
  
 DB_E_CANTCANCEL  
 バッチは取り消されませんでした。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細についてを使用して、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、オブジェクトはゾンビ状態にため**issabort::abort**は既に呼び出されています。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
  
