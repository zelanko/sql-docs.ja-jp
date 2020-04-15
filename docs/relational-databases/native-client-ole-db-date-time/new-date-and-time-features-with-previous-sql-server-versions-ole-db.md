---
title: 以前のバージョンの SQL Server を使用した日時の OLE DB 機能
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a90863fb061912dd0a6c44fe23ba2baa402662c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301023"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>以前のバージョンの SQL Server における、新しい日付または時刻の機能の動作 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、拡張された日付と時刻の機能を使用するクライアント アプリケーションが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 以前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]のバージョンの バージョンと通信するとき、およびクライアントが、拡張された日付[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と時刻の機能[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートするサーバーにコマンドを送信する前のバージョンの Native Client で通信する場合の動作について説明します。  
  
## <a name="down-level-client-behavior"></a>下位クライアントの動作  
 新しい日付/時刻型を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] **nvarchar**列として表示するよりも前のバージョンのネイティブ クライアントを使用するクライアント アプリケーション。 列のコンテンツはリテラル表現になります。 詳細については[、「OLE DB の日付と時刻の向上のためのデータ型のサポート](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)」の「データ形式: 文字列とリテラル」を参照してください。 列のサイズは、列に指定された有効桁数に対するリテラルの最大長です。  
  
 カタログ API は、クライアントに返されるダウンレベルのデータ型コード **(nvarchar**など) と関連する下位レベル表現 (適切なリテラル形式など) と一致するメタデータを返します。 ただし、返されるデータ型名は、実際の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] の型名です。  
  
 下位レベルのクライアント アプリケーションが、日付/[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]時刻型へのスキーマ変更が行われた (またはそれ以降の) サーバーに対して実行される場合、予期される動作は次のようになります。  
  
|OLE DB クライアントの型|SQL Server 2005 の型|SQL Server 2008 以降の種類|結果の変換 (サーバーからクライアントへ)|パラメーターの変換 (クライアントからサーバーへ)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Date|[OK]|[OK]|  
|DBTYPE_DBTIMESTAMP|||時刻フィールドは 0 に設定されます。|時刻フィールドが 0 以外の場合、文字列の切り捨てが原因で IRowsetChange が失敗します。|  
|DBTYPE_DBTIME||Time(0)|[OK]|[OK]|  
|DBTYPE_DBTIMESTAMP|||日付フィールドは現在の日付に設定されます。|小数秒がゼロ以外の場合、文字列の切り捨てが原因で IRowsetChange が失敗します。<br /><br /> 日付は無視されます。|  
|DBTYPE_DBTIME||Time(7)|失敗 - 無効な時間リテラル。|[OK]|  
|DBTYPE_DBTIMESTAMP|||失敗 - 無効な時間リテラル。|[OK]|  
|DBTYPE_DBTIMESTAMP||日時2(3)|[OK]|[OK]|  
|DBTYPE_DBTIMESTAMP||日時2(7)|[OK]|[OK]|  
|DBTYPE_DBDATE|Smalldatetime|Date|[OK]|[OK]|  
|DBTYPE_DBTIMESTAMP|||時刻フィールドは 0 に設定されます。|時刻フィールドが 0 以外の場合、文字列の切り捨てが原因で IRowsetChange が失敗します。|  
|DBTYPE_DBTIME||Time(0)|[OK]|[OK]|  
|DBTYPE_DBTIMESTAMP|||日付フィールドは現在の日付に設定されます。|小数秒がゼロ以外の場合、文字列の切り捨てが原因で IRowsetChange が失敗します。<br /><br /> 日付は無視されます。|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|[OK]|[OK]|  
  
 OK は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で機能した場合には、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降でも引き続き機能することを意味します。  
  
 次の一般的なスキーマ変更のみが考慮されています。  
  
-   論理的にアプリケーションで日付値または時刻値のみが必要な場合に、新しい型を使用します。 ただし、別の日付と時刻の型が使用できなかったため、アプリケーションは**datetime**または**smalldatetime**を使用することを強制されました。  
  
-   追加の秒の小数部の有効桁数または精度を取得するために、新しい型を使用します。  
  
-   日付と時刻のデータ型が優先されるため **、datetime2**に切り替えます。  
  
 ICommandWithParameters::GetParameterInfo またはスキーマ行セットを使用して取得したサーバー メタデータを使用して、ICommandWithParameters::SetParameterInfo を使用してパラメーター型情報を設定するアプリケーションは、ソース型の文字列表現が変換先の型の文字列表現よりも大きいクライアント変換中に失敗します。 たとえば、クライアント バインドで DBTYPE_DBTIMESTAMPを使用し、サーバー列が日付[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]である場合、ネイティブ クライアントは値を "yyyy-dd-mm hh:mm:ss.fff" に変換しますが、サーバー メタデータは**nvarchar(10)** として返されます。 その結果発生するオーバーフローが、DBSTATUS_E_CATCONVERTVALUE の原因となります。 同様の問題は、行セット メタデータが結果セット メタデータから設定されるため、IRowsetChange によるデータ変換で発生します。  
  
### <a name="parameter-and-rowset-metadata"></a>パラメーターと行セットのメタデータ  
 このセクションでは、以前のバージョンの Native Client でコンパイルされたクライアントのパラメータ、結果列、およびスキーマ行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットのメタデータについて[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]説明します。  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 構造体は *、prgParamInfo*パラメーターを使用して次の情報を返します。  
  
|パラメーターのタイプ|wType|ulParamSize|bPrecision|bScale|  
|--------------------|-----------|-----------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8、10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
 上記の値の範囲は連続していない場合があることに注意してください。たとえば、"8,10..16" には 9 は含まれません。 有効桁数が 0 より大きい場合は、小数点が追加されるためです。  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 返される列を次に示します。  
  
|列の型|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE、DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8、10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 構造体は、次の情報を返します。  
  
|パラメーターの型|wType|ulColumnSize|bPrecision|bScale|  
|--------------------|-----------|------------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8、10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>スキーマ行セット  
 このセクションでは、新しいデータ型のパラメーター、結果列、およびスキーマ行セットのメタデータについて説明します。 この情報は、ネイティブ クライアントよりも[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]前のバージョンのツールを使用して開発されたクライアント プロバイダーを使用する場合に役立ちます。  
  
#### <a name="columns-rowset"></a>COLUMNS 行セット  
 日付型または時刻型に対して返される列の値を次に示します。  
  
|列の型|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8、10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedure_parameters-rowset"></a>PROCEDURE_PARAMETERS 行セット  
 日付型または時刻型に対して返される列の値を次に示します。  
  
|列の型|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|date|DBTYPE_WSTR|10|20|date|  
|time|DBTYPE_WSTR|8、10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|DATETIME|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="provider_types-rowset"></a>PROVIDER_TYPES 行セット  
 日付/時刻型に対して返される行を次に示します。  
  
|型 -><br /><br /> 列|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_WSTR|DBTYPE_WSTR|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_WSTR|DBTYPE_WSTR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>下位サーバーの動作  
 以前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]のバージョンのサーバーに接続すると、新しいサーバー型名を使用しようとすると (たとえば、ICommandWithParameters::SetParameterInfo または ITableDefinition::CreateTable を使用して) DB_E_BADTYPENAME。  
  
 型名を使用せずに新しい型がパラメーターまたは結果にバインドされている場合に、新しい型を使用してサーバーの型を暗黙的に指定するか、サーバーの型からクライアントの型への有効な変換がないと、DB_E_ERRORSOCCURRED が返されます。また、実行時に使用されるアクセサーのバインドの状態に DBBINDSTATUS_UNSUPPORTED_CONVERSION が設定されます。  
  
 接続時に、サーバーのバージョンに対して、クライアントでのバッファーの型からサーバーの型への変換がサポートされている場合は、クライアントのすべてのバッファーの型を使用できます。 このコンテキストでは、*サーバーの種類*は、ICommandWithParameters::SetParameterInfo で指定された型を意味します。 つまり、クライアントでサポートされるサーバーの型への変換が成功した場合、DBTYPE_DBTIME2 および DBTYPE_DBTIMESTAMPOFFSET は、下位サーバーで使用するか、DataTypeCompatibility=80 の場合に使用することができます。 当然ながら、サーバーの型が正しくないと、実際のサーバーの型への暗黙的な変換を実行できない場合にサーバーからエラーが報告されます。  
  
## <a name="ssprop_init_datatypecompatibility-behavior"></a>SSPROP_INIT_DATATYPECOMPATIBILITY の動作  
 SSPROP_INIT_DATATYPECOMPATIBILITYをSSPROPVAL_DATATYPECOMPATIBILITY_SQL2000 に設定すると、新しい日付/時刻型および関連メタデータは[、&#41;下位](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)レベルのクライアントに対して表示されるとおり &#40;に表示されます。  
  
## <a name="comparability-for-irowsetfind"></a>IRowsetFind での比較  
 新しい日付型または時刻型に対しては、すべての比較演算子を使用できます。これは、日付型または時刻型ではなく文字列型と見なされるためです。  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化機能 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
