---
title: Issabort::abort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 90fdb17506d624e5210288716736ae29721c0feb
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431261"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
**ISSAbort**で公開される、インターフェイス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、提供、 **issabort::abort**現在の行セットと任意のコマンドをキャンセルするために使用するメソッドがバッチ処理最初に、行セットを生成してをまだ完了していない実行コマンド。  
  
 **ISSAbort**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client プロバイダーに固有のインターフェイスを使用して利用可能な**QueryInterface**上、 **IMultipleResults**によって返されるオブジェクト**Icommand::execute**または**iopenrowset::openrowset**します。  
  
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
 プロバイダー固有のエラーが発生しました。詳細については、使用、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイス。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、オブジェクトはゾンビ状態にため**issabort::abort**既に呼び出されています。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [ISSAbort &#40;OLE DB&#41;](http://msdn.microsoft.com/library/7c4df482-4a83-4da0-802b-3637b507693a)  
  
  
