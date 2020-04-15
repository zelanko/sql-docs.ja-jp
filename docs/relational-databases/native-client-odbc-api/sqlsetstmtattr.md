---
title: をクリックして行う |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetStmtAttr function
ms.assetid: 799c80fd-c561-4912-8562-9229076dfd19
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2fc3bf094504415cc2ec27c6c472cce747b53481
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301901"
---
# <a name="sqlsetstmtattr"></a>SQLSetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、混合 (キーセット/動的) カーソル モデルをサポートしません。 SQL_ATTR_KEYSET_SIZE を使用してキーセットのサイズを設定する場合、0 以外の値を設定すると失敗します。  
  
 アプリケーションは、すべてのステートメントにSQL_ATTR_ROW_ARRAY_SIZEを設定して **、SQLFetch**関数呼び出しまたは[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)関数呼び出しで返される行数を宣言します。 ドライバーは、サーバー カーソルを指定するステートメントで SQL_ATTR_ROW_ARRAY_SIZE を使用して、カーソルからのフェッチ要求を満たすためにサーバーが生成する行ブロックのサイズを判断します。 トランザクションの分離レベルが、コミット済みのトランザクションの反復可能読み取りを保証できるレベルの場合、行のメンバーシップや順序が、動的カーソルのブロック サイズに収まる範囲内で固定されます。 カーソルは、この値で示されるブロック外では完全に動的になります。 サーバー カーソルのブロック サイズは完全に動的で、フェッチ処理のどの時点でも変更可能です。  
  
## <a name="sqlsetstmtattr-and-table-valued-parameters"></a>SQLSetStmtAttr とテーブル値パラメーター  
 SQLSetStmtAttr を使用すると、テーブル値パラメーター列の記述子フィールドにアクセスする前に、アプリケーション・パラメーター記述子 (APD) にSQL_SOPT_SS_PARAM_FOCUSを設定できます。  
  
 テーブル値パラメーターでないパラメーターの序数にSQL_SOPT_SS_PARAM_FOCUSを設定しようとすると、SQLSetStmtAttr はSQL_ERRORを戻し、診断レコードは SQLSTATE = HY024 およびメッセージ「無効な属性値」で作成されます。 SQL_SOPT_SS_PARAM_FOCUS は、SQL_ERROR が返されたときに変更されません。  
  
 SQL_SOPT_SS_PARAM_FOCUS に 0 を設定すると、パラメーターの記述子レコードへのアクセスが復元されます。  
  
 また、SQL_SOPT_SS_NAME_SCOPEを設定するために使用することもできます。 詳細については、このトピックの後半の「SQL_SOPT_SS_NAME_SCOPE」のセクションを参照してください。  
  
 詳細については、「[準備済みステートメントのテーブル値パラメーター メタデータ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlsetstmtattr-support-for-sparse-columns"></a>SQLSetStmtAttr によるスパース列のサポート  
 SQL_SOPT_SS_NAME_SCOPEを設定するために使用できます。 詳細については、このトピックの「SQL_SOPT_SS_NAME_SCOPE」セクションを参照してください。スパース列の詳細については、「 [ODBC&#41;&#40;スパース列のサポート](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)」を参照してください。  
  
## <a name="statement-attributes"></a>ステートメント属性  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、次のドライバー固有のステートメント属性もサポートします。  
  
### <a name="sql_sopt_ss_cursor_options"></a>SQL_SOPT_SS_CURSOR_OPTIONS  
 カーソルでのドライバー固有のパフォーマンス オプションを使用するかどうかを指定します。 これらのオプションが設定されている場合は[、SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)は使用できません。 既定の設定は SQL_CO_OFF です。 *値が*SQLLEN 型です。  
  
|*値Ptr*値|説明|  
|----------------------|-----------------|  
|SQL_CO_OFF|既定値。 高速順方向専用の読み取り専用カーソルと自動フェッチを無効にし、前方専用の読み取り専用カーソルで**SQLGetData**を有効にします。 SQL_SOPT_SS_CURSOR_OPTIONS を SQL_CO_OFF に設定すると、カーソルの種類は変更されません。 つまり、高速順方向専用カーソルは高速順方向専用カーソルのままです。 カーソルの種類を変更するには、アプリケーションは**SQLSetStmtAttr**/SQL_ATTR_CURSOR_TYPEを使用して別のカーソルの種類を設定する必要があります。|  
|SQL_CO_FFO|高速順方向専用、読み取り専用カーソルを有効にし、前方専用の読み取り専用カーソルで**SQLGetData**を無効にします。|  
|SQL_CO_AF|すべてのカーソルの種類で autofetch オプションを有効にします。 ステートメント ハンドルに対してこのオプションを設定すると **、SQLExecute**または**SQLExecDirect**は暗黙的な**SQLFetchScroll** (SQL_FIRST) を生成します。 カーソルが開かれ、最初の行バッチが 1 回のラウンドトリップでサーバーに返されます。|  
|SQL_CO_FFO_AF|autofetch オプションを設定して高速順方向専用カーソルを有効にします。 これは、SQL_CO_AF と SQL_CO_FFO の両方を指定した場合と同じです。|  
  
 これらのオプションを設定すると、サーバーは最後の行がフェッチされたことを検出した時点で、カーソルを自動的に閉じます。 アプリケーションは[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) (SQL_CLOSE) または[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)を呼び出す必要がありますが、ドライバーはサーバーに閉じる通知を送信する必要はありません。  
  
 選択リストに**テキスト** **、ntext、** または**image**列が含まれている場合、高速順方向専用カーソルは動的カーソルに変換され **、SQLGetData**が使用できます。  
  
### <a name="sql_sopt_ss_defer_prepare"></a>SQL_SOPT_SS_DEFER_PREPARE  
 SQL_SOPT_SS_DEFER_PREPARE属性は、ステートメントをすぐに準備するか **、SQLDescribeCol**または[SQLDescribe](../../relational-databases/native-client-odbc-api/sqldescribecol.md) [パラム](../../relational-databases/native-client-odbc-api/sqldescribeparam.md)が実行されるまで延期するかを決定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以前のバージョンでは、このプロパティは無視されます (準備は遅延されません)。 *値が*SQLLEN 型です。  
  
|*値Ptr*値|説明|  
|----------------------|-----------------|  
|SQL_DP_ON|既定値。 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を呼び出した後、ステートメントの準備は **、SQLExecute**が呼び出されるか、またはメタ プロパティ操作 (**SQLDescribeCol**または**SQLDescribeParam**) が実行されるまで延期されます。|  
|SQL_DP_OFF|ステートメントは **、SQLPrepare が**実行されるとすぐに準備されます。|  
  
### <a name="sql_sopt_ss_regionalize"></a>SQL_SOPT_SS_REGIONALIZE  
 ステートメント レベルのデータ変換を決定します。 この属性を設定すると、日付、時刻、通貨の値を文字列値に変換する際に、ドライバーはクライアントのロケール設定を使用します。 この場合の変換は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ データ型から文字列への変換のみです。  
  
 *値が*SQLLEN 型です。  
  
|*値Ptr*値|説明|  
|----------------------|-----------------|  
|SQL_RE_OFF|既定値。 ドライバーは、日付、時刻、通貨の値を文字列データに変換する際に、クライアントのロケール設定を使用しません。|  
|SQL_RE_ON|ドライバーは、日付、時刻、通貨の値を文字列データに変換する際に、クライアントのロケール設定を使用します。|  
  
 地域別の変換の設定は、通貨、数値、日付、および時刻のデータ型に適用されます。 変換の設定は、通貨、数値、日付、または時刻の値を文字列に変換するときの出力変換にのみ適用されます。  
  
> [!NOTE]  
>  ステートメント オプション SQL_SOPT_SS_REGIONALIZE が有効な場合、ドライバーは現在のユーザーのロケール レジストリ設定を使用します。 たとえば **、SetThreadLocale**を呼び出すなどして、アプリケーションが設定した場合、ドライバーは現在のスレッドのロケールを受け入れません。  
  
 データ ソースの地域別の動作を変更すると、アプリケーション エラーが発生することがあります。 日付文字列を解析し、ODBC の定義に従った形式の日付文字列を受け付けるアプリケーションは、地域別の動作の値を変更することによって、悪影響を受ける可能性があります。  
  
### <a name="sql_sopt_ss_textptr_logging"></a>SQL_SOPT_SS_TEXTPTR_LOGGING  
 SQL_SOPT_SS_TEXTPTR_LOGGING属性は、**テキスト**または**イメージ**データを含む列に対する操作のロギングを切り替えます。 *値が*SQLLEN 型です。  
  
|*値Ptr*値|説明|  
|----------------------|-----------------|  
|SQL_TL_OFF|**テキスト**および**イメージ**データに対して実行された操作のログを無効にします。|  
|SQL_TL_ON|既定値。 **テキスト**および**イメージ**データに対して実行される操作のログを有効にします。|  
  
### <a name="sql_sopt_ss_hidden_columns"></a>SQL_SOPT_SS_HIDDEN_COLUMNS  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SELECT FOR BROWSE ステートメントで非表示にされた列を結果セットに公開します。 既定では、ドライバーはこのような列を公開しません。 *値が*SQLLEN 型です。  
  
|*値Ptr*値|説明|  
|----------------------|-----------------|  
|SQL_HC_OFF|既定値。 FOR BROWSE 列が結果セットで非表示になります。|  
|SQL_HC_ON|FOR BROWSE 列を公開します。|  
  
### <a name="sql_sopt_ss_querynotification_msgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 クエリ通知要求のメッセージ テキストを返します。  
  
### <a name="sql_sopt_ss_querynotification_options"></a>SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
 クエリ通知要求で使用するオプションを指定します。 オプションは、次に示すように、`name=value` 構文を使用した文字列で指定します。 アプリケーションがサービスを作成して、キューから通知を読み取る必要があります。  
  
 クエリ通知オプションの構文を次に示します。  
  
 `service=<service-name>[;(local database=<database>|broker instance=<broker instance>)]`  
  
 次に例を示します。  
  
 `service=mySSBService;local database=mydb`  
  
### <a name="sql_sopt_ss_querynotification_timeout"></a>SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
 クエリ通知をアクティブのままにしておく秒数を指定します。 デフォルト値は 432000 秒 (5 日) です。 *値が*SQLLEN 型です。  
  
### <a name="sql_sopt_ss_param_focus"></a>SQL_SOPT_SS_PARAM_FOCUS  
 SQL_SOPT_SS_PARAM_FOCUS 属性は、後続の SQLBind パラメーター、SQLGetDescField、SQL セットデスフィールド、SQLGetDescRec、および SQLSetDescRec 呼び出しのフォーカスを指定します。  
  
 SQL_SOPT_SS_PARAM_FOCUS の型は SQLULEN です。  
  
 既定値は 0 で、SQL ステートメントのパラメーター マーカーに対応するパラメーターが、上記の呼び出しで指定されます。 テーブル値パラメーターのパラメーター番号に設定すると、そのテーブル値パラメーターの列が上記の呼び出しで指定されます。 テーブル値パラメーターのパラメーター番号以外の値に設定すると、エラー IM020 ("パラメーターのフォーカスがテーブル値パラメーターを参照していません") が返されます。  
  
### <a name="sql_sopt_ss_name_scope"></a>SQL_SOPT_SS_NAME_SCOPE  
 SQL_SOPT_SS_NAME_SCOPE 属性は、後続のカタログ関数呼び出しの名前スコープを指定します。 SQLColumns によって返される結果セットは、SQL_SOPT_SS_NAME_SCOPEの設定によって異なります。  
  
 SQL_SOPT_SS_NAME_SCOPE の型は SQLULEN です。  
  
|*値Ptr*値|説明|  
|----------------------|-----------------|  
|SQL_SS_NAME_SCOPE_TABLE|既定値。<br /><br /> テーブル値パラメーターを使用する場合は、実際のテーブルのメタデータが返される必要があることを示します。<br /><br /> スパース列機能を使用すると、 SQLColumns はスパース**column_set**のメンバーではない列のみを返します。|  
|SQL_SS_NAME_SCOPE_TABLE_TYPE|アプリケーションが実際のテーブルではなくテーブル型のメタデータを必要としていること (テーブル型のメタデータが返される必要があること) を示します。 その後、アプリケーションはテーブル値パラメーターのTYPE_NAMEを*TableName*パラメーターとして渡します。|  
|SQL_SS_NAME_SCOPE_EXTENDED|スパース列機能を使用すると、SQLColumns は、メンバーシップに関係なく、すべての列**column_set**返します。|  
|SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET|スパース列機能を使用すると、 SQLColumns はスパース**column_set**のメンバーである列のみを返します。|  
|SQL_SS_NAME_SCOPE_DEFAULT|SQL_SS_NAME_SCOPE_TABLE と同等です。|  
  
 SS_TYPE_CATALOG_NAMEとSS_TYPE_SCHEMA_NAMEは、それぞれ*CatalogName*パラメーターと*SchemaName*パラメーターと共に使用され、テーブル値パラメーターのカタログとスキーマを識別します。 テーブル値パラメーターのメタデータの取得が完了すると、アプリケーションによって、SQL_SOPT_SS_NAME_SCOPE は既定値 SQL_SS_NAME_SCOPE_TABLE に設定し直す必要があります。  
  
 SQL_SOPT_SS_NAME_SCOPE が SQL_SS_NAME_SCOPE_TABLE に設定されると、リンク サーバーへのクエリは失敗します。 サーバー コンポーネントを含むカタログを使用して SQLColumns または SQLPrimaryKeys を呼び出すと、失敗します。  
  
 SQL_SOPT_SS_NAME_SCOPE を無効な値に設定しようとすると、SQL_ERROR が返され、"属性の値が正しくありません" というメッセージを含む SQLSTATE HY024 の診断レコードが生成されます。  
  
 SQL_SS_NAME_SCOPE_TABLE以外の値を持つときに、その他のカタログ関数が呼び出SQL_SOPT_SS_NAME_SCOPE場合は、SQL_ERROR SQL_SS_NAME_SCOPE_TABLEが返されます。 "関数のシーケンス エラーです (SQL_SOPT_SS_NAME_SCOPE が SQL_SS_NAME_SCOPE_TABLE に設定されていません)" というメッセージを含む SQLSTATE HY010 の診断レコードが生成されます。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59355)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
