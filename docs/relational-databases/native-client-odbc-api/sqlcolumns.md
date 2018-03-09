---
title: "SQLColumns |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 661c678e8d98d1b4d3f88c29d6d0b786b4e686d4
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumns**値が存在するかどうかに関係なく SQL_SUCCESS を返します、 *CatalogName*、 *TableName*、または*ColumnName*パラメーター。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
> [!NOTE]  
>  大きな値型の場合、すべての長さパラメーターが SQL_SS_LENGTH_UNLIMITED という値で返されます。  
  
 **SQLColumns**は静的サーバー カーソルで実行できます。 実行すると**SQLColumns**更新可能な (動的カーソルまたはキーセット カーソル) では、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
 ODBC 2 です。*x*でワイルドカードを使用していないアプリケーション*TableName*、 **SQLColumns**に関する情報の名前と一致するテーブルを返します*TableName*は、現在のユーザーによって所有されているとします。 かどうか、現在のユーザーを所有していない名前に一致するテーブル、 *TableName*パラメーター、 **SQLColumns**テーブル名が一致する他のユーザーが所有するテーブルに関する情報を返します、 *TableName*パラメーター。 ODBC 2 です。*x*ワイルドカードを使用してアプリケーションを**SQLColumns**すべての名前と一致するテーブルを返します*TableName*です。 ODBC 3 です。*x*アプリケーション**SQLColumns**すべての名前と一致するテーブルを返します*TableName*所有者またはワイルドカードを使用するかどうかに関係なく。  
  
 次の表は、結果セットによって返される列の一覧です。  
  
|列名|Description|  
|-----------------|-----------------|  
|DATA_TYPE|SQL_VARCHAR、SQL_VARBINARY、または SQL_WVARCHAR を返します、 **varchar (max)**データ型。|  
|TYPE_NAME|"Varchar"、"varbinary"、または"nvarchar"を返します、 **varchar (max)**、 **varbinary (max)**、および**nvarchar (max)**データ型。|  
|COLUMN_SIZE|Returns SQL_SS_LENGTH_UNLIMITED for **varchar(max)** data types indicating that the size of the column is unlimited.|  
|BUFFER_LENGTH|Returns SQL_SS_LENGTH_UNLIMITED for **varchar(max)** data types indicating that the size of the buffer is unlimited.|  
|SQL_DATA_TYPE|SQL_VARCHAR、SQL_VARBINARY、または SQL_WVARCHAR を返します、 **varchar (max)**データ型。|  
|CHAR_OCTET_LENGTH|char 型または binary 型の列の最大長を返します。 サイズが無制限であることを示す場合は 0 を返します。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|XML スキーマ コレクション名が定義されているカタログの名前を返します。 カタログ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|XML スキーマ コレクション名が定義されているスキーマの名前を返します。 スキーマ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_NAME|XML スキーマ コレクションの名前を返します。 名前が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_UDT_CATALOG_NAME|UDT (ユーザー定義型) を含むカタログの名前です。|  
|SS_UDT_SCHEMA_NAME|UDT を含むスキーマの名前。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|UDT のアセンブリ修飾名です。|  
  
 Udt の場合、既存の TYPE_NAME 列が; UDT の名前を示すために使用されます。そのために追加の列は追加されませんの結果セットに**SQLColumns**または[SQLProcedureColumns](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md)です。 UDT 列または UDT パラメーターの場合、DATA_TYPE は SQL_SS_UDT です。  
  
 サーバーからパラメーターの UDT に関する追加のメタデータ プロパティを返したり、サーバーでこのメタデータ プロパティの情報が必要となる場合は、上記に定義したドライバー固有の新しい記述子を使用して、UDT のメタデータ プロパティの取得や設定を行えます。  
  
 クライアントが接続する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カタログ入力パラメーターには、他のカタログから情報を返しませんの値を NULL またはワイルドカードを使用して、SQLColumns を呼び出すとします。 代わりに、現在のカタログに関する情報だけが返されます。 クライアントを決定するカタログは、目的のテーブルがある SQLTables を呼び出す最初ことができます。 クライアントはそのカタログの値をそのテーブル内の列に関する情報を取得するのに SQLColumns 呼び出しでカタログ入力パラメーターの使用してできます。  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns とテーブル値パラメーター  
 SQLColumns によって返される結果セットは、SQL_SOPT_SS_NAME_SCOPE の設定によって異なります。 詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。 テーブル値パラメーター用に次の列が追加されました。  
  
|列名|データ型|目次|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|TABLE_TYPE の列では、列が計算列の場合は SQL_TRUE、それ以外の場合は SQL_FALSE になります。|  
|SS_IS_IDENTITY|Smallint|列が ID 列の場合は SQL_TRUE、それ以外の場合は SQL_FALSE になります。|  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>SQLColumns による機能強化された日付と時刻のサポート  
 日付/時刻型に対して返される値については、次を参照してください。[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>SQLColumns による大きな CLR UDT のサポート  
 **SQLColumns**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>SQLColumns によるスパース列のサポート  
 2 つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLColumns の結果セットに特定の列が追加されました。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint**|列がスパース列の場合は SQL_TRUE、それ以外の場合は SQL_FALSE になります。|  
|SS_IS_COLUMN_SET|**Smallint**|列がある場合、 **column_set**列は SQL_TRUE、それ以外の SQL_FALSE します。|  
  
 SS_IS_SPARSE と SS_IS_COLUMN_SET で前に追加されたすべてのドライバー固有の列に表示、ODBC 仕様に準拠して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョンよりも前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、および ODBC 自体によって指定すべての列の後にします。  
  
 SQLColumns によって返される結果セットは、SQL_SOPT_SS_NAME_SCOPE の設定によって異なります。 詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
 ODBC のスパース列の詳細については、次を参照してください。[スパース列のサポート &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLColumns 関数](http://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
