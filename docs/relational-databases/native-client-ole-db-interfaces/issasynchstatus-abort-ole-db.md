---
title: 'Issasynchstatus: (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3edaceb5802299ec8637634bf0006fb66d5d6851
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408681"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  非同期に実行されている操作を取り消します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>引数  
 *hChapter*[in]  
 操作を中止するチャプターのハンドル。 呼び出されるオブジェクトは、行セット オブジェクトではない場合、または、操作がチャプターに適用されません、呼び出し元を設定する必要があります*hChapter* DB_NULL_HCHAPTER にします。  
  
 *eOperation*[in]  
 中止する操作。 この引数には、  
  
 DBASYNCHOP_OPEN を設定する必要があります。キャンセル要求は、非同期に行セットを開いたり、非同期に行セットのデータを設定する場合、または非同期にデータ ソース オブジェクトを初期化する場合に適用されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 非同期操作を取り消す要求が処理されました。 ただし、その操作自体が取り消されることが保証されるわけではありません。 操作が取り消されたかどうかを判断するコンシューマーを呼び出す必要があります[issasynchstatus::getstatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)と db_e_canceled。 ただし、その可能性がありますいない呼び出しで返される、非常に [次へ]。  
  
 DB_E_CANTCANCEL  
 非同期操作をキャンセルできません。  
  
 DB_E_CANCELED  
 非同期操作を中止する要求は、通知中に取り消されました。 操作は引き続き非同期に実行されます。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。  
  
 E_INVALIDARG  
 *HChapter*パラメーターがない DB_NULL_HCHAPTER または*eOperation* DBASYNCH_OPEN ではありません。  
  
 E_UNEXPECTED  
 **Issasynchstatus:** をデータ ソース オブジェクトで呼び出された**idbinitialize::initialize**が呼び出されていない、またはが完了していません。  
  
 **Issasynchstatus:** をデータ ソース オブジェクトで呼び出された**idbinitialize::initialize** 、初期化する前に、その後に取り消されたが、呼び出されたかがタイムアウトしました。データ ソース オブジェクトはまだ初期化されていないことになります。  
  
 **Issasynchstatus:** を行セットに対して呼び出された**itransaction::commit**または**itransaction::abort** 、以前に呼び出された行セットのコミット後も存続または中止していないと、ゾンビ状態。  
  
 **Issasynchstatus:** が初期化フェーズで非同期に取り消された行セットに対して呼び出されました。 行セットはゾンビ状態になります。  
  
## <a name="remarks"></a>コメント  
 ゾンビ状態の場合に行セットまたはデータ ソース オブジェクトを残す可能性があります行セットまたはデータ ソース オブジェクトの初期化を中止するよう以外のすべてのメソッド**IUnknown**メソッドは E_UNEXPECTED を返します。 この状態になると、コンシューマーはその行セットまたはデータ ソース オブジェクトの解放しか実行できません。  
  
 呼び出す**issasynchstatus:** の値を渡すと*eOperation*以外の DBASYNCHOP_OPEN が S_OK を返します。 これは、操作が完了したか取り消されたことを示すわけではありません。  
  
## <a name="see-also"></a>参照  
 [非同期操作の実行](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
