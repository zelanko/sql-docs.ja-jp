---
title: ADO プロパティ |Microsoft ドキュメント
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
- properties [ADO]
- ADO properties
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9598a56b4f803299e3bc02fc040199081f4383c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-properties"></a>ADO のプロパティ
|||  
|-|-|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|現在のレコードがどのページが存在することを示します。|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|現在のレコードの序数位置を示す、 **Recordset**オブジェクト。|  
|[ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md)|示します、**コマンド**を作成した、関連付けられているオブジェクト**Recordset**オブジェクト。|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|示す**接続**オブジェクトの指定した**コマンド**、**レコード セット**、または**レコード**オブジェクトが現在属しています。|  
|[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)|フィールドの値の実際の長さを示します。|  
|[属性](../../../ado/reference/ado-api/attributes-property-ado.md)|オブジェクトの 1 つまたは複数の特性を示します。|  
|[BOF と EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|**BOF**レコード セット オブジェクトの最初のレコードの前に、現在のレコードの位置があることを示します。<br /><br /> **EOF**レコード セット オブジェクトの最後のレコードの後に、現在のレコードの位置があることを示します。|  
|[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)|ブックマークの現在のレコードを一意に識別することを示します、**レコード セット**オブジェクトまたは現在のレコードを設定、**レコード セット**レコードの有効なブックマークによって識別されるオブジェクト。|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|レコードの数を示す、 **Recordset**メモリにローカルにキャッシュされたオブジェクト。|  
|[章](../../../ado/reference/ado-api/chapter-property-ado.md)|OLE DB の設定を取得または**章**オブジェクトから/上、 **ADORecordsetConstruction**オブジェクト。|  
|[CharSet](../../../ado/reference/ado-api/charset-property-ado.md)|文字セットを示します、テキストの内容**ストリーム**変換する必要があります。|  
|[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)|入力として使用されるストリームを示す、**コマンド**オブジェクト。|  
|[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)|プロバイダーに対して発行できるコマンドのテキストを示します。|  
|[CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)|試行を終了し、エラーが発生する前に、コマンドを実行中に待機する時間を示します。|  
|[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)|型を示す、**コマンド**オブジェクト。|  
|[ConnectionString プロパティ](../../../ado/reference/ado-api/connectionstring-property-ado.md)|データ ソースへの接続を確立するために使用される情報を示します。|  
|[ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)|試行を終了し、エラーが発生する前に、接続を確立中に待機する時間を示します。|  
|[Count](../../../ado/reference/ado-api/count-property-ado.md)|コレクション内のオブジェクトの数を示します。|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|カーソル サービスの場所を示します。|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|使用されているカーソルの種類を示す、 **Recordset**オブジェクト。|  
|[DataMember](../../../ado/reference/ado-api/datamember-property.md)|によって参照されるオブジェクトから取得されるデータ メンバーの名前を示す、**データソース**プロパティです。|  
|[DataSource](../../../ado/reference/ado-api/datasource-property-ado.md)|として表現されているデータを格納しているオブジェクトを示す、 **Recordset**オブジェクト。|  
|[DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)|既定のデータベースを示す、**接続**オブジェクト。|  
|[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)|データ容量を示す、**フィールド**オブジェクト。|  
|[Description](../../../ado/reference/ado-api/description-property.md)|について説明します、**エラー**オブジェクト。|  
|[言語仕様](../../../ado/reference/ado-api/dialect-property.md)|構文と、プロバイダーは解析に使用される一般的な規則を示します、 **CommandText**または**CommandStream**プロパティです。|  
|[方向](../../../ado/reference/ado-api/direction-property.md)|示すかどうか、**パラメーター**入力パラメーター、出力パラメーター、またはその両方を表すパラメーターがストアド プロシージャからの戻り値の場合、または。|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|現在のレコードの編集状態を示します。|  
|[EOS](../../../ado/reference/ado-api/eos-property.md)|現在の位置がストリームの末尾にするかどうかを示します。|  
|[フィルター](../../../ado/reference/ado-api/filter-property.md)|内のデータにフィルターを示します、 **Recordset**です。|  
|[HelpContext と HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)|ヘルプ ファイルとに関連付けられているトピックを示します、**エラー**オブジェクト。<br /><br /> **ヘルプ コンテキスト Id**として、コンテキスト ID を返します、**長い**ヘルプ ファイルのトピックの値。<br /><br /> **HelpFile**を返します、**文字列**ヘルプ ファイルの完全に解決されたパスに評価される値。|  
|[Index](../../../ado/reference/ado-api/index-property.md)|有効にインデックスを現在の名前を示す、 **Recordset**オブジェクト。|  
|[IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)|分離のレベルを示す、**接続**オブジェクト。|  
|[アイテム](../../../ado/reference/ado-api/item-property-ado.md)|名前または序数で、コレクションの特定のメンバーを示します。|  
|[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)|テキストの行区切り記号として使用するバイナリの文字を示す**ストリーム**オブジェクト。|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|編集中のレコードに置かれたロックの種類を示します。|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|レコードが、サーバーにマーシャ リングするかを示します。|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|返されるレコードの最大数を示す、 **Recordset**クエリからです。|  
|[モード](../../../ado/reference/ado-api/mode-property-ado.md)|データの変更の利用可能なアクセス許可を示す、**接続**、**レコード**、または**ストリーム**オブジェクト。|  
|[名前](../../../ado/reference/ado-api/name-property-ado.md)|オブジェクトの名前を示します。|  
|[NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md)|特定のプロバイダー固有のエラー コードを示します**エラー**オブジェクト。|  
|[数](../../../ado/reference/ado-api/number-property-ado.md)|一意に識別する数値を示します、**エラー**オブジェクト。|  
|[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)|内の数値の小数点以下桁数を示す、**パラメーター**または**フィールド**オブジェクト。|  
|[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)|値を示す、**フィールド**すべての変更が行われる前に、レコード内に存在します。|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|データのページ数を示す、 **Recordset**オブジェクトが含まれます。|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|レコードの数を表すで 1 つのページを示します、 **Recordset**です。|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|OLE DB のコンテナーを設定**行**上のオブジェクト、 **ADORecordConstruction**オブジェクト、ADO に行の親になっているため、**レコード**オブジェクト。|  
|[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)|親を指す絶対 URL 文字列を示す**レコード**、現在の**レコード**オブジェクト。|  
|[[位置]](../../../ado/reference/ado-api/position-property-ado.md)|内の現在位置を示す、**ストリーム**オブジェクト。|  
|[有効桁数](../../../ado/reference/ado-api/precision-property-ado.md)|内の数値の正確さの度合いを示す、**パラメーター**オブジェクトまたは数値に**フィールド**オブジェクト。|  
|[準備ができています。](../../../ado/reference/ado-api/prepared-property-ado.md)|実行する前に、コマンドのコンパイル済みのバージョンを保存するかどうかを示します。|  
|[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)|プロバイダーの名前を示す、**接続**オブジェクト。|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|内のレコードの数を示す、 **Recordset**オブジェクト。|  
|[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)|型を示す**レコード**オブジェクト。|  
|[行](../../../ado/reference/ado-api/row-property-ado.md)|OLE DB の設定を取得または**行**オブジェクトから/上、 **ADORecordConstruction**オブジェクト。|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|OLE DB の設定を取得または**RowPosition**オブジェクトから/上、 **ADORecordsetConstruction**オブジェクト。|  
|[行セット](../../../ado/reference/ado-api/rowset-property-ado.md)|OLE DB の設定を取得または**行セット**オブジェクトから/上、 **ADORecordsetConstruction**オブジェクト。|  
|[ソース (ADO エラー)](../../../ado/reference/ado-api/source-property-ado-error.md)|オブジェクトまたはエラーの発生源アプリケーションの名前を示します。|  
|[ソース (ADO レコード)](../../../ado/reference/ado-api/source-property-ado-record.md)|表されるエンティティを示す、**レコード**オブジェクト。|  
|[ソース (ADO レコード セット)](../../../ado/reference/ado-api/source-property-ado-recordset.md)|内のデータ ソースを示す、 **Recordset**オブジェクト|  
|[SQLState](../../../ado/reference/ado-api/sqlstate-property.md)|特定の SQL 状態を示す**エラー**オブジェクト。|  
|[状態](../../../ado/reference/ado-api/state-property-ado.md)|すべての該当するオブジェクトのオブジェクトの状態がオープンかクローズかどうかを示します。 オブジェクトの現在の状態が接続するを実行するかを取得するか、非同期メソッドを実行するすべての該当するオブジェクトを示します。|  
|[ステータス (ADO フィールド)](../../../ado/reference/ado-api/status-property-ado-field.md)|状態を示す、**フィールド**オブジェクト。|  
|[ステータス (ADO レコード セット)](../../../ado/reference/ado-api/status-property-ado-recordset.md)|バッチ更新またはその他の一括操作に関する現在のレコードの状態を示します。|  
|[StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)|階層構造内に示します**レコード セット**オブジェクトかどうか、基になる子レコードへの参照 (つまり、*章*)、親の行の位置が変わったときに変更します。|  
|[Stream プロパティ](../../../ado/reference/ado-api/stream-property.md)|OLE DB の設定を取得または**ストリーム**オブジェクトから/上、 **ADOStreamConstruction**オブジェクト。|  
|[型](../../../ado/reference/ado-api/type-property-ado.md)|操作の種類またはデータ型を示す、**パラメーター**、**フィールド**、または**プロパティ**オブジェクト。|  
|[型 (ADO Stream)](../../../ado/reference/ado-api/type-property-ado-stream.md)|含まれているデータの種類を示す、**ストリーム**(バイナリまたはテキスト)。|  
|[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)|データベースの現在の値を示す、**フィールド**オブジェクト。|  
|[値](../../../ado/reference/ado-api/value-property-ado.md)|割り当てられた値を示す、**フィールド**、**パラメーター**、または**プロパティ**オブジェクト。|  
|[[バージョン]](../../../ado/reference/ado-api/version-property-ado.md)|ADO のバージョン番号を示します。|  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 b: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO のオブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)
