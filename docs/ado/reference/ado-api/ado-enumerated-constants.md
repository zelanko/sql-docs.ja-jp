---
title: ADO 列挙定数 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
author: rothja
ms.author: jroth
ms.openlocfilehash: 74d3cc347d14a1d02ae5953b7762513b252493e6
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242882"
---
# <a name="ado-enumerated-constants"></a>ADO の列挙定数
デバッグを支援するために、ADO 列挙体には各定数の値が一覧表示されます。 ただし、この値は純粋にアドバイザリであり、あるリリースの ADO から別のリリースに変更される可能性があります。 コードは、各列挙定数の実際の値ではなく、名前のみに依存する必要があります。  
  
|定数|説明|  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|RDS**レコードセット**オブジェクトの場合は、データを取得する非同期スレッドの実行の優先度を指定します。|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|**MSDataShape**プロバイダーが階層**レコードセット**の集計列と計算列を再計算するタイミングを指定します。|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|**レコードセット**オブジェクトを使用してデータソースの行をオプティミスティック更新するときに、競合を検出するために使用できるフィールドを指定します。|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|**UpdateBatch**メソッドの後に暗黙の再**同期**メソッド操作が続くかどうかを指定します。それを行う場合は、その操作のスコープを指定します。|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|操作の影響を受けるレコードを指定します。|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|操作の開始位置を示すブックマークを指定します。|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|コマンド引数をどのように解釈するかを指定します。|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|ブックマークによって表される2つのレコードの相対位置を指定します。|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|**接続**のデータを変更したり、**レコード**を開いたり、**レコード**および**ストリーム**オブジェクトの**Mode**プロパティの値を指定したりするために使用できるアクセス許可を指定します。|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|**接続オブジェクト**の**Open**メソッドが、接続が確立された (同期的に) かそれより前 (非同期) に戻る必要があるかどうかを指定します。|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|ODBC データソースへの接続を開くときに、ダイアログボックスを表示して、不足しているパラメーターを確認するかどうかを指定します。|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|**Copyrecord**メソッドの動作を指定します。|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|カーソルエンジンの場所を指定します。|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|**サポート**メソッドがテストする必要がある機能を指定します。|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|**レコードセット**オブジェクトで使用されるカーソルの種類を指定します。|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|**フィールド**、**パラメーター**、または**プロパティ**のデータ型を指定します。|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|レコードの編集状態を指定します。|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|ADO ランタイムエラーの種類を指定します。|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|イベントの発生原因となった理由を指定します。|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|イベントの実行の現在の状態を指定します。|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|プロバイダーがコマンドを実行する方法を指定します。|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|**レコード**オブジェクトの**fields**コレクションで参照される特殊なフィールドを指定します。|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|**Field**オブジェクトの1つまたは複数の属性を指定します。|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|**フィールド**オブジェクトの状態を指定します。|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|レコード**セット**からフィルター選択するレコードのグループを指定します。|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|レコード**セット**から取得するレコードの数を指定します。|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|**接続**オブジェクトのトランザクション分離レベルを指定します。|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|テキスト**ストリーム**オブジェクトの行区切り記号として使用される文字を指定します。|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|編集中にレコードに適用されるロックの種類を指定します。|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|サーバーに返すレコードを指定します。|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|**Record**オブジェクトの**MoveRecord**メソッドの動作を指定します。|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|オブジェクトが開いているか閉じられているか、データソースに接続しているか、コマンドを実行しているか、データをフェッチしているかを指定します。|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|**パラメーター**オブジェクトの属性を指定します。|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|**パラメーター**が入力パラメーター、出力パラメーター、またはその両方を表すか、またはパラメーターがストアドプロシージャからの戻り値であるかを指定します。|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|**レコードセット**を保存する形式を指定します。|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|レコード**セット**内のレコードポインターの現在位置を指定します。|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|**プロパティ**オブジェクトの属性を指定します。|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|**Record**オブジェクト**Open**メソッドに対して、既存の**レコード**を開くか、新しい**レコード**を作成するかを指定します。|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|**レコード**を開くためのオプションを指定します。 これらの値は、OR 演算子を使用して組み合わせることができます。|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|バッチ更新やその他の一括操作に関して、レコードの状態を指定します。|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|**レコード**オブジェクトの種類を指定します。|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|再**同期**の呼び出しによって基になる値を上書きするかどうかを指定します。|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|**ストリーム**オブジェクトから保存するときにファイルを作成するか上書きするかを指定します。 値は AND 演算子と組み合わせることができます。|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|**OpenSchema**メソッドによって取得されるスキーマ**レコードセット**の種類を指定します。 レコード**セット**内のレコード検索の方向を指定します。|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|レコード**セット**内のレコード検索の方向を指定します。 実行する**シーク**の種類を指定します。|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|実行する**シーク**の種類を指定します。 **ストリーム**オブジェクトを開くためのオプションを指定します。 値は AND 演算子と組み合わせることができます。|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|**ストリーム**オブジェクトを開くためのオプションを指定します。 値は AND 演算子と組み合わせることができます。 ストリーム全体または次の行を**ストリーム**オブジェクトから読み取るかどうかを指定します。|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|ストリーム全体または次の行を**ストリーム**オブジェクトから読み取るかどうかを指定します。 **ストリーム**オブジェクトに格納されているデータの型を指定します。|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|**ストリーム**オブジェクトに格納されているデータの型を指定します。 **ストリーム**オブジェクトに書き込まれる文字列に行の区切り記号を追加するかどうかを指定します。|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|**ストリーム**オブジェクトに書き込まれる文字列に行の区切り記号を追加するかどうかを指定します。 **レコードセット**を文字列として取得する場合の形式を指定します。|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|**レコードセット**を文字列として取得する場合の形式を指定します。 **接続**オブジェクトのトランザクション属性を指定します。|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|**接続**オブジェクトのトランザクション属性を指定します。|  
  
## <a name="see-also"></a>参照  
 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [付録 B: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
