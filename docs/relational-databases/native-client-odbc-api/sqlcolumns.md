---
title: SQL カラム |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: abce98b64da8de6039f81025201cce25269763a6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302610"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLColumns は**、*カタログ名*、*テーブル*名、列*名*の各パラメーターに値が存在するかどうかをSQL_SUCCESS返します。 **SQLFetch**は、これらのパラメーターで無効な値が使用されている場合にSQL_NO_DATAを返します。  
  
> [!NOTE]  
>  大きな値型の場合、すべての長さパラメーターが SQL_SS_LENGTH_UNLIMITED という値で返されます。  
  
 **SQLColumns は**、静的サーバー カーソルで実行できます。 更新可能 (動的またはキーセット) カーソルで**SQLColumns**を実行しようとすると、カーソルの種類が変更されたことを示すSQL_SUCCESS_WITH_INFOが返されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバは *、CatalogName* Linked_Server_Name パラメータの 2 つの部分から構成される名前を受け取ることによって、リンク サーバー上のテーブルのレポート情報*をサポートCatalog_Name。*  
  
 ODBC 2 の場合。*x*アプリケーションが*テーブル名*でワイルドカードを使用していない場合 **、SQLColumns は***、名前が TableName*と一致し、現在のユーザーが所有しているテーブルに関する情報を返します。 現在のユーザーがテーブルを所有していない場合 *、名前が TableName*パラメーターに一致する名前を持つ**SQLColumns は**、テーブル名が*TableName*パラメーターと一致する他のユーザーが所有するテーブルに関する情報を返します。 ODBC 2 の場合。*x*アプリケーションでワイルドカードを使用すると、**名前**が*テーブル名*と一致するすべてのテーブルが返されます。 ODBC 3 の場合。*x*アプリケーション**SQLColumns は**、所有者やワイルドカードが使用されているかどうかに関係なく *、名前が TableName に*一致するすべてのテーブルを返します。  
  
 次の表は、結果セットによって返される列の一覧です。  
  
|列名|説明|  
|-----------------|-----------------|  
|DATA_TYPE|**varchar(max)** データ型のSQL_VARCHAR、SQL_VARBINARY、またはSQL_WVARCHARを返します。|  
|TYPE_NAME|**varchar(max) 、varbinary(最大)**、**および** **nvarchar(最大)** データ型の "varchar"、"varchar"、または "nvarchar" を返します。|  
|COLUMN_SIZE|列のサイズが無制限であることを示す**varchar(max)** データ型のSQL_SS_LENGTH_UNLIMITEDを返します。|  
|BUFFER_LENGTH|バッファのサイズが無制限であることを示す**varchar(max)** データ型のSQL_SS_LENGTH_UNLIMITEDを返します。|  
|SQL_DATA_TYPE|**varchar(max)** データ型のSQL_VARCHAR、SQL_VARBINARY、またはSQL_WVARCHARを返します。|  
|CHAR_OCTET_LENGTH|char 型または binary 型の列の最大長を返します。 サイズが無制限であることを示す場合は 0 を返します。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|XML スキーマ コレクション名が定義されているカタログの名前を返します。 カタログ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|XML スキーマ コレクション名が定義されているスキーマの名前を返します。 スキーマ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_NAME|XML スキーマ コレクションの名前を返します。 名前が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_UDT_CATALOG_NAME|UDT (ユーザー定義型) を含むカタログの名前です。|  
|SS_UDT_SCHEMA_NAME|UDT を含むスキーマの名前。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|UDT のアセンブリ修飾名です。|  
  
 UDT の場合、既存の TYPE_NAME列は UDT の名前を示すために使用されます。したがって、SQLColumns または**SQLProcedureColumns**の結果セットに追加する列[はありません](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md)。 UDT 列または UDT パラメーターの場合、DATA_TYPE は SQL_SS_UDT です。  
  
 サーバーからパラメーターの UDT に関する追加のメタデータ プロパティを返したり、サーバーでこのメタデータ プロパティの情報が必要となる場合は、上記に定義したドライバー固有の新しい記述子を使用して、UDT のメタデータ プロパティの取得や設定を行えます。  
  
 クライアントが SQLColumns[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続して呼び出した場合、カタログ入力パラメータに NULL またはワイルド カード値を使用しても、他のカタログから情報が返されません。 代わりに、現在のカタログに関する情報だけが返されます。 クライアントは、まず SQLTables を呼び出して、目的のテーブルがどのカタログに存在するかを判断します。 クライアントは、そのカタログ値を SQLColumns の呼び出しでカタログ入力パラメーターに使用して、そのテーブル内の列に関する情報を取得できます。  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns とテーブル値パラメーター  
 SQLColumns によって返される結果セットは、SQL_SOPT_SS_NAME_SCOPEの設定によって異なります。 詳細については、 [SQLSetStmtAttr を](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)参照してください。 テーブル値パラメーター用に次の列が追加されました。  
  
|列名|データ型|内容|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|TABLE_TYPE の列では、列が計算列の場合は SQL_TRUE、それ以外の場合は SQL_FALSE になります。|  
|SS_IS_IDENTITY|Smallint|列が ID 列の場合は SQL_TRUE、それ以外の場合は SQL_FALSE になります。|  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>SQLColumns による機能強化された日付と時刻のサポート  
 日付/時刻型に対して返される値については、「[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)」を参照してください。  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>SQLColumns による大きな CLR UDT のサポート  
 **SQLColumns は**、大規模な CLR ユーザー定義型 (UDT) をサポートします。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>SQLColumns によるスパース列のサポート  
 SQLColumns の結果セットに次の 2 つの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列が追加されました。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint**|列がスパース列の場合は SQL_TRUE、それ以外の場合は SQL_FALSE になります。|  
|SS_IS_COLUMN_SET|**Smallint**|列が**column_set**列の場合は、これはSQL_TRUE。それ以外の場合は、SQL_FALSE。|  
  
 ODBC 仕様に準拠して、SS_IS_SPARSEとSS_IS_COLUMN_SETは、以前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]のバージョンに追加されたすべてのドライバー固有の列の前、および ODBC 自体によって指定されたすべての列の後に表示されます。  
  
 SQLColumns によって返される結果セットは、SQL_SOPT_SS_NAME_SCOPEの設定によって異なります。 詳細については、 [SQLSetStmtAttr を](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)参照してください。  
  
 ODBC のスパース列の詳細については、「 ODBC [&#41;のスパース列のサポート&#40;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
