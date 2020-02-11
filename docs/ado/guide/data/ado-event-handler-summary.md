---
title: ADO イベントハンドラーの概要 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4fef63ff610ad85e353c2ef1dc0f8e5987c74ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926198"
---
# <a name="ado-connection-and-recordset-events"></a>ADO 接続およびレコードセットイベント
2つの ADO オブジェクトがイベントを発生させることができます。[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトと[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトです。 **Connectionevent**ファミリは**接続**オブジェクトに対する操作に関連し、 **RecordsetEvent**ファミリは**レコードセット**オブジェクトの操作に関連します。

-   **接続イベント**: イベントは、接続のトランザクションが開始、コミット、またはロールバックされるときに発行されます。[コマンド](../../../ado/reference/ado-api/command-object-ado.md)が実行されたとき。**接続イベント**の操作中に警告が発生した場合は、**接続**が開始または終了したとき。

-   **レコードセットイベント**: 非同期フェッチ操作に加えて、**レコードセット**オブジェクトの行を移動したり、**レコードセットの**行のフィールドを変更したり **、レコードセット**の行を変更したり、**レコードセットを**閉じたり **、レコードセット**を閉じたり、**レコードセットに**変更を加えたりするときに、イベントが発行されます。

 次の表は、イベントとその説明をまとめたものです。

|ConnectionEvent|[説明]|
|---------------------|-----------------|
|[BeginTransComplete、CommitTransComplete、RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**トランザクション管理**-接続の現在のトランザクションが開始、コミット、またはロールバックされたことを通知します。|
|[接続](../../../ado/reference/ado-api/willconnect-event-ado.md)、 [Connectcomplete、切断](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**接続管理**-現在の接続が開始されるか、開始されたか、または終了したことを通知します。|
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)を[実行](../../../ado/reference/ado-api/willexecute-event-ado.md)します。|**コマンド実行管理**-接続での現在のコマンドの実行が開始されるか、終了することを通知します。|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**情報**-現在の操作に関する追加情報があることを通知します。|

|RecordsetEvent|[説明]|
|--------------------|-----------------|
|[Fetchprogress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)、 [fetchprogress](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[**取得ステータス**]-データ取得操作の進行状況の通知、または取得操作が完了したことを示す通知。 これらのイベントは、**レコードセット**がクライアント側カーソルを使用して開かれた場合にのみ使用できます。|
|[FieldChangeComplete、Changefield、](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**フィールド変更管理**-現在のフィールドの値が変更されるか、または変更されたことを通知します。|
|[を移動、MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)、 [endofrecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**ナビゲーション管理**-**レコードセット**内の現在の行の位置が変更されたか、変更されたか、**レコードセット**の末尾に達したことを通知します。|
|[RecordChangeComplete、](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**行の変更管理**-**レコードセット**の現在の行に何らかの変更が行われたこと、または変更されたことを通知します。|
|[WillChangeRecordset, RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**レコードセットの変更管理**-現在の**レコードセット**の内容が変更されるか、変更されたことを通知します。|

## <a name="see-also"></a>参照
 [言語による Ado イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md) [Ado events](../../../ado/reference/ado-api/ado-events.md)イベント[パラメーター](../../../ado/guide/data/event-parameters.md)イベントハンドラー[とイベントの種類の](../../../ado/guide/data/types-of-events.md)[連携](../../../ado/guide/data/how-event-handlers-work-together.md)
