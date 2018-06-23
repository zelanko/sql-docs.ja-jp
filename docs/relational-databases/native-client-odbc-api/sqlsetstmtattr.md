---
title: SQLSetStmtAttr |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetStmtAttr function
ms.assetid: 799c80fd-c561-4912-8562-9229076dfd19
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3bf9b7e907bbc00febe4ef86b17bf266408b131e
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702813"
---
# <a name="sqlsetstmtattr"></a>SQLSetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、混合 (キーセット/動的) カーソル モデルをサポートしません。 SQL_ATTR_KEYSET_SIZE を使用してキーセットのサイズを設定する場合、0 以外の値を設定すると失敗します。  
  
 アプリケーションに返される行の数を宣言するすべてのステートメントで SQL_ATTR_ROW_ARRAY_SIZE を設定する、 **SQLFetch**または[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)関数呼び出しです。 ドライバーは、サーバー カーソルを指定するステートメントで SQL_ATTR_ROW_ARRAY_SIZE を使用して、カーソルからのフェッチ要求を満たすためにサーバーが生成する行ブロックのサイズを判断します。 トランザクションの分離レベルが、コミット済みのトランザクションの反復可能読み取りを保証できるレベルの場合、行のメンバーシップや順序が、動的カーソルのブロック サイズに収まる範囲内で固定されます。 カーソルは、この値で示されるブロック外では完全に動的になります。 サーバー カーソルのブロック サイズは完全に動的で、フェッチ処理のどの時点でも変更可能です。  
  
## <a name="sqlsetstmtattr-and-table-valued-parameters"></a>SQLSetStmtAttr とテーブル値パラメーター  
 SQLSetStmtAttr は、テーブル値パラメーター列の記述子フィールドにアクセスする前に、アプリケーション パラメーター記述子 (APD) の SQL_SOPT_SS_PARAM_FOCUS を設定するために使用できます。  
  
 Sqlstate いない、テーブル値パラメーター、SQLSetStmtAttr SQL_ERROR を返し、診断レコードが作成されているパラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定しようとしましたが場合 = HY024 メッセージ「無効な属性値」です。 SQL_SOPT_SS_PARAM_FOCUS は、SQL_ERROR が返されたときに変更されません。  
  
 SQL_SOPT_SS_PARAM_FOCUS に 0 を設定すると、パラメーターの記述子レコードへのアクセスが復元されます。  
  
 SQLSetStmtAttr は、SQL_SOPT_SS_NAME_SCOPE を設定することもできます。 詳細については、このトピックの後半の「SQL_SOPT_SS_NAME_SCOPE」のセクションを参照してください。  
  
 詳細については、次を参照してください。[準備されたステートメントのテーブル値パラメーターのメタデータ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlsetstmtattr-support-for-sparse-columns"></a>SQLSetStmtAttr によるスパース列のサポート  
 SQLSetStmtAttr は、SQL_SOPT_SS_NAME_SCOPE を設定するために使用します。 詳細については、このトピックの「、SQL_SOPT_SS_NAME_SCOPE」のセクションを参照してください。スパース列の詳細については、次を参照してください。[スパース列のサポート&#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)です。  
  
## <a name="statement-attributes"></a>ステートメント属性  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、次のドライバー固有のステートメント属性もサポートします。  
  
### <a name="sqlsoptsscursoroptions"></a>SQL_SOPT_SS_CURSOR_OPTIONS  
 カーソルでのドライバー固有のパフォーマンス オプションを使用するかどうかを指定します。 [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)はこれらのオプションが設定されている場合は使用できません。 既定の設定は SQL_CO_OFF です。 *ValuePtr*値型は SQLLEN です。  
  
|*ValuePtr*値|説明|  
|----------------------|-----------------|  
|SQL_CO_OFF|既定値です。 高速順方向専用、読み取り専用カーソルと autofetch を無効になり、によって**SQLGetData**順方向専用、読み取り専用のカーソルにします。 SQL_SOPT_SS_CURSOR_OPTIONS を SQL_CO_OFF に設定すると、カーソルの種類は変更されません。 つまり、高速順方向専用カーソルは高速順方向専用カーソルのままです。 カーソルの種類を変更するには、アプリケーションする必要がありますを設定別のカーソルの種類を使用して、 **SQLSetStmtAttr**/SQL_ATTR_CURSOR_TYPE です。|  
|SQL_CO_FFO|高速順方向専用、読み取り専用カーソルの場合、無効にできるように**SQLGetData**順方向専用、読み取り専用のカーソルにします。|  
|SQL_CO_AF|すべてのカーソルの種類で autofetch オプションを有効にします。 このオプションは、ステートメント ハンドルに設定した場合**SQLExecute**または**SQLExecDirect**暗黙が生成されます**SQLFetchScroll** (SQL_FIRST)。 カーソルが開かれ、最初の行バッチが 1 回のラウンドトリップでサーバーに返されます。|  
|SQL_CO_FFO_AF|autofetch オプションを設定して高速順方向専用カーソルを有効にします。 これは、SQL_CO_AF と SQL_CO_FFO の両方を指定した場合と同じです。|  
  
 これらのオプションを設定すると、サーバーは最後の行がフェッチされたことを検出した時点で、カーソルを自動的に閉じます。 アプリケーションを呼び出す必要がありますも[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) (SQL_CLOSE) または[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)ドライバーは、サーバーに閉じる通知を送信する必要はありませんが、します。  
  
 選択リストが含まれている場合、**テキスト**、 **ntext**、または**イメージ**列、高速順方向専用カーソルが動的カーソルに変換し、 **SQLGetData**は許可されています。  
  
### <a name="sqlsoptssdeferprepare"></a>SQL_SOPT_SS_DEFER_PREPARE  
 SQL_SOPT_SS_DEFER_PREPARE 属性は、ステートメントがすぐに準備ができているか、まで延期されるかどうかを判断**SQLExecute**、 [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)または[SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md)を実行します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以前のバージョンでは、このプロパティは無視されます (準備は遅延されません)。 *ValuePtr*値型は SQLLEN です。  
  
|*ValuePtr*値|説明|  
|----------------------|-----------------|  
|SQL_DP_ON|既定値です。 呼び出した後[SQLPrepare 関数](http://go.microsoft.com/fwlink/?LinkId=59360)、まで、ステートメントの準備は遅延**SQLExecute**が呼び出されたか、メタプロパティ操作 (**SQLDescribeCol**または**SQLDescribeParam**) を実行します。|  
|SQL_DP_OFF|ステートメントが準備されたとすぐに**SQLPrepare**を実行します。|  
  
### <a name="sqlsoptssregionalize"></a>SQL_SOPT_SS_REGIONALIZE  
 ステートメント レベルのデータ変換を決定します。 この属性を設定すると、日付、時刻、通貨の値を文字列値に変換する際に、ドライバーはクライアントのロケール設定を使用します。 この場合の変換は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ データ型から文字列への変換のみです。  
  
 *ValuePtr*値型は SQLLEN です。  
  
|*ValuePtr*値|説明|  
|----------------------|-----------------|  
|SQL_RE_OFF|既定値です。 ドライバーは、日付、時刻、通貨の値を文字列データに変換する際に、クライアントのロケール設定を使用しません。|  
|SQL_RE_ON|ドライバーは、日付、時刻、通貨の値を文字列データに変換する際に、クライアントのロケール設定を使用します。|  
  
 地域別の変換の設定は、通貨、数値、日付、および時刻のデータ型に適用されます。 変換の設定は、通貨、数値、日付、または時刻の値を文字列に変換するときの出力変換にのみ適用されます。  
  
> [!NOTE]  
>  ステートメント オプション SQL_SOPT_SS_REGIONALIZE が有効な場合、ドライバーは現在のユーザーのロケール レジストリ設定を使用します。 アプリケーションを設定して、たとえばを呼び出す場合、ドライバーは現在のスレッドのロケールを認めません**SetThreadLocale**です。  
  
 データ ソースの地域別の動作を変更すると、アプリケーション エラーが発生することがあります。 日付文字列を解析し、ODBC の定義に従った形式の日付文字列を受け付けるアプリケーションは、地域別の動作の値を変更することによって、悪影響を受ける可能性があります。  
  
### <a name="sqlsoptsstextptrlogging"></a>SQL_SOPT_SS_TEXTPTR_LOGGING  
 型の属性を含む列に対する操作のログ記録を切り替えます**テキスト**または**イメージ**データ。 *ValuePtr*値型は SQLLEN です。  
  
|*ValuePtr*値|説明|  
|----------------------|-----------------|  
|SQL_TL_OFF|実行される操作のログ記録を無効に**テキスト**と**イメージ**データ。|  
|SQL_TL_ON|既定値です。 実行される操作のログ記録を有効に**テキスト**と**イメージ**データ。|  
  
### <a name="sqlsoptsshiddencolumns"></a>SQL_SOPT_SS_HIDDEN_COLUMNS  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SELECT FOR BROWSE ステートメントで非表示にされた列を結果セットに公開します。 既定では、ドライバーはこのような列を公開しません。 *ValuePtr*値型は SQLLEN です。  
  
|*ValuePtr*値|説明|  
|----------------------|-----------------|  
|SQL_HC_OFF|既定値です。 FOR BROWSE 列が結果セットで非表示になります。|  
|SQL_HC_ON|FOR BROWSE 列を公開します。|  
  
### <a name="sqlsoptssquerynotificationmsgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 クエリ通知要求のメッセージ テキストを返します。  
  
### <a name="sqlsoptssquerynotificationoptions"></a>SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
 クエリ通知要求で使用するオプションを指定します。 オプションは、次に示すように、`name=value` 構文を使用した文字列で指定します。 アプリケーションがサービスを作成して、キューから通知を読み取る必要があります。  
  
 クエリ通知オプションの文字列の構文です。  
  
 `service=<service-name>[;(local database=<database>|broker instance=<broker instance>)]`  
  
 以下に例を示します。  
  
 `service=mySSBService;local database=mydb`  
  
### <a name="sqlsoptssquerynotificationtimeout"></a>SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
 クエリ通知をアクティブのままにしておく秒数を指定します。 既定値は 432,000 秒 (5 日) です。 *ValuePtr*値型は SQLLEN です。  
  
### <a name="sqlsoptssparamfocus"></a>SQL_SOPT_SS_PARAM_FOCUS  
 SQL_SOPT_SS_PARAM_FOCUS 属性は、後続の SQLBindParameter、SQLGetDescField、SQLSetDescField、SQLGetDescRec、フォーカスを指定し、SQLSetDescRec を呼び出します。  
  
 SQL_SOPT_SS_PARAM_FOCUS の型は SQLULEN です。  
  
 既定値は 0 で、SQL ステートメントのパラメーター マーカーに対応するパラメーターが、上記の呼び出しで指定されます。 テーブル値パラメーターのパラメーター番号に設定すると、そのテーブル値パラメーターの列が上記の呼び出しで指定されます。 テーブル値パラメーターのパラメーター番号以外の値に設定すると、エラー IM020 ("パラメーターのフォーカスがテーブル値パラメーターを参照していません") が返されます。  
  
### <a name="sqlsoptssnamescope"></a>SQL_SOPT_SS_NAME_SCOPE  
 SQL_SOPT_SS_NAME_SCOPE 属性は、後続のカタログ関数呼び出しの名前スコープを指定します。 SQLColumns によって返される結果セットは、SQL_SOPT_SS_NAME_SCOPE の設定によって異なります。  
  
 SQL_SOPT_SS_NAME_SCOPE の型は SQLULEN です。  
  
|*ValuePtr*値|説明|  
|----------------------|-----------------|  
|SQL_SS_NAME_SCOPE_TABLE|既定値です。<br /><br /> テーブル値パラメーターを使用する場合は、実際のテーブルのメタデータが返される必要があることを示します。<br /><br /> SQLColumns が、スパースのメンバーではない列のみを返す、スパース列機能を使用する場合**column_set**です。|  
|SQL_SS_NAME_SCOPE_TABLE_TYPE|アプリケーションが実際のテーブルではなくテーブル型のメタデータを必要としていること (テーブル型のメタデータが返される必要があること) を示します。 その後、アプリケーションとして、テーブル値パラメーターの TYPE_NAME を渡します、 *TableName*パラメーター。|  
|SQL_SS_NAME_SCOPE_EXTENDED|SQLColumns に返しますに関係なく、すべての列がスパース列機能を使用する場合**column_set**メンバーシップです。|  
|SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET|SQLColumns には、スパースのメンバーである列のみが返されます、スパース列機能を使用する場合**column_set**です。|  
|SQL_SS_NAME_SCOPE_DEFAULT|SQL_SS_NAME_SCOPE_TABLE と同等です。|  
  
 SS_TYPE_CATALOG_NAME と SS_TYPE_SCHEMA_NAME は併用、 *CatalogName*と*SchemaName*パラメーターをそれぞれカタログおよびテーブル値パラメーターのスキーマを識別します。 テーブル値パラメーターのメタデータの取得が完了すると、アプリケーションによって、SQL_SOPT_SS_NAME_SCOPE は既定値 SQL_SS_NAME_SCOPE_TABLE に設定し直す必要があります。  
  
 SQL_SOPT_SS_NAME_SCOPE が SQL_SS_NAME_SCOPE_TABLE に設定されると、リンク サーバーへのクエリは失敗します。 SQLColumns または SQLPrimaryKeys とサーバー コンポーネントを含むカタログの呼び出しは失敗します。  
  
 SQL_SOPT_SS_NAME_SCOPE を無効な値に設定しようとすると、SQL_ERROR が返され、"属性の値が正しくありません" というメッセージを含む SQLSTATE HY024 の診断レコードが生成されます。  
  
 SQL_SOPT_SS_NAME_SCOPE 以外の値が入って SQLTables、SQLColumns、または SQLPrimaryKeys を呼び出すし、カタログ関数 SQL_SS_NAME_SCOPE_TABLE、SQL_ERROR が返されます。 "関数のシーケンス エラーです (SQL_SOPT_SS_NAME_SCOPE が SQL_SS_NAME_SCOPE_TABLE に設定されていません)" というメッセージを含む SQLSTATE HY010 の診断レコードが生成されます。  
  
## <a name="see-also"></a>参照  
 [SQLGetStmtAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59355)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
