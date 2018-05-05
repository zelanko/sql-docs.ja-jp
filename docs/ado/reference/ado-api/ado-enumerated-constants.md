---
title: ADO 列挙定数 |Microsoft ドキュメント
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
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151b4e88b3f094cd44ac7078e5d16e0b0730a9e3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-enumerated-constants"></a>ADO 列挙定数
デバッグに役立つ、ADO 列挙体には、各定数の値が一覧表示します。 ただし、この値は、参考し、ADO の 1 つのリリース別に変更があります。 コードは、列挙定数の実際の値ではなく、名前に依存する必要がありますのみです。  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|RDS の**Recordset**オブジェクト、データを取得する非同期スレッドの実行の優先順位を指定します。|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|タイミングを指定します、 **MSDataShape**プロバイダーが、階層構造での集計と集計の列を再計算**Recordset**です。|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|オプティミスティックを持つデータ ソースの行の更新中に競合を検出するために使用できるフィールドを指定します、 **Recordset**オブジェクト。|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|指定するかどうか、 **UpdateBatch**メソッドは暗黙的な続けている**再同期**メソッド操作と、そのその操作のスコープです。|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|操作によって、対象となるレコードを指定します。|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|操作の開始位置を示すブックマークを指定します。|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|コマンドの引数を解釈する方法を指定します。|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|ブックマークによって表される 2 つのレコードの相対位置を指定します。|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|内のデータを変更するため利用可能なアクセス許可を指定、**接続**、opening、**レコード**の値を指定するか、**モード**のプロパティ、 **レコード**と**ストリーム**オブジェクト。|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|指定するかどうか、**開いている**のメソッド、**接続**後にオブジェクトを返す必要があります (同期的に) (非同期)、接続が確立される前に、または。|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|ODBC データ ソースへの接続を開くときに、不足しているパラメーターを要求するダイアログ ボックスを表示するかどうかを指定します。|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|動作を指定します、**つまり**メソッドです。|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|カーソル エンジンの場所を指定します。|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|どのような機能を指定、**サポート**のメソッドをテストする必要があります。|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|使用するカーソルの種類を指定します、 **Recordset**オブジェクト。|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|データ型を指定します、**フィールド**、**パラメーター**、または**プロパティ**です。|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|レコードの編集状態を指定します。|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|ADO の実行時エラーの種類を指定します。|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|イベントを発生の原因となった理由を指定します。|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|イベントの実行の現在の状態を指定します。|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|プロバイダーでのコマンドの実行方法を指定します。|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|参照されている特別なフィールドを指定します、**フィールド**のコレクション、**レコード**オブジェクト。|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|1 つまたは複数の属性を指定します、**フィールド**オブジェクト。|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|状態を示す、**フィールド**オブジェクト。|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|フィルター処理するレコードのグループを指定します、 **Recordset**です。|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|取得するレコードの数を指定します、 **Recordset**です。|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|トランザクションの分離のレベルを指定します、**接続**オブジェクト。|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|テキストの行区切り記号として使用される文字を指定**ストリーム**オブジェクト。|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|編集中のレコードに適用されるロックの種類を指定します。|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|サーバーにどのレコードを返す必要がありますを指定します。|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|動作を指定します、**レコード**オブジェクト**後続**メソッドです。|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|オブジェクトがオープンかクローズは、コマンドの実行またはデータのフェッチで、データ ソースに接続するかどうかを指定します。|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|属性を指定、**パラメーター**オブジェクト。|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|指定するかどうか、**パラメーター**入力パラメーター、出力パラメーター、またはその両方を表すパラメーターがストアド プロシージャからの戻り値の場合またはします。|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|保存する形式を指定します、 **Recordset**です。|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|内のレコードのポインターの現在位置を示す、 **Recordset**です。|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|属性を指定、**プロパティ**オブジェクト。|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|指定、**レコード**オブジェクト**開く**メソッド既存かどうか**レコード**開かれている、または、新規にする必要があります**レコード**作成する必要があります。|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|開くのためのオプションを指定します、**レコード**です。 これらの値は、OR 演算子を使用して組み合わせることができます。|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|バッチ更新およびその他の一括操作に関して、レコードの状態を指定します。|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|型を指定**レコード**オブジェクト。|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|呼び出しによって基になる値を上書きするかどうかを示す**再同期**です。|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|ファイルを作成またはからの保存時に上書きするかどうかを指定します、**ストリーム**オブジェクト。 値は、AND 演算子と組み合わせることができます。|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|スキーマの種類を指定**Recordset**を**OpenSchema**メソッドを取得します。 内のレコードの検索の方向を指定します、 **Recordset**です。|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|内のレコードの検索の方向を指定します、 **Recordset**です。 型を指定**シーク**を実行します。|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|型を指定**シーク**を実行します。 開くのためのオプションを指定します、**ストリーム**オブジェクト。 値は、AND 演算子と組み合わせることができます。|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|開くのためのオプションを指定します、**ストリーム**オブジェクト。 値は、AND 演算子と組み合わせることができます。 ストリーム全体、または次の行をから読み取る必要があるかどうかを指定します、**ストリーム**オブジェクト。|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|ストリーム全体、または次の行をから読み取る必要があるかどうかを指定します、**ストリーム**オブジェクト。 格納されたデータの種類を指定、**ストリーム**オブジェクト。|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|格納されたデータの種類を指定、**ストリーム**オブジェクト。 行区切り記号に書き込まれる文字列に追加するかどうかを指定します、**ストリーム**オブジェクト。|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|行区切り記号に書き込まれる文字列に追加するかどうかを指定します、**ストリーム**オブジェクト。 取得するときに、形式を指定、 **Recordset**を文字列として。|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|取得するときに、形式を指定、 **Recordset**を文字列として。 トランザクション属性を指定します、**接続**オブジェクト。|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|トランザクション属性を指定します、**接続**オブジェクト。|  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [付録 b: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
