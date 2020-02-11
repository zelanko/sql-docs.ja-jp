---
title: ADO Events |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 35169313ae487514403f62c8e6d1ba2c262cb8a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921005"
---
# <a name="ado-events"></a>ADO のイベント

|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**BeginTrans**操作の後に呼び出されます。|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**CommitTrans**操作の後に呼び出されます。|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|接続の開始後に呼び出されます。|  
|[切断](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|接続の終了後に呼び出されます。|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**レコードセット**の末尾を越えて行を移動しようとしたときに呼び出されます。|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|コマンドの実行が完了した後に呼び出されます。|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|長い非同期操作内のすべてのレコードが**レコードセット**に取得された後に呼び出されます。|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|長い非同期操作中に、**レコードセット**に現在取得されている行の数を報告するために定期的に呼び出されます。|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|1つまたは複数の**フィールド**オブジェクトの値が変更された後に呼び出されます。|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Connectionevent**操作中に警告が発生するたびに呼び出されます。|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|**レコードセット**内の現在位置が変更された後に呼び出されます。|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|1つ以上のレコードが変更した後に呼び出されます。|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**レコードセット**が変更された後に呼び出されます。|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**RollbackTrans**操作の後に呼び出されます。|  
|[Changefield](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|保留中の操作が**レコードセット**内の1つまたは複数の**フィールド**オブジェクトの値を変更する前に呼び出されます。|  
|[Changerecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**レコードセット**内の1つ以上のレコード (行) が変更される前に呼び出されます。|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|保留中の操作によって**レコードセット**が変更される前に呼び出されます。|  
|[接続](../../../ado/reference/ado-api/willconnect-event-ado.md)|接続が開始される前に呼び出されます。|  
|[実行する](../../../ado/reference/ado-api/willexecute-event-ado.md)|保留中のコマンドがこの接続で実行される直前に呼び出され、保留中の実行パラメーターを確認および変更する機会をユーザーに与えます。|  
|[移動](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|"イベントの**移動**" は、保留中の操作が**レコードセット**内の現在の位置を変更*する前に*呼び出されます。|  
  
## <a name="see-also"></a>参照  
 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 B: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベントの処理](../../../ado/guide/data/handling-ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
