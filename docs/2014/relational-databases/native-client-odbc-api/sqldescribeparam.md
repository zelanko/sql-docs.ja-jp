---
title: SQLDescribeParam |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d52d68cc0cd31e9dbb3da25c46901e126252607
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067735"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
  SQL ステートメントのパラメーターを記述するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client odbc ドライバーは、準備さ[!INCLUDE[tsql](../../includes/tsql-md.md)]れた Odbc ステートメントハンドルで SQLDescribeParam が呼び出されたときに、SELECT ステートメントを構築して実行します。 この結果セットのメタデータにより、準備されたステートメント内のパラメーターの特性が決まります。 SQLDescribeParam は、SQLExecute または SQLExecDirect が返す可能性のあるエラーコードを返すことができます。  
  
 で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]始まるデータベースエンジンの機能強化により、SQLDescribeParam は、予期される結果についてより正確な説明を取得できます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で SQLDescribeParam によって返された値とは異なる場合があります。 詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。  
  
 また、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] *parametersizeptr*は、 [ODBC 仕様](https://go.microsoft.com/fwlink/?LinkId=207044)で定義されている、対応するパラメーターマーカーの列または式のサイズ (文字数) の定義に合わせて値を返すようになりました。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、 *parametersizeptr*は、型の`SQL_DESC_OCTET_LENGTH`の対応する値、または型の SQLBindParameter に指定された関係のない列サイズの値になる可能性があり`SQL_INTEGER`ます。この値は無視する必要があります (など)。  
  
 ドライバーは、次の状況での SQLDescribeParam の呼び出しをサポートしていません。  
  
-   SQLExecDirect の後に[!INCLUDE[tsql](../../includes/tsql-md.md)] 、from 句を含む UPDATE または DELETE ステートメントを実行します。  
  
-   ODBC ステートメントまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが HAVING 句にパラメーターを含んでいる場合、または SUM 関数の結果と比較される場合。  
  
-   ODBC ステートメントまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがパラメーターを含んでいるサブクエリに依存している場合。  
  
-   ODBC SQL ステートメントが、比較の両方の式、LIKE、定量化された述語内にパラメーター マーカーを含んでいる場合。  
  
-   クエリのいずれかのパラメーターが関数に対するパラメーターである場合。  
  
-   コマンドにコメント (/* \*/) がある場合。 [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 ステートメントの[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチを処理する場合、ドライバーはバッチ内の最初のステートメントの後にあるステートメント内のパラメーターマーカーに対して SQLDescribeParam を呼び出すこともサポートしていません。  
  
 SQLDescribeParam では、準備されたストアドプロシージャのパラメーターを記述するときに、システムストアドプロシージャ[sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql)を使用してパラメーターの特性を取得します。 sp_sproc_columns は、現在のユーザーデータベース内のストアドプロシージャのデータをレポートできます。 完全に修飾されたストアドプロシージャ名を準備すると、データベース間で SQLDescribeParam を実行できるようになります。 たとえば、システムストアドプロシージャ[sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql)を準備し、任意のデータベースで次のように実行できます。  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 準備が正常に完了した後に SQLDescribeParam を実行すると、データベース`master`に接続しているときに空の行セットが返されます。 次のように準備された同じ呼び出しは、現在のユーザーデータベースに関係なく SQLDescribeParam を成功させます。  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 大きな値のデータ型の場合、 *DataTypePtr*で返される値は SQL_VARCHAR、SQL_VARBINARY、または SQL_NVARCHAR です。 大きな値のデータ型パラメーターのサイズが "無制限" であることを示すため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、NATIVE Client ODBC ドライバーは*parametersizeptr*を0に設定します。 標準の `varchar` 型パラメーターでは実際のサイズ値が返されます。  
  
> [!NOTE]  
>  パラメーターが SQL_VARCHAR、SQL_VARBINARY、SQL_WVARCHAR のいずれかのパラメーターの最大サイズに既にバインドされている場合は、"無制限" ではなく、バインドされたパラメーターのサイズが返されます。  
  
 サイズが "無制限" の入力パラメーターをバインドするには、実行時データを使用する必要があります。 "無制限" サイズの出力パラメーターをバインドすることはできません ( [SQLGetData](sqlgetdata.md)が結果セットに対して行うように、出力パラメーターからデータをストリーミングする方法はありません)。  
  
 出力パラメーターの場合は、バッファーをバインドする必要があります。値が大きすぎる場合はバッファーがいっぱいになり、SQL_SUCCESS_WITH_INFO メッセージが "文字列データの右側が切り捨てられました。" という警告と共に返されます。 その後、切り捨てられたデータが破棄されます。  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam とテーブル値パラメーター  
 アプリケーションでは、SQLDescribeParam を使用して、準備されたステートメントのテーブル値パラメーター情報を取得できます。 詳細については、「準備された[ステートメントのテーブル値パラメーターのメタデータ](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)」を参照してください。  
  
 一般的なテーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>SQLDescribeParam による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*DataTypePtr*|*ParameterSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|日付|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8、10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19、21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26、28..34|0..7|  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>SQLDescribeParam による大きな CLR UDT のサポート  
 `SQLDescribeParam` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLDescribeParam 関数](https://go.microsoft.com/fwlink/?LinkId=59339)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
