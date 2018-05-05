---
title: ADO イベント ハンドラーの概要 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3e52fe70e497ab8c5b715861e16f3f67266f9f8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-connection-and-recordset-events"></a>ADO 接続とレコード セットのイベント
2 つの ADO オブジェクトは、イベントを発生させることができます。[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトおよび[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 **ConnectionEvent**ファミリで操作に関連する、**接続**オブジェクト、および**RecordsetEvent**ファミリで操作に関連する、 **レコード セット**オブジェクト。

-   **接続イベント**: 接続でトランザクションを開始がコミットまたは戻る以外の場合はロールバックされるときにイベントが発行されて、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)実行されます警告が発生した場合、**接続イベント**。操作です。または、**接続**開始または終了します。

-   **レコード セットのイベント**: 非同期フェッチ操作中心、および内の行を移動するときにイベントが発行されて、 **Recordset**オブジェクト、行内のフィールドを変更、 **Recordset**、内の行を変更、**レコード セット**を開き、**レコード セット**サーバー側のカーソルを閉じる、**レコード セット**、またはいずれかが変更にも一切変更、 **レコード セット**です。

 次の表は、イベントとその説明を要約します。

|ConnectionEvent|Description|
|---------------------|-----------------|
|[BeginTransComplete、CommitTransComplete、RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**トランザクションの管理**: 接続で現在のトランザクションが開始すると、通知をコミットまたはロールバックします。|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)、 [ConnectComplete、切断](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**接続の管理**: 現在の接続が開始すると、通知が開始または終了しました。|
|[アクティビ ティー](../../../ado/reference/ado-api/willexecute-event-ado.md)、 [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**コマンドの実行管理**: 接続で現在のコマンドの実行が開始または終了したことを通知します。|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**情報**-現在の操作に関する追加情報があることを通知します。|

|RecordsetEvent|Description|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)、 [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**取得状況**-データ取得操作の進行状況の通知または取得操作が完了したことです。 これらのイベントは使用可能な場合、**レコード セット**クライアント側カーソルを使用します。|
|[WillChangeField、FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**フィールドの変更管理**: 現在のフィールドの値は変更または変更されたことを通知します。|
|[WillMove、MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)、 [EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**ナビゲーション管理**-通知の現在の行の位置を**Recordset**変更が変更されている、またはの終わりに達しました、**レコード セット**です。|
|[WillChangeRecord、RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**行の変更管理**— の現在の行で何かを通知、 **Recordset**変更、または変更しました。|
|[WillChangeRecordset、RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**レコード セットの変更管理**— 現在で何かを通知**Recordset**変更、または変更しました。|

## <a name="see-also"></a>参照
 [言語によって、ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md) [ADO イベント](../../../ado/reference/ado-api/ado-events.md)[イベント パラメーター](../../../ado/guide/data/event-parameters.md) [イベント ハンドラーがどのように連携](../../../ado/guide/data/how-event-handlers-work-together.md)[イベントの種類](../../../ado/guide/data/types-of-events.md)
