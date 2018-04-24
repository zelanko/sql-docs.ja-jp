---
title: ADO イベント |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 641871f489875d139b3082ac1454a03ed94f3861
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="ado-events"></a>ADO イベント
|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|後に呼び出される、 **BeginTrans**操作します。|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|後に呼び出される、 **CommitTrans**操作します。|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|接続の開始後に呼び出されます。|  
|[[接続解除]](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|接続が終了後に呼び出されます。|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|末尾行に移動しようとしたときに呼び出されます、 **Recordset**です。|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|コマンドの実行が完了した後に呼び出されます。|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|長い非同期操作のすべてのレコードに取得された後に呼び出されます、 **Recordset**です。|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|現在までに取得された行の数を報告する場合は、長い非同期操作中に定期的と呼ばれる、 **Recordset**です。|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|1 つ以上の値の後に呼び出されます**フィールド**オブジェクトが変更されています。|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|中に警告が発生するたびに呼び出されます、 **ConnectionEvent**操作します。|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|内の現在位置の後に呼び出される、 **Recordset**変更します。|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|1 つまたは複数のレコードの変更後に呼び出されます。|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|後に呼び出される、 **Recordset**が変更されました。|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|後に呼び出される、 **RollbackTrans**操作します。|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|保留中の操作が 1 つまたは複数の値を変更する前に呼び出す**フィールド**内のオブジェクト、 **Recordset**です。|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|1 つまたは複数のレコード (行) の前に呼び出されます、 **Recordset**を変更します。|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|保留中の操作を変更する前に呼び出す、 **Recordset**です。|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|接続を開始する前に呼び出されます。|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|保留中のコマンドは、この接続上で実行し、により、営業案件を調べて、保留中の実行のパラメーターを変更する直前に呼び出されます。|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|**WillMove**イベントが呼び出された*する前に*保留中の操作の現在の位置を変更する、 **Recordset**です。|  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 b: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベントの処理](../../../ado/guide/data/handling-ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
