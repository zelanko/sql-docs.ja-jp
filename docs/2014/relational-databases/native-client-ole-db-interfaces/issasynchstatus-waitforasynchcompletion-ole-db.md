---
title: Issasynchstatus::waitforasynchcompletion (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5c8b2bf4b7ffbc3a478dc872a32053799b6419b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165859"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
  非同期で実行している操作が完了するまで、またはタイムアウトが発生するまで待機します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>引数  
 *dwMillisecTimeOut*[in]  
 ミリ秒単位のタイムアウト。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_UNEXPECTED  
 に、行セットが使用されていない状態では**itransaction::commit**または**itransaction::abort**が呼び出されたか、初期化フェーズ中に、行セットが取り消されました。  
  
 DB_E_CANCELED  
 行セットの設定中またはデータ ソース オブジェクトの初期化中に、非同期処理が取り消されました。  
  
 DB_S_ASYNCHRONOUS  
 指定したタイムアウトに達しても、操作が完了していません。  
  
> [!NOTE]  
>  上記のリターン コード値に加えて、 **issasynchstatus::waitforasynchcompletion**メソッドには、主要な OLEDB によって返されるリターン コード値もサポートしています**icommand::execute**と**Idbinitialize::initialize**メソッドです。  
  
## <a name="remarks"></a>コメント  
 **Issasynchstatus::waitforasynchcompletion**メソッドは、タイムアウト値 (ミリ秒単位) が経過するか、保留中の操作が完了するまでは返されません。 **コマンド**オブジェクトには、 **CommandTimeout**秒数を制御するプロパティ、クエリは、タイムアウト前に実行されます。**CommandTimeout**と組み合わせて使用する場合、プロパティは無視されます**issasynchstatus::waitforasynchcompletion**メソッドです。  
  
 非同期操作では、タイムアウト プロパティが無視されます。 タイムアウト パラメーター **issasynchstatus::waitforasynchcompletion**制御は、呼び出し元に返されるまでの経過時間の最大サイズを指定します。 タイムアウトが発生すると、DB_S_ASYNCHRONOUS が返されます。 タイムアウトによって非同期操作が取り消されることはありません。 タイムアウト期間内に完了しない非同期操作をアプリケーションで取り消す必要がある場合、タイムアウトを待機後、DB_S_ASYNCHRONOUS が返されたときに明示的に操作を取り消す必要があります。  
  
> [!NOTE]  
>  OLE DB サービス コンポーネントを使用している場合は S_OK、返される可能性が DB_S_ASYNCHRONOUS が予想される場合ので、アプリケーションを呼び出す必要があります[issasynchstatus::getstatus](issasynchstatus-getstatus-ole-db.md) S_OK または DB_S_ASYNCHRONOUS が返される場合の完了を確認します。  
  
 場合、 *dwMillisecTimeOut*値が、無限に設定されている、 **issasynchstatus::waitforasynchcompletion**メソッド、操作が完了するまでブロックします。 場合、 *dwMillisecTimeOut*値が 0 に設定し、メソッドはすぐに保留中の操作の状態を返します。 操作が完了する前にタイムアウトが発生すると、DB_S_ASYNCHRONOUS が返されます。  
  
 タイムアウトが発生する前に操作が完了すると、返される HRESULT には操作から返された HRESULT が設定されます (返される HRESULT は、操作が同期的に実行された場合に返される HRESULT になります)。  
  
 また、DBPROPSET_SQLSERVERROWSET プロパティ セットに SSPROP_ISSAsynchStatus プロパティが追加されています。 サポートするプロバイダー、 [ISSAsynchStatus](issasynchstatus-ole-db.md)インターフェイスが VARIANT_TRUE の値は、このプロパティを実装する必要があります。  
  
## <a name="see-also"></a>参照  
 [非同期操作を実行します。](../native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](issasynchstatus-ole-db.md)  
  
  