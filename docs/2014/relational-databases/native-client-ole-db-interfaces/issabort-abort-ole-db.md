---
title: Issabort::abort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05673bb90cd0958344a6a12550f15c122489219a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416291"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>コメント  
 中止されるコマンドがストアド プロシージャの場合、ストアド プロシージャ (およびそのプロシージャを呼び出したすべてのプロシージャ) の実行と、そのストアド プロシージャの呼び出しが含まれるコマンド バッチの実行が終了します。 サーバーがクライアントに結果セットを転送中の場合、この処理も停止します。 呼び出して、クライアントが結果セットを使用しない場合**issabort::abort**行セットの解放を高速化は、行セットを解放する前に、トランザクションはロールバックされます、開いているトランザクションがある場合、XACT_ABORT が ON と**Issabort::abort**が呼び出されます  
  
 後**issabort::abort** 、関連付けられている S_OK を返す**IMultipleResults**インターフェイスが使用できない状態に入るし、すべてのメソッド呼び出しに DB_E_CANCELED が返されます (、によって定義されたメソッドを除く**IUnknown**インターフェイス) が解放されるまでです。 場合、 **IRowset**から取得されていた**IMultipleResults**呼び出し前に**中止**も使用できない状態に入るし、すべてのメソッドに DB_E_CANCELED を返します呼び出し (、。によって定義されたメソッドを除く、 **IUnknown**インターフェイスと **::releaserows**) に成功した呼び出しの後に解放されるまで**issabort::abort**.  
  
> [!NOTE]  
>  以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]サーバーの XACT_ABORT 状態を実行する場合は、 **issabort::abort**が終了しに接続されているときに現在暗黙的または明示的なトランザクションはロールバック[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。  
  
## <a name="arguments"></a>引数  
 [なし] :  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 **Issabort::abort**メソッドは、バッチが取り消された場合 S_OK db_e_cantcancel をそれ以外の場合返します。 バッチが既に取り消されている場合は、DB_E_CANCELED を返します。  
  
 DB_E_CANCELED  
 バッチは既に取り消されています。  
  
 DB_E_CANTCANCEL  
 バッチは取り消されませんでした。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、使用、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイス。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、オブジェクトはゾンビ状態にため**issabort::abort**既に呼び出されています。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
