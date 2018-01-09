---
title: "SQLDescribeParam |Microsoft ドキュメント"
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
helpviewer_keywords: SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
caps.latest.revision: "61"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dfe8843e8b3062f058cfc8de0235dfeecf029004
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  任意の SQL ステートメントのパラメーターを記述する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが構築され、実行、 [!INCLUDE[tsql](../../includes/tsql-md.md)] SQLDescribeParam が準備された ODBC ステートメント ハンドルで呼び出されたときに、SELECT ステートメント。 この結果セットのメタデータにより、準備されたステートメント内のパラメーターの特性が決まります。 SQLDescribeParam は、SQLExecute または SQLExecDirect が返す可能性のあるエラー コードを返すことができます。  
  
 以降で、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SQLDescribeParam を期待する結果のより正確な記述を取得できるようにします。 以前のバージョンの SQLDescribeParam によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
 新機能も[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 *ParameterSizePtr*で定義されている、対応するパラメーター マーカーの式または列の文字のサイズの定義に沿って調整された値を返すようになりました、 [ODBC仕様](http://go.microsoft.com/fwlink/?LinkId=207044)です。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client、 *ParameterSizePtr*の対応する値がある可能性があります**SQL_DESC_OCTET_LENGTH**型、または渡された無関係な列サイズ値型の場合は、SQLBindParameter には、値を無視するか (**SQL_INTEGER**など)。  
  
 ドライバーでは、次の状況で呼び出し元 SQLDescribeParam はサポートされません。  
  
-   いずれかの SQLExecDirect 後[!INCLUDE[tsql](../../includes/tsql-md.md)]UPDATE または DELETE ステートメントの FROM 句を含むです。  
  
-   ODBC ステートメントまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが HAVING 句にパラメーターを含んでいる場合、または SUM 関数の結果と比較される場合。  
  
-   ODBC ステートメントまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがパラメーターを含んでいるサブクエリに依存している場合。  
  
-   ODBC SQL ステートメントが、比較の両方の式、LIKE、定量化された述語内にパラメーター マーカーを含んでいる場合。  
  
-   クエリのいずれかのパラメーターが関数に対するパラメーターである場合。  
  
-   コメントがある場合 (/* \*/) で、[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンド。  
  
 バッチを処理するときに[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、ドライバーもサポートしていない、バッチ内の最初のステートメントの後のステートメントのパラメーター マーカー SQLDescribeParam を呼び出すことです。  
  
 SQLDescribeParam は、システム ストアド プロシージャを使用して準備されたストアド プロシージャのパラメーターの説明、 [sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md)パラメーターの特性を取得します。 sp_sproc_columns には、現在のユーザー データベース内のストアド プロシージャのデータをレポートできます。 データベース間で実行する SQLDescribeParam をストアド プロシージャの完全修飾名を準備できます。 たとえば、システム ストアド プロシージャ[sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)準備されとして任意のデータベースで実行されたことができます。  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 SQLDescribeParam を正しく準備には、空の行が任意のデータベースに接続しているときに設定が返された後に実行しますが、**マスター**です。 次のように準備ができている同じ呼び出しを現在のユーザー データベースに関係なく正常に SQLDescribeParam が発生します。  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 大きな値データ型で返される値*DataTypePtr*は、SQL_VARCHAR、SQL_VARBINARY、SQL_NVARCHAR のいずれか。 大きな値データ型のパラメーターのサイズが「無制限」であることを示す、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのセット*ParameterSizePtr*を 0 にします。 標準の実際のサイズの値が返されます**varchar**パラメーター。  
  
> [!NOTE]  
>  パラメーターが SQL_VARCHAR、SQL_VARBINARY、SQL_WVARCHAR のいずれかのパラメーターの最大サイズに既にバインドされている場合は、"無制限" ではなく、バインドされたパラメーターのサイズが返されます。  
  
 サイズが "無制限" の入力パラメーターをバインドするには、実行時データを使用する必要があります。 サイズが「無制限」の出力パラメーターをバインドすることはできません (と同様に、出力パラメーターからデータをストリーミングにメソッドがない[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)が結果セット)。  
  
 出力パラメーターの場合は、バッファーをバインドする必要があります。値が大きすぎる場合はバッファーがいっぱいになり、SQL_SUCCESS_WITH_INFO メッセージが "文字列データの右側が切り捨てられました。" という警告と共に返されます。 その後、切り捨てられたデータが破棄されます。  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam とテーブル値パラメーター  
 アプリケーションでは、SQLDescribeParam の準備されたステートメントのテーブル値パラメーターの情報を取得できます。 詳細については、次を参照してください。[準備されたステートメントのテーブル値パラメーターのメタデータ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)です。  
  
 テーブル値パラメーターの詳細については一般を参照してください[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>SQLDescribeParam による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*DataTypePtr*|*ParameterSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|日付|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 詳細については、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>SQLDescribeParam による大きな CLR UDT のサポート  
 **SQLDescribeParam**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLDescribeParam 関数](http://go.microsoft.com/fwlink/?LinkId=59339)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
