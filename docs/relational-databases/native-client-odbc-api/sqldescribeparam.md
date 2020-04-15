---
title: SQL 記述パラム |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: efe1fdccbef4f5c4a393083f6eb81efee759be5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302586"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL ステートメントのパラメーターを記述するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、SQLDescribeParam が準備された ODBC ステートメント ハンドルで呼び出されたときに[!INCLUDE[tsql](../../includes/tsql-md.md)]SELECT ステートメントを構築し、実行します。 この結果セットのメタデータにより、準備されたステートメント内のパラメーターの特性が決まります。 SQLDescribe パラムは、SQL 実行または SQLExecDirect が返す可能性のあるエラー コードを返すことができます。  
  
 データベース エンジンの機能強化を開始[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]すると、SQLDescribeParam は期待される結果をより正確に説明できます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLDescribeParam が返した値とは異なる場合があります。 詳細については、「[メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)」を参照してください。  
  
 また、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] *ParameterSizePtr*では[、ODBC 仕様](https://go.microsoft.com/fwlink/?LinkId=207044)で定義されている対応するパラメーター マーカーの列または式のサイズ (文字数) の定義に合わせて値が返されるようになりました。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントでは *、ParameterSizePtr*は型に対応する**SQL_DESC_OCTET_LENGTH**値、または型に対して SQLBindParameter に指定された無関係な列サイズ値であり、その値は無視する必要があります **(SQL_INTEGER**など)。  
  
 ドライバーは、次の状況では、呼び出しをサポートしません。  
  
-   FROM 句を含む[!INCLUDE[tsql](../../includes/tsql-md.md)]任意の UPDATE ステートメントまたは DELETE ステートメントの SQLExecDirect の後。  
  
-   ODBC ステートメントまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが HAVING 句にパラメーターを含んでいる場合、または SUM 関数の結果と比較される場合。  
  
-   ODBC ステートメントまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがパラメーターを含んでいるサブクエリに依存している場合。  
  
-   ODBC SQL ステートメントが、比較の両方の式、LIKE、定量化された述語内にパラメーター マーカーを含んでいる場合。  
  
-   クエリのいずれかのパラメーターが関数に対するパラメーターである場合。  
  
-   コマンドにコメント (/* \*/) がある場合。 [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 ステートメントのバッチを処理[!INCLUDE[tsql](../../includes/tsql-md.md)]する場合、ドライバーは、バッチの最初のステートメントの後にステートメントでパラメーター マーカーの SQLDescribeParam を呼び出すもサポートしていません。  
  
 準備されたストアド プロシージャのパラメータを記述する場合、SQLDescribeParam は、システム ストアド プロシージャ[sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md)を使用してパラメータ特性を取得します。 sp_sproc_columns現在のユーザー データベース内のストアド プロシージャのデータを報告できます。 完全修飾ストアド プロシージャ名を準備すると、SQLDescribeParam を複数のデータベースにわたって実行できます。 たとえば、システム ストアド プロシージャ[sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)は、次のように任意のデータベースで準備および実行できます。  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 準備が成功した後に SQLDescribeParam を実行すると **、master**以外のデータベースに接続されると空の行セットが返されます。 次のように準備された同じ呼び出しにより、現在のユーザー データベースに関係なく SQLDescribeParam が成功します。  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 大きな値のデータ型の場合 *、DataTypePtr*で返される値は、SQL_VARCHAR、SQL_VARBINARY、またはSQL_NVARCHARです。 大きな値のデータ型パラメーターのサイズが「無制限」であることを示すには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバー*は、パラメーターサイズ*を 0 に設定します。 標準**の varchar**パラメーターの実際のサイズの値が返されます。  
  
> [!NOTE]  
>  パラメーターが SQL_VARCHAR、SQL_VARBINARY、SQL_WVARCHAR のいずれかのパラメーターの最大サイズに既にバインドされている場合は、"無制限" ではなく、バインドされたパラメーターのサイズが返されます。  
  
 サイズが "無制限" の入力パラメーターをバインドするには、実行時データを使用する必要があります。 「無制限」サイズの出力パラメータをバインドすることはできません[(SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)が結果セットに対して行うような、出力パラメータからデータをストリーミングするメソッドはありません)。  
  
 出力パラメーターの場合は、バッファーをバインドする必要があります。値が大きすぎる場合はバッファーがいっぱいになり、SQL_SUCCESS_WITH_INFO メッセージが "文字列データの右側が切り捨てられました。" という警告と共に返されます。 その後、切り捨てられたデータが破棄されます。  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam とテーブル値パラメーター  
 アプリケーションは、SQLDescribeParam を使用して準備されたステートメントのテーブル値パラメーター情報を取得できます。 詳細については、「[準備済みステートメントのテーブル値パラメーター メタデータ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)」を参照してください。  
  
 テーブル値パラメーター全般の詳細については[、「ODBC&#41;&#40;テーブル値パラメーター」](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)を参照してください。  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>SQLDescribeParam による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*データ型Ptr*|*パラメーターサイズプラー*|*10 進数の桁数Ptr*|  
|-|-------------------|------------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8、10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19、21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26、28..34|0..7|  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>SQLDescribeParam による大きな CLR UDT のサポート  
 **大規模**な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数の記述](https://go.microsoft.com/fwlink/?LinkId=59339)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
