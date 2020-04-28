---
title: ADO のプロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- properties [ADO]
- ADO properties
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3ddf4e26d015067c0b5bf06f6e2adeecd39f041
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920892"
---
# <a name="ado-properties"></a>ADO のプロパティ

|||  
|-|-|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|現在のレコードが存在するページを示します。|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|**レコードセット**オブジェクトの現在のレコードの位置を表す序数を示します。|  
|[ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md)|関連付けられた**レコードセット**オブジェクトを作成した**Command**オブジェクトを示します。|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|指定した**コマンド**、**レコードセット**、または**レコード**オブジェクトが現在どの**接続**オブジェクトに属しているかを示します。|  
|[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)|フィールドの値の実際の長さを示します。|  
|[属性](../../../ado/reference/ado-api/attributes-property-ado.md)|オブジェクトの1つまたは複数の特性を示します。|  
|[BOF と EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|**BOF**は、現在のレコード位置が、レコードセットオブジェクトの最初のレコードの前にあることを示します。<br /><br /> **EOF**は、レコードセットオブジェクトの最後のレコードの後に現在のレコード位置があることを示します。|  
|[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)|**レコードセット**オブジェクト内の現在のレコードを一意に識別するブックマークを示します。または、**レコードセット**オブジェクトの現在のレコードを、有効なブックマークによって識別されるレコードに設定します。|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|メモリ内にローカルにキャッシュされているレコード**セット**オブジェクトのレコードの数を示します。|  
|[章](../../../ado/reference/ado-api/chapter-property-ado.md)|**ADORecordsetConstruction**オブジェクトから OLE DB**チャプター**オブジェクトを取得します。値の設定もできます。|  
|[集合](../../../ado/reference/ado-api/charset-property-ado.md)|テキスト**ストリーム**の内容を変換する文字セットを示します。|  
|[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)|**Command**オブジェクトへの入力として使用されるストリームを示します。|  
|[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)|プロバイダーに対して発行されるコマンドのテキストを示します。|  
|[CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)|コマンドの実行中に、試行を終了してエラーを生成するまでの待機時間を示します。|  
|[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)|**Command**オブジェクトの種類を示します。|  
|[ConnectionString プロパティ](../../../ado/reference/ado-api/connectionstring-property-ado.md)|データソースへの接続を確立するために使用される情報を示します。|  
|[ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)|接続の確立中に、試行を終了してエラーを生成するまでの待機時間を示します。|  
|[Count](../../../ado/reference/ado-api/count-property-ado.md)|コレクション内のオブジェクトの数を示します。|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|カーソルサービスの場所を示します。|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|**レコードセット**オブジェクトで使用されるカーソルの種類を示します。|  
|[DataMember](../../../ado/reference/ado-api/datamember-property.md)|**DataSource**プロパティによって参照されるオブジェクトから取得されるデータメンバーの名前を示します。|  
|[DataSource](../../../ado/reference/ado-api/datasource-property-ado.md)|**レコードセット**オブジェクトとして表されるデータを格納するオブジェクトを示します。|  
|[DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)|**接続**オブジェクトの既定のデータベースを示します。|  
|[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)|**フィールド**オブジェクトのデータ容量を示します。|  
|[説明](../../../ado/reference/ado-api/description-property.md)|**エラー**オブジェクトについて説明します。|  
|[レクト](../../../ado/reference/ado-api/dialect-property.md)|**CommandText**または**commandstream**プロパティを解析するためにプロバイダーが使用する構文と一般規則を示します。|  
|[方向](../../../ado/reference/ado-api/direction-property.md)|**パラメーター**が入力パラメーター、出力パラメーター、またはその両方を表すか、またはパラメーターがストアドプロシージャからの戻り値であるかを示します。|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|現在のレコードの編集状態を示します。|  
|[EOS](../../../ado/reference/ado-api/eos-property.md)|現在の位置がストリームの末尾にあるかどうかを示します。|  
|[Assert](../../../ado/reference/ado-api/filter-property.md)|**レコードセット**内のデータのフィルターを示します。|  
|[HelpContext と HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)|**エラー**オブジェクトに関連付けられたヘルプファイルとトピックを示します。<br /><br /> **HelpContextID**は、ヘルプファイルのトピックのコンテキスト ID を**Long 型**の値として返します。<br /><br /> **HelpFile**は、ヘルプファイルの完全に解決されたパスに評価される**文字列**値を返します。|  
|[化](../../../ado/reference/ado-api/index-property.md)|**レコードセット**オブジェクトに現在適用されているインデックスの名前を示します。|  
|[IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)|**接続**オブジェクトの分離レベルを示します。|  
|[項目](../../../ado/reference/ado-api/item-property-ado.md)|名前または序数を指定して、コレクションの特定のメンバーを示します。|  
|[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)|テキスト**ストリーム**オブジェクトの行区切り記号として使用されるバイナリ文字を示します。|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|編集中にレコードに配置されたロックの種類を示します。|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|サーバーにマーシャリングされるレコードを示します。|  
|[数](../../../ado/reference/ado-api/maxrecords-property-ado.md)|クエリから**レコードセット**に返されるレコードの最大数を示します。|  
|[モード](../../../ado/reference/ado-api/mode-property-ado.md)|**接続**、**レコード**、または**ストリーム**オブジェクトのデータを変更するために使用できるアクセス許可を示します。|  
|[名前](../../../ado/reference/ado-api/name-property-ado.md)|オブジェクトの名前を示します。|  
|[NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md)|特定の**エラー**オブジェクトのプロバイダー固有のエラーコードを示します。|  
|[数値](../../../ado/reference/ado-api/number-property-ado.md)|**エラー**オブジェクトを一意に識別する番号を示します。|  
|[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)|**パラメーター**または**フィールド**オブジェクトの数値の小数点以下桁数を示します。|  
|[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)|変更が行われる前にレコード内に存在していた**フィールド**の値を示します。|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|**Recordset**オブジェクトに格納されているデータのページ数を示します。|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|レコード**セット**内の1ページを表すレコードの数を示します。|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|行の親が ADO **Record**オブジェクトに変換されるように、 **ADORecordConstruction**オブジェクトの OLE DB **row**オブジェクトのコンテナーを設定します。|  
|[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)|現在の**レコード**オブジェクトの親**レコード**を指す絶対 URL 文字列を示します。|  
|[移動](../../../ado/reference/ado-api/position-property-ado.md)|**ストリーム**オブジェクト内の現在の位置を示します。|  
|[[精度]](../../../ado/reference/ado-api/precision-property-ado.md)|**パラメーター**オブジェクトまたは数値**フィールド**オブジェクトの数値の有効桁数を示します。|  
|[Prepared](../../../ado/reference/ado-api/prepared-property-ado.md)|コンパイルされたバージョンのコマンドを実行前に保存するかどうかを示します。|  
|[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)|**接続**オブジェクトのプロバイダーの名前を示します。|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|**レコードセット**オブジェクト内のレコードの数を示します。|  
|[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)|**レコード**オブジェクトの種類を示します。|  
|[行](../../../ado/reference/ado-api/row-property-ado.md)|**ADORecordConstruction**オブジェクトからの OLE DB **Row**オブジェクトを取得します。値の設定もできます。|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|**ADORecordsetConstruction**オブジェクトからの OLE DB **rowposition**オブジェクトを取得します。値の設定もできます。|  
|[[行セット]](../../../ado/reference/ado-api/rowset-property-ado.md)|**ADORecordsetConstruction**オブジェクトの/から OLE DB**行セット**オブジェクトを取得します。値の設定もできます。|  
|[ソース (ADO エラー)](../../../ado/reference/ado-api/source-property-ado-error.md)|最初にエラーを生成したオブジェクトまたはアプリケーションの名前を示します。|  
|[ソース (ADO レコード)](../../../ado/reference/ado-api/source-property-ado-record.md)|**レコード**オブジェクトによって表されるエンティティを示します。|  
|[変換元 (ADO レコードセット)](../../../ado/reference/ado-api/source-property-ado-recordset.md)|**レコードセット**オブジェクトのデータのソースを示します。|  
|[SQLState](../../../ado/reference/ado-api/sqlstate-property.md)|特定の**エラー**オブジェクトの SQL 状態を示します。|  
|[状態](../../../ado/reference/ado-api/state-property-ado.md)|オブジェクトの状態が開いているか閉じられているかにかかわらず、適用可能なすべてのオブジェクトを示します。 オブジェクトの現在の状態が接続、実行中、または取得中かどうかにかかわらず、非同期メソッドを実行するすべての適用可能なオブジェクトに対してを示します。|  
|[状態 (ADO フィールド)](../../../ado/reference/ado-api/status-property-ado-field.md)|**フィールド**オブジェクトの状態を示します。|  
|[状態 (ADO レコードセット)](../../../ado/reference/ado-api/status-property-ado-recordset.md)|バッチ更新やその他の一括操作に関する現在のレコードの状態を示します。|  
|[StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)|親の行位置が変更されたときに、基になる子レコード (つまり、*チャプター*) への参照が変更されるかどうかを階層**レコードセット**オブジェクトで示します。|  
|[Stream プロパティ](../../../ado/reference/ado-api/stream-property.md)|**ADOStreamConstruction**オブジェクトからの OLE DB**ストリーム**オブジェクトを取得します。値の設定もできます。|  
|[Type](../../../ado/reference/ado-api/type-property-ado.md)|**パラメーター**、**フィールド**、または**プロパティ**オブジェクトの操作の種類またはデータ型を示します。|  
|[型 (ADO ストリーム)](../../../ado/reference/ado-api/type-property-ado-stream.md)|**ストリーム**に格納されているデータの型 (バイナリまたはテキスト) を示します。|  
|[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)|**Field**オブジェクトのデータベースの現在の値を示します。|  
|[[値]](../../../ado/reference/ado-api/value-property-ado.md)|**フィールド**、**パラメーター**、または**プロパティ**オブジェクトに割り当てられた値を示します。|  
|[Version](../../../ado/reference/ado-api/version-property-ado.md)|ADO のバージョン番号を示します。|  
  
## <a name="see-also"></a>参照  
 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 B: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO のオブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)
