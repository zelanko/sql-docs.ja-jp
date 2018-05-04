---
title: 大きな CLR ユーザー定義型 (OLE DB) |Microsoft ドキュメント
description: 大きな CLR ユーザー定義型 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a3e7c0491454a4b3fa0998994cb63ab0ebcbe589
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="large-clr-user-defined-types-ole-db"></a>大きな CLR ユーザー定義型 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、OLE DB Driver for 大きな共通言語ランタイム (CLR) ユーザー定義型 (Udt) をサポートするために SQL Server で、OLE DB への変更について説明します。  
  
 SQL Server の OLE DB Driver における大きな CLR Udt のサポートの詳細については、次を参照してください。 [Large CLR User-Defined 型](../../oledb/features/large-clr-user-defined-types.md)です。 サンプルについては、次を参照してください。[を使用して大きな CLR Udt &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-large-clr-udts-ole-db.md)です。  
  
## <a name="data-format"></a>データ形式  
 OLE DB Driver for SQL Server を使用して ~ ラージ オブジェクト (LOB) 型のサイズが無制限である値の長さを表現する場合は 0 です。 8,000 バイトを超える CLR UDT のサイズも ~0 で表されます。  
  
 次の表に、パラメーターおよび行セットでのデータ型のマッピングを示します。  
  
|SQL Server データ型|OLE DB データ型|メモリ レイアウト|値|  
|--------------------------|----------------------|-------------------|-----------|  
|CLR UDT|DBTYPE_UDT|Byte[] (バイト配列\)|132 (oledb.h)|  
  
 UDT 値はバイト配列として表されます。 16 進文字列との間の変換がサポートされています。 リテラル値は、"0x" で始まる 16 進文字列として表されます。 16 進文字列は、ベース 16 のバイナリ データをテキストで表現したものです。 サーバーの種類からの変換は、例です**varbinary(10)** DBTYPE_STR にその結果は文字の各ペアが 1 バイトを表す 20 文字の 16 進表記でします。  
  
## <a name="parameter-properties"></a>パラメーターのプロパティ  
 DBPROPSET_SQLSERVERPARAMETER プロパティ セットは、OLE DB を介して UDT をサポートします。 詳細については、次を参照してください。[ユーザー種類](../../oledb/features/using-user-defined-types.md)です。  
  
## <a name="column-properties"></a>列のプロパティ  
 DBPROPSET_SQLSERVERCOLUMN プロパティ セットは、OLE DB を介してテーブルの作成をサポートします。 詳細については、次を参照してください。[ユーザー種類](../../oledb/features/using-user-defined-types.md)です。  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>ITableDefinition::CreateTable でのデータ型マッピング  
 次の情報が使用される**DBCOLUMNDESC** itabledefinition::createtable で UDT 列が必要な場合に使用する構造体。  
  
|OLE DB データ型 (*wType*)|*pwszTypeName*|SQL Server データ型|*rgPropertySets*|  
|----------------------------------|--------------------|--------------------------|----------------------|  
|DBTYPE_UDT|無視|UDT (UDT)|DBPROPSET_SQLSERVERCOLUMN プロパティ セットを含める必要があります。|  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 介して DBPARAMINFO 構造体で返される情報**prgParamInfo**のとおりです。  
  
|パラメーターの型|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|-------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (8,000 バイト以下の長さ)|"DBTYPE_UDT"|*n*|未定義|未定義|オフ|  
|DBTYPE_UDT<br /><br /> (8,000 バイトを超える長さ)|"DBTYPE_UDT"|~0|未定義|未定義|セット (set)|  
  
## <a name="icommandwithparameterssetparameterinfo"></a>ICommandWithParameters::SetParameterInfo  
 DBPARAMBINDINFO 構造体で提供される情報は、次の表に準拠する必要があります。  
  
|パラメーターの型|*pwszDataSourceType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|--------------------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (8,000 バイト以下の長さ)|DBTYPE_UDT|*n*|無視されます。|無視されます。|パラメーターが DBTYPE_IUNKNOWN を使用して渡される場合に設定する必要があります。|  
|DBTYPE_UDT<br /><br /> (8,000 バイトを超える長さ)|DBTYPE_UDT|~0|無視されます。|無視されます。|無視されます。|  
  
## <a name="isscommandwithparameters"></a>ISSCommandWithParameters  
 アプリケーションを使用して**ISSCommandWithParameters**を取得し、パラメーターのプロパティ セクションで定義されているパラメーターのプロパティを設定します。  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 返される列は次のとおりです。  
  
|列の型|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE|DBCOLUMN_FLAGS_ISLONG|DBCOLUMNS_ISSEARCHABLE|DBCOLUMN_OCTETLENGTH|  
|-----------------|--------------------|--------------------------|-------------------------|---------------------|-----------------------------|-----------------------------|---------------------------|  
|DBTYPE_UDT<br /><br /> (8,000 バイト以下の長さ)|DBTYPE_UDT|*n*|NULL|NULL|Clear|DB_ALL_EXCEPT_LIKE|n|  
|DBTYPE_UDT<br /><br /> (8,000 バイトを超える長さ)|DBTYPE_UDT|~0|NULL|NULL|オン|DB_ALL_EXCEPT_LIKE|0|  
  
 UDT には次の列も定義されています。  
  
|列識別子|型|Description|  
|-----------------------|----------|-----------------|  
|DBCOLUMN_UDT_CATALOGNAME|DBTYPE_WSTR|UDT 列の場合は、UDT が定義されているカタログの名前。|  
|DBCOLUMN_UDT_SCHEMANAME|DBTYPE_WSTR|UDT 列の場合は、UDT が定義されているスキーマの名前。|  
|DBCOLUMN_UDT_NAME|DBTYPE_WSTR|UDT 列の場合は、UDT の 1 部構成の名前。|  
|DBCOLUMN_ASSEMBLY_TYPENAME|DBTYPE_WSTR|UDT 列の UDT の完全な型名。 アセンブリ型の完全修飾名を使用することで、Type.GetType メソッドを使用してその型のオブジェクトのインスタンスを作成できます。|  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 DBCOLUMNINFO 構造体で返される情報は次のとおりです。  
  
|パラメーターの型|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBCOLUMNFLAGS_ISLONG|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------|  
|DBTYPE_UDT<br /><br /> (8,000 バイト以下の長さ)|DBTYPE_UDT|*n*|~0|~0|Clear|  
|DBTYPE_UDT<br /><br /> (8,000 バイトを超える長さ)|DBTYPE_UDT|~0|~0|~0|オン|  
  
## <a name="columns-rowset-schema-rowsets"></a>COLUMNS 行セット (スキーマ行セット)  
 UDT 型に対して返される列値を次に示します。  
  
|列の型|DATA_TYPE|COLUMN_FLAGS、DBCOLUMFLAGS_ISLONG|CHARACTER_OCTET_LENGTH|  
|-----------------|----------------|-----------------------------------------|------------------------------|  
|DBTYPE_UDT<br /><br /> (8,000 バイト以下の長さ)|DBTYPE_UDT|Clear|*n*|  
|DBTYPE_UDT<br /><br /> (8,000 バイトを超える長さ)|DBTYPE_UDT|オン|0|  
  
 UDT には、次の追加の列が定義されています。  
  
|列の識別子|型|Description|  
|-----------------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|UDT 列の場合は、UDT が定義されているカタログの名前。|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|UDT 列の場合は、UDT が定義されているスキーマの名前。|  
|SS_UDT_NAME|DBTYPE_WSTR|UDT 列の場合は、UDT の 1 部構成の名前。|  
|SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|UDT 列の場合は、UDT の完全な型名。 アセンブリ型の完全修飾名を使用することで、Type.GetType メソッドを使用してその型のオブジェクトのインスタンスを作成できます。|  
  
 PROCEDURE_PARAMETERS 行セットに関しては、DATA_TYPE に COLUMNS スキーマ行セットと同じ値が格納され、TYPE_NAME に UDT が格納されます。 同じ追加の列も定義されています。  
  
 PROVIDER_TYPES スキーマ行セットには、ユーザー定義型が表示されません。  
  
## <a name="bindings-and-conversions"></a>バインドと変換  
  
|Binding データ型|UDT からサーバー|UDT 以外からサーバー|サーバーから UDT|サーバーから UDT 以外|  
|----------------------|-------------------|------------------------|---------------------|--------------------------|  
|DBTYPE_UDT|サポートされている (5)|エラー (1)|サポートされている (5)|エラー (4)|  
|DBTYPE_BYTES|サポートされている (5)|なし|サポートされている (5)|なし|  
|DBTYPE_WSTR|サポート (2)、(5)|なし|サポート (3)、(5)、(6)|なし|  
|DBTYPE_BSTR|サポート (2)、(5)|なし|サポートされている (3), (5)|なし|  
|DBTYPE_STR|サポート (2)、(5)|なし|サポートされている (3), (5)|なし|  
|DBTYPE_IUNKNOWN|サポートされている (6)|なし|サポートされている (6)|なし|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|サポート (5)|なし|サポートされている (3), (5)|なし|  
|DBTYPE_VARIANT (VT_BSTR)|サポート (2)、(5)|なし|なし|なし|  
  
### <a name="key-to-symbols"></a>記号の説明  
  
|記号|意味|  
|------------|-------------|  
|1|サーバー以外の型で dbtype_udt 型が指定された場合**icommandwithparameters::setparameterinfo**アクセサーの型が DBTYPE_UDT と、ステートメントが実行されるときにエラーが発生します。  発生するエラーは DB_E_ERRORSOCCURRED、パラメーターの状態は DBSTATUS_E_BADACCESSOR です。<br /><br /> UDT ではないサーバー パラメーターに UDT 型のパラメーターを指定すると、エラーになります。|  
|2|データが 16 進数文字列からバイナリ データに変換されます。|  
|3|データがバイナリ データから 16 進文字列に変換されます。|  
|4|使用する場合、検証が行われる**CreateAccessor**または**GetNextRows**です。 このエラーは DB_E_ERRORSOCCURRED です。 バインドの状態は、DBBINDSTATUS_UNSUPPORTEDCONVERSION に設定されます。|  
|5|BY_REF を使用できます。|  
|6|UDT パラメーターを、DBBINDING で DBTYPE_IUNKNOWN としてバインドできます。 DBTYPE_IUNKNOWN へのバインドは、アプリケーションが、ISequentialStream インターフェイスを使用してストリームとしてデータを処理することを示します。 指定されている場合、コンシューマー *wType* DBTYPE_IUNKNOWN 型としてバインドし、対応する列または出力で、ストアド プロシージャのパラメーターが UDT は、OLE DB Driver for SQL Server は ISequentialStream を返します。 入力パラメーター、OLE DB Driver for SQL Server に対してクエリを ISequentialStream インターフェイスです。<br /><br /> UDT が大きい場合は、DBTYPE_IUNKNOWN バインドを使用しながら UDT データの長さをバインドしないようにすることができます。 ただし、小さな UDT の場合は長さをバインドする必要があります。 次の条件が 1 つ以上当てはまる場合は、DBTYPE_UDT パラメーターを大きな UDT として指定できます。<br />*ulParamParamSize*は ~ 0 です。<br />DBPARAMBINDINFO 構造体で DBPARAMFLAGS_ISLONG が設定されている。<br /><br /> 行データの場合は、DBTYPE_IUNKNOWN バインドを大きな UDT だけに使用できます。 列が行セットで icolumnsinfo::getcolumninfo メソッドを使用して、大きな UDT 型がかどうかを確認したり、オブジェクトの IColumnsInfo インターフェイスをコマンドします。 次の条件が 1 つ以上当てはまる場合、DBTYPE_UDT 列は大きな UDT 列です。<br />DBCOLUMNFLAGS_ISLONG フラグが設定で*dwFlags* DBCOLUMNINFO 構造体のメンバーです。 <br />*ulColumnSize* DBCOLUMNINFO のメンバーは ~ 0 です。|  
  
 DBTYPE_NULL と DBTYPE_EMPTY は入力パラメーターにバインドできますが、出力パラメーターや結果にはバインドできません。 入力パラメーターにバインドした場合は、状態を DBSTATUS_S_ISNULL (DBTYPE_NULL の場合) または DBSTATUS_S_DEFAULT (DBTYPE_EMPTY の場合) に設定する必要があります。 DBTYPE_BYREF を、DBTYPE_NULL または DBTYPE_EMPTY と共に使用することはできません。  
  
 DBTYPE_UDT は、DBTYPE_EMPTY および DBTYPE_NULL に変換することもできます。 ただし、DBTYPE_NULL および DBTYPE_EMPTY を DBTYPE_UDT に変換することはできません。 この動作は、DBTYPE_BYTES 型と一貫性があります。 **ISSCommandWithParameters**はプロセス Udt をパラメーターとして使用します。  
  
 OLE DB core services で提供されるデータ変換 (**IDataConvert**) は、dbtype_udt 型に適用できません。  
  
 また、その他のバインドもサポートされません。  
  
## <a name="comparability-for-irowsetfind"></a>IRowsetFind での比較  
 UDT 型については、次の比較のみがサポートされています。  
  
-   EQ  
  
-   NE  
  
-   IGNORE  
  
 その他の比較を試みると、DB_E_BADCOMPAREOP が返されます。  
  
## <a name="bcp-support-for-udts"></a>BCP による UDT のサポート  
 UDT 値をインポートし、文字またはバイナリ値としてのみをエクスポートします。  
  
## <a name="down-level-client-behavior-for-udts"></a>Udt に対する下位クライアントの動作  
 UDT に対しては、下位クライアントで次のように型マッピングが行われます。  
  
|クライアントのバージョン|DBTYPE_UDT<br /><br /> (8,000 バイト以下の長さ)|DBTYPE_UDT<br /><br /> (8,000 バイトを超える長さ)|  
|--------------------|------------------------------------------------------------------|---------------------------------------------------------|  
|SQL Server 2005|UDT (UDT)|varbinary(max)|  
|SQL Server 2008 以降|UDT (UDT)|UDT (UDT)|  
  
 ときに**DataTypeCompatibility** (SSPROP_INIT_DATATYPECOMPATIBILITY) が「80」に設定されている、大きな UDT 型がダウンレベルのクライアントに表示される同じ方法でクライアントに表示されます。  
  
## <a name="see-also"></a>参照  
 [大きな CLR ユーザー定義型](../../oledb/features/large-clr-user-defined-types.md)  
  
  

