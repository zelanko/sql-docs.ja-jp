---
title: Issabort::abort (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0729183a2e5be91d3cdb30eae3ae5990f8398103
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164072"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>コメント  
 中止されるコマンドがストアド プロシージャの場合、ストアド プロシージャ (およびそのプロシージャを呼び出したすべてのプロシージャ) の実行と、そのストアド プロシージャの呼び出しが含まれるコマンド バッチの実行が終了します。 サーバーがクライアントに結果セットを転送中の場合、この処理も停止します。 クライアントがいない場合、結果セットを使用する、呼び出し**issabort::abort**行セットの解放を高速化は、行セットを解放する前に、トランザクションはロールバックされます、開いているトランザクションが存在しないと、XACT_ABORT が ON、ときに**Issabort::abort**は呼び出されます  
  
 後に**issabort::abort** 、関連付けられている S_OK を返す**IMultipleResults**インターフェイスが使用できない状態になるし、すべてのメソッド呼び出しに DB_E_CANCELED が返されます (、によって定義されたメソッドを除く**IUnknown**インターフェイス) が解放されるまでです。 場合、 **IRowset**から取得されていた**IMultipleResults**呼び出しの前に**中止**、また、使用できない状態に入るし、すべてのメソッドに DB_E_CANCELED を返します (の呼び出しによって定義されたメソッドを除く、 **IUnknown**インターフェイスと**irowset::releaserows**) に正常な呼び出しの後に解放されるまで**issabort::abort**.  
  
> [!NOTE]  
>  以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]サーバーの XACT_ABORT 状態を実行する場合は、 **issabort::abort**が終了しに接続しているときに現在暗黙的または明示的なトランザクションはロールバック[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。  
  
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
 プロバイダー固有のエラーが発生しました。詳細についてを使用して、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、オブジェクトはゾンビ状態にため**issabort::abort**は既に呼び出されています。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  