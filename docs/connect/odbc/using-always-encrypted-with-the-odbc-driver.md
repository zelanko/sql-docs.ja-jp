---
title: "SQL Server 用 ODBC Driver 13.1 で Always Encrypted を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e306b8-9dde-4846-8d64-c528e2ffe479
caps.latest.revision: 3
ms.author: v-chojas
manager: jhubbard
author: MightyPen
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: d28b647de71c5064dfbe0d49f399119f6a9ac283
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="using-always-encrypted-with-the-odbc-driver-131-for-sql-server"></a>SQL Server 用 ODBC Driver 13.1 で Always Encrypted を使用します。
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

この記事の内容を使用する ODBC アプリケーションを開発する方法について情報を提供する[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[SQL Server 用 ODBC Driver 13.1](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)です。

Always Encrypted を使用すると、クライアント アプリケーションは SQL Server または Azure SQL データベースにデータまたは暗号化キーを開示することなく、機密データを暗号化することができます。 Always Encrypted が有効になっているドライバーなどが、SQL Server 用 ODBC Driver 13.1 がこれを透過的に暗号化およびクライアント アプリケーション内の機密データを復号化を実現します。 ドライバーは、どのクエリ パラメーターが機密データベース列 (Always Encrypted を使用して保護される) に対応するかを自動的に決定し、SQL Server または Azure SQL データベースにデータを渡す前にこれらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、「 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。

### <a name="prerequisites"></a>前提条件

データベースで Always Encrypted を構成します。 この処理には、Always Encrypted キーのプロビジョニング、および選択したデータベース列の暗号化の設定が含まれます。 Always Encrypted が構成されたデータベースがない場合は、「 [Always Encrypted の作業の開始](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted)」の手順に従います。 具体的には、データベースは、列マスター_キー (CMK)、列暗号化キー (CEK)、およびその CEK を使用して暗号化された 1 つまたは複数の列を含むテーブルのメタデータ定義を含める必要があります。

### <a name="enabling-always-encrypted-in-an-odbc-application"></a>ODBC アプリケーションで Always Encrypted を有効にします。

パラメーターの暗号化と暗号化の結果セット列の暗号化解除の両方を有効にする最も簡単な方法は、の値を設定して、`ColumnEncryption`接続文字列キーワードを**有効**です。 Always Encrypted を使用する接続文字列の例を次に示します。

```
SQLWCHAR *connString = L"Driver={ODBC Driver 13 for SQL Server};Server={myServer};Trusted_Connection=yes;ColumnEncryption=Enabled;";
```

常に暗号化された可能性がありますも有効にする DSN の構成で使用して、同じキーと値 (存在する場合、接続文字列の設定によって上書きされます)、またはプログラムによって、`SQL_COPT_SS_COLUMN_ENCRYPTION`接続前の属性です。 この方法を設定すると、接続文字列または DSN に設定された値が上書き。

```
 SQLSetConnectAttr(hdbc, SQL_COPT_SS_COLUMN_ENCRYPTION, (SQLPOINTER)SQL_COLUMN_ENCRYPTION_ENABLE, 0);
```

接続を有効にすると、個々 のクエリの Always Encrypted の動作を調整可能性があります。 参照してください[、パフォーマンスへの影響の Always Encrypted を制御する](#controlling-the-performance-impact-of-always-encrypted)の下の詳細についてはします。

Always Encrypted を有効にされている暗号化または暗号化解除を成功させるための十分な注意してください。また、ことを確認する必要があります。

- アプリケーションが、データベース内の Always Encrypted キーに関するメタデータへのアクセスに必要な *VIEW ANY COLUMN MASTER KEY DEFINITION* および *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* データベース権限を持っている。 詳細については、「[データベース権限](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions)です。

- アプリケーションは、照会された暗号化列で Cek を保護する CMK にアクセスできます。 これは、CMK を格納するキー ストア プロバイダーによって異なります。 参照してください[列マスター キー ストアの操作](#working-with-column-master-key-stores)詳細についてはします。

### <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>暗号化された列のデータを取得および変更する

接続で Always Encrypted を有効すると、標準の ODBC Api を使用することができます (を参照してください[ODBC サンプル コード](https://code.msdn.microsoft.com/windowsapps/ODBC-sample-191624ae/sourcecode?fileId=51137&pathId=1980325953)または[ODBC プログラマ リファレンス](https://msdn.microsoft.com/library/ms714177(v=vs.85).aspx)) を取得または暗号化されたデータベース列のデータを変更します。 データベース権限と列マスター _ キーにアクセスできる、ドライバーでは、暗号化された列をターゲットし、する同様の動作に透過的に暗号化された列から取得されたデータを復号化するクエリ パラメーターを暗号化します必要なアプリケーションがある場合、。列が暗号化されていない場合、アプリケーションです。

Always Encrypted が有効でない場合は、暗号化された列の対象とするパラメーターを持つクエリは失敗します。 クエリには、暗号化された列をターゲットとするパラメーターがあるない限り、データはまだ、暗号化された列から取得できます。 ただし、ドライバーは、暗号化の解除を試行しませんし、アプリケーションが、暗号化されたバイナリ データ (バイト配列) として表示されます。

次の表は、Always Encrypted が有効かどうかに応じて、クエリの動作をまとめたものです。

|クエリの特性 | Always Encrypted が有効になっており、アプリケーションがキーとキー メタデータにアクセスできる|Always Encrypted が有効になっており、アプリケーションがキーまたはキー メタデータにアクセスできない | Always Encrypted が無効になっている|
|:---|:---|:---|:---|
| 暗号化された列をターゲットとするパラメーターです。 | パラメーター値は透過的に暗号化されます。 | [エラー] | [エラー]|
| 暗号化された列をターゲットとするパラメーターを指定せず、暗号化された列からデータを取得します。| 暗号化された列の結果は透過的に暗号化解除されます。 アプリケーションでは、プレーン テキスト列の値を受け取ります。 | [エラー] | 暗号化された列の結果は暗号化解除されません。 アプリケーションは、バイト配列として暗号化された値を受け取ります。

次の例は、暗号化された列のデータを取得および変更する方法を示しています。 例には、次のスキーマを持つテーブルがあるとします。 SSN 列と BirthDate 列が暗号化されていることに注意してください。

```
CREATE TABLE [dbo].[Patients](
 [PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY] )
 GO
```

#### <a name="data-insertion-example"></a>データの挿入の例

この例では、Patients テーブルに列を挿入します。 次のことを考慮してください。

- このサンプル コードの暗号化に固有のものは何もありません。 ドライバーは自動的に検出し、暗号化された列をターゲット SSN と date パラメーターの値を暗号化します。 これにより、アプリケーションに対して暗号化が透過的に実行されます。

- 暗号化された列を含め、データベース列に挿入された値はバインドされたパラメーターとして渡されます (を参照してください[SQLBindParameter 関数](https://msdn.microsoft.com/library/ms710963(v=vs.85).aspx))。 中にパラメーターを使用する省略可能な (ただし、SQL インジェクションを防ぐのに役立つのでを強くお勧め) は、暗号化されていない列に値を送信するときは、暗号化された列をターゲットとする値に必要です。 SSN または BirthDate 列に挿入された値は、クエリ ステートメントに埋め込まれたリテラルとして渡された、ドライバーが暗号化またはその他のクエリ内のリテラルの処理を行いませんため、クエリは失敗します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。

- マップされる SQL_CHAR に SSN 列に挿入されるパラメーターの SQL 型が設定されている、 **char** SQL Server データ型 (`rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);`)。 マップされる SQL_WCHAR にパラメーターの型が設定されたかどうかは**nchar**、Always Encrypted は nchar の暗号化された値から暗号化された char 値へのサーバー側の変換はサポートされていない、クエリは失敗します。 参照してください[ODBC プログラマ リファレンス--付録 d: データ型](https://msdn.microsoft.com/library/ms713607.aspx)については、データ型マッピングします。

```
    SQL_DATE_STRUCT date;
    SQLLEN cbdate;   // size of date structure  

    SQLCHAR SSN[12];
    strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

    SQLWCHAR* firstName = L"Catherine";
    SQLWCHAR* lastName = L"Abel";
    SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

    // Initialize the date structure  
    date.day = 10;
    date.month = 9;
    date.year = 1996;

    // Size of structures   
    cbdate = sizeof(SQL_DATE_STRUCT);

    SQLRETURN rc = 0;

    string queryText = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?) ";

    rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

    //SSN
    rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);
    //FirstName
    rc = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)firstName, 0, &cbFirstName);
    //LastName
    rc = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);
    //BirthDate
    rc = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 10, 0, (SQLPOINTER)&date, 0, &cbdate);

    rc = SQLExecute(hstmt);
```

#### <a name="plaintext-data-retrieval-example"></a>プレーン テキスト データの取得の例

次の例は、暗号化された値に基づいてデータをフィルター処理し、暗号化された列からプレーンテキスト データを取得する方法を示しています。 次のことを考慮してください。

- SSN 列に対してフィルター処理する WHERE 句が必要で渡される場合は、SQLBindParameter を使用して、ドライバーを透過的に暗号化をサーバーに送信する前にできるようにするために使用する値。

- ドライバーは、SSN 列と BirthDate 列から取得されたデータを透過的に暗号化解除のため、プログラムによって印刷されるすべての値は、プレーン テキストになります。

> [!NOTE]
> クエリは、暗号化は明確な場合にのみ、暗号化された列に対して等価比較を実行できます。 詳細については、次を参照してください。[を選択すると決定性またはランダム化された暗号化](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption)です。

```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[SSN] = ? ";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//SSN
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="ciphertext-data-retrieval-example"></a>暗号化テキスト データの取得の例

Always Encrypted が有効になっていない場合でも、暗号化された列をターゲットとするパラメーターがクエリになければ、クエリでは、暗号化された列からデータを取得できます。

次の例では、暗号化された列から暗号化されたバイナリ データの取得を示します。 次のことを考慮してください。

- 接続文字列で Always Encrypted が有効になっていないので、クエリは、SSN と BirthDate の暗号化された値をバイト配列として返します (プログラムによって値が文字列に変換されます)。
- Always Encrypted が無効の状態で、暗号化された列からデータを取得するクエリは、暗号化された列をターゲットとするパラメーターがない場合に限り、パラメーターを含むことができます。 上記のクエリは、データベースで暗号化されない LastName によってフィルター処理を行います。 クエリが SSN または BirthDate によってフィルター処理を行った場合、クエリは失敗します。


```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[LastName] = ?";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//LastName
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>暗号化された列をクエリする際の一般的な問題を回避する

このセクションでは、ODBC アプリケーションおよびそれを回避する方法のガイドラインをいくつかの暗号化された列を照会するときに、エラーの一般的なカテゴリがについて説明します。

##### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型の変換エラー

Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 参照してください[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)サポートされる型変換の詳細な一覧についてはします。 データ型変換エラーを回避するのには、SQLBindParameter を暗号化された列をターゲットとするパラメーターを使用すると、次の点を確認することを確認します。

- SQL の型パラメーターがか正確に対象の列の型と同じまたは SQL 型から列の型への変換はサポートされています。

- 有効桁数と小数点以下桁数の列をターゲットとするパラメーター、`decimal`と`numeric`有効桁数と小数点以下桁数が、ターゲット列に対して構成されていると同じ SQL Server データ型であります。

- 列をターゲットとするパラメーターの有効桁数`datetime2`、 `datetimeoffset`、または`time`SQL Server データ型は、対象列を変更するクエリ内のターゲット列の有効桁数より大きい値ではありません。  

##### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値の代わりにプレーンテキストを渡すことによるエラー

暗号化された列を対象とする任意の値は、サーバーに送信される前に暗号化する必要があります。 挿入、しようとすると、変更、または暗号化された列でプレーン テキスト値でフィルター処理、エラーが発生します。 このようなエラーを防ぐためには、ことを確認します。

- Always Encrypted が有効に (DSN、接続文字列の前に、接続を設定して、`SQL_COPT_SS_COLUMN_ENCRYPTION`特定の接続の接続属性、または`SQL_SOPT_SS_COLUMN_ENCRYPTION`特定のステートメントのステートメント属性)。

- SQLBindParameter を使用して、暗号化された列をターゲットとするデータを送信します。 次の例では、不正なフィルター処理、暗号化された列 (SSN) でリテラル/定数によって SQLBindParameter に引数としてリテラルを渡す代わりに、クエリを示します。

```
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

### <a name="precautions-when-using-sqlsetpos-and-sqlmoreresults"></a>SQLSetPos と SQLMoreResults を使用するときの注意事項

#### <a name="sqlsetpos"></a>SQLSetPos

`SQLSetPos` API により、バッファー SQLBindCol にバインドされていると、どの行にデータのフェッチ以前を使用して結果セット内の行を更新するアプリケーション。 暗号化された固定長の型の非対称パディング動作によるものが予期せず、行の他の列での更新プログラムの実行中にこれらの列のデータを変更することができます。 AE の値が、バッファーのサイズより小さい場合に固定長文字の値が埋め込まれます。

この問題を軽減するには、使用、`SQL_COLUMN_IGNORE`フラグの一部として更新されません列を無視する`SQLBulkOperations`を使用する場合と`SQLSetPos`カーソル ベースの更新プログラム。  アプリケーションによっては、直接変更されないすべての列を無視するか、両方のパフォーマンス低下したり、バッファーにバインドされている列の切り捨てを避けるため*小さい*(DB) の実際のサイズよりもします。 詳細については、次を参照してください。 [SQLSetPos 関数リファレンス](https://msdn.microsoft.com/library/ms713507(v=vs.85).aspx)です。

#### <a name="sqlmoreresults--sqldescribecol"></a>SQLMoreResults & SQLDescribeCol

アプリケーションを呼び出すことが[SQLDescribeCol](https://msdn.microsoft.com/library/ms716289(v=vs.85).aspx)準備されたステートメントの列に関するメタデータを返すようにします。  Always Encrypted が有効になっているときに呼び出す`SQLMoreResults`*する前に*呼び出す`SQLDescribeCol`により[sp_describe_first_result_set](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)呼び出される、正しく返さないプレーン テキスト暗号化された列のメタデータ。 この問題を避けるためには、呼び出す`SQLDescribeCol`準備されたステートメントで*する前に*呼び出す`SQLMoreResults`です。

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスに与える影響の制御

常に暗号化がクライアント側暗号化テクノロジであるため、データベースではなく、クライアント側でほとんどのパフォーマンスのオーバーヘッドが発生します。 暗号化および暗号化解除の操作のコストとは別のパフォーマンスのオーバーヘッドがクライアント側の他の原因を示します。

- クエリ パラメーターのメタデータを取得するためのデータベースへの追加のラウンド トリップ。

- 列マスター キーにアクセスするための列マスター キー ストアの呼び出し。

このセクションでは、SQL Server とのパフォーマンスに上記の 2 つの要因の影響を制御する方法の ODBC Driver 13.1 で組み込みのパフォーマンスの最適化について説明します。

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>メタデータを取得するクエリ パラメーターのラウンド トリップを制御します。

接続に対して Always Encrypted が有効になっている場合、ODBC Driver 13.1 SQL Server が、既定では、呼び出す[sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)パラメーター化各クエリの渡す (パラメーターを指定しないで、クエリ ステートメントSQL Server には値)。 このストアド プロシージャを調べる場合は、すべてのパラメーターを暗号化する必要がある場合に、クエリ ステートメントを分析し、それらを暗号化するドライバーを許可するには、各パラメーターの暗号化に関連する情報を返します。 上記の動作により、クライアント アプリケーションへの透過性の高度な: アプリケーション (およびアプリケーション開発者) は暗号化された列をターゲットとする値が渡される限り、暗号化された列にアクセスするクエリについて注意する必要ありませんドライバーのパラメーターにします。

### <a name="per-statement-always-encrypted-behavior"></a>ステートメントごとの動作を常に暗号化します。

パラメーター化クエリに対して暗号化メタデータを取得する操作のパフォーマンスに与える影響を制御するには、接続で有効になっている場合、個々 のクエリの Always Encrypted の動作を変更できます。 このようにすることを確認`sys.sp_describe_parameter_encryption`クエリがわかっている暗号化された列をターゲットとするパラメーターがあるためだけに呼び出すことができます。 ただし、これにより、暗号化の透明性を削減すること。 データベースに追加の列を暗号化する場合は、スキーマの変更を配置するアプリケーションのコードを変更するたい場合があります。

ステートメントの Always Encrypted の動作を制御するに呼び出しを設定する SQLSetStmtAttr、`SQL_SOPT_SS_COLUMN_ENCRYPTION`ステートメント属性を次の値のいずれか。

|値|Description|
|-|-|
|`SQL_CE_DISABLED` (0)|ステートメントの暗号化が常に無効になっています|
|`SQL_CE_RESULTSETONLY` (1)|復号化だけです。 結果セットと戻り値が復号化、およびパラメーターが暗号化されていません|
|`SQL_CE_ENABLED` (3) | 暗号化が常に有効になっており、パラメーターと結果の両方に使用|

Always Encrypted との接続から作成された新しいステートメント ハンドルでは、SQL_CE_ENABLED の既定値は有効になります。 使用して接続から作成された無効 SQL_CE_DISABLED に既定値 (およびそれらで Always Encrypted を有効にすることはできません。)

ほとんどのクライアント アプリケーションのクエリは、暗号化された列にアクセスする場合は、以下が推奨されます。

- 設定、`ColumnEncryption`接続文字列キーワードを`Enabled`です。

- 設定、`SQL_SOPT_SS_COLUMN_ENCRYPTION`属性を`SQL_CE_DISABLED`ステートメントで暗号化された列にアクセスしないが上です。 両方の呼び出しを無効にするにはこの`sys.sp_describe_parameter_encryption`結果の値を暗号化解除しようと設定します。
    
- 設定、`SQL_SOPT_SS_COLUMN_ENCRYPTION`属性を`SQL_CE_RESULTSETONLY`暗号化を必要とするすべてのパラメーターはありませんが、暗号化された列からデータを取得するステートメントにします。 呼び出し元が無効にするにはこの`sys.sp_describe_parameter_encryption`と、パラメーター暗号化します。 暗号化を解除する暗号化された列を含む結果が続行されます。

## <a name="always-encrypted-security-settings"></a>セキュリティの設定は常に暗号化

### <a name="force-column-encryption"></a>列の暗号化

パラメーターの暗号化を強制するのには、設定、 `SQL_CA_SS_FORCE_ENCRYPT` SQLSetDescField 関数を呼び出すことによって実装パラメーター記述子 (IPD) のフィールドです。 0 以外の値が原因ドライバー時に返されるエラーに関連付けられているパラメーター暗号化メタデータは返されません。

```
SQLHDESC ipd;
SQLGetStmtAttr(hStmt, SQL_ATTR_IMP_PARAM_DESC, &ipd, 0, 0);
SQLSetDescField(ipd, paramNum, SQL_CA_SS_FORCE_ENCRYPT, (SQLPOINTER)TRUE, SQL_IS_SMALLINT);   
```

SQL Server では、パラメーターを暗号化する必要はありません、ドライバーに通知、そのパラメーターを使用するクエリは失敗します。 これにより、侵害された SQL server が、クライアントは、データの漏えいにつながる可能性がありますを不正な暗号化メタデータを提供するセキュリティ攻撃に対する保護を強化できます。

### <a name="column-encryption-key-caching"></a>列暗号化キーのキャッシュ

列暗号化キーの暗号化を解除するための列マスター キー ストアへの呼び出しの数を減らすためには、ドライバーは、メモリ内でプレーン テキスト Cek をキャッシュします。 受信したらを使用して ECEK データベース メタデータから、ドライバーは、まず、キャッシュ内で暗号化されたキーの値に対応するプレーン テキスト CEK を検索を試みます。 ドライバーは、キャッシュに対応するプレーン テキスト CEK を見つけられない場合にのみ、CMK を含むキー ストアを呼び出します。

> [!NOTE]
> SQL Server 用 ODBC Driver 13.1、キャッシュ内のエントリが 2 時間のタイムアウト後に削除されます。 つまり、特定の使用して ECEK のドライバーは、2 時間ごと、またはアプリケーションの有効期間中に 1 回だけキー ストアを取引先担当者、か小さい方です。

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアを操作する

暗号化と、データを暗号化解除、ドライバーは、ターゲット列に対して構成されている、CEK を取得する必要があります。 Cek は、暗号化された形式 (ECEKs) で、データベースのメタデータに格納されます。 各 CEK には、暗号化に使用された対応する CMK があります。 [データベース メタデータ](../../t-sql/statements/create-column-master-key-transact-sql.md)CMK 自体は格納されません、キーストアとキーストアを使用して CMK を検索する情報の名前にはのみが含まれます。

使用して ECEK のプレーン テキスト値を取得するドライバー最初取得 CEK とその対応する CMK の両方に関するメタデータしこの情報を使用して、CMK を含むキーストアを連絡しを使用して ECEK の暗号化を解除することを要求します。 ドライバーは、キー ストア プロバイダーを使用してキー ストアと通信します。

### <a name="built-in-keystore-providers"></a>組み込みキー ストア プロバイダー

SQL Server 用 ODBC Driver 13.1 は、次の組み込みキー ストア プロバイダーが付属します。

| 名前 | Description | プロバイダー (メタデータ) の名前 |可用性|
|:---|:---|:---|:---|
|Azure Key Vault |Azure Key Vault でのストアの Cmk | `AZURE_KEY_VAULT` |Windows、Linux、macOS|
|Windows 証明書ストア|キーストアを Windows に Cmk をローカルに格納します。| `MSSQL_CERTIFICATE_STORE`|Windows|

- (または、DBA) 列マスター_キーのメタデータで構成されているプロバイダー名が正しいこと、および列マスター_キーのパスが指定されたプロバイダーのキー パスの形式に準拠しているかどうかを確認する必要があります。 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md) ステートメントを発行した際に有効なプロバイダー名とキー パスを自動的に生成する、SQL Server Management Studio などのツールを使用してキーを構成することをお勧めします。

- アプリケーションは、キー ストア内のキーにアクセスできるようにする必要があります。 アプリケーションのキーや、キーストアに応じて、キーストアへのアクセスを許可またはその他のキー ストア固有の構成手順を実行する可能性があります。 たとえば、Azure Key Vault にアクセスするにキー ストアへの正しい資格情報を提供する必要があります。

### <a name="using-the-azure-key-vault-provider"></a>Azure Key Vault Provider を使用します。

Azure Key Vault は、特にアプリケーションが Azure でホストされている場合、Always Encrypted の列マスター キーの格納と管理に便利なオプションです。 Linux、macOS、および Windows 上の SQL Server 用 ODBC Driver 13.1 には、Azure Key Vault の組み込み列マスター キー ストア プロバイダーが含まれています。 参照してください[Azure Key Vault – ステップ バイ ステップ](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/)、 [Key Vault の使用を開始する](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)、および[Azure Key Vault で列マスター_キーの作成](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2)Azure キーを構成する方法について資格情報コンテナーの Always Encrypted のです。

ドライバーは、次の資格情報の種類を使用して Azure Key Vault への認証をサポートします。

- ユーザー名/パスワード – この方法では、資格情報は、Azure Active Directory ユーザーとそのパスワードの名前。

- このメソッドにより、クライアント ID とシークレット – 資格情報は、アプリケーション クライアント ID とアプリケーション シークレットがします。

列の暗号化の AKV に格納されている Cmk を使用するドライバーを許可するのには、次の接続文字列専用のキーワードを使用します。

|[資格情報の種類]| `KeyStoreAuthentication` |`KeyStorePrincipalId`| `KeyStoreSecret` |
|-|-|-|-|
|ユーザー名/パスワード| `KeyVaultPassword`|ユーザー プリンシパル名|Password|
|クライアント ID とシークレット| `KeyVaultClientSecret`|クライアント ID|シークレット|

#### <a name="example-connection-strings"></a>接続文字列の例

次の接続文字列は、次の 2 つの資格情報の種類を Azure Key Vault に認証する方法を示します。

**ClientID/シークレット**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultClientSecret;KeyStorePrincipalId=<clientId>;KeyStoreSecret=<secret>
```

**ユーザー名/パスワード**

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultPassword;KeyStorePrincipalId=<username>;KeyStoreSecret=<password>
```

AKV CMK 記憶域を使用するその他の ODBC アプリケーションの変更は必要ありません。

### <a name="using-the-windows-certificate-store-provider"></a>Windows 証明書ストアのプロバイダーを使用します。

Windows 上の SQL Server 用 ODBC Driver 13.1 には、Windows 証明書ストア、という名前の組み込み列マスター キー ストア プロバイダーが含まれています。`MSSQL_CERTIFICATE_STORE`です。 (このプロバイダーは macOS または Linux で使用できません) です。このプロバイダーと、クライアント コンピューターに CMK をローカルに格納されてし、アプリケーションによって追加の構成は、ドライバーで使用する必要はありません。 ただし、アプリケーションでは、ストアに証明書とその秘密キーへのアクセスが必要です。 参照してください[(Always Encrypted) ストア列のマスター_キーの作成と](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted)詳細についてはします。

### <a name="using-custom-keystore-providers"></a>カスタム キー ストア プロバイダーを使用します。

SQL Server 用 ODBC Driver 13.1 CEKeystoreProvider インターフェイスを使用して、サード パーティのカスタム キー ストア プロバイダーがサポートされます。 これにより、アプリケーションを読み込むには、クエリ、および暗号化された列にアクセスする、ドライバーで使用できるようにする、キー ストア プロバイダーを構成します。 アプリケーションが SQL Server でストレージの Cek を暗号化および ODBC; の暗号化された列へのアクセスを超えるタスクを実行するために、キー ストア プロバイダーと連携する可能性も直接詳細については、次を参照してください。[カスタム キー ストア プロバイダー](../../connect/odbc/custom-keystore-providers.md)です。

2 つの接続属性は、カスタム キー ストア プロバイダーとの対話に使用されます。 これらは次のとおりです。

- `SQL_COPT_SS_CEKEYSTOREPROVIDER`

- `SQL_COPT_SS_CEKEYSTOREDATA`

前者は読み込みおよび後者によりアプリケーション プロバイダーの通信中に読み込まれたキー ストア プロバイダーを列挙に使用されます。 これらの接続属性は、前に、またはアプリケーション プロバイダーの操作では、SQL Server との通信を含まないため、接続を確立した後、いつでも使用できます。 ただし、ドライバーはまだ読み込まれていない、ため設定と接続する前にこれらの属性を取得は、ドライバー マネージャーによって処理することによりし、期待どおりの結果がもたらすされます。

#### <a name="loading-a-keystore-provider"></a>キー ストア プロバイダーの読み込み

設定、`SQL_COPT_SS_CEKEYSTOREPROVIDER`接続属性をそれに含まれるキー ストア プロバイダーを使用してを利用できるように、プロバイダー ライブラリを読み込むクライアント アプリケーションを有効にします。

```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```
| 引数 | Description |
|:---|:---|
|`ConnectionHandle`|[入力]接続ハンドルです。 有効な接続ハンドルをする必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから、同じプロセス内の他のアクセス。|
|`Attribute`|[入力]設定する属性を:`SQL_COPT_SS_CEKEYSTOREPROVIDER`定数。|
|`ValuePtr`|[入力]プロバイダー ライブラリのファイル名を指定する文字の null で終わる文字列へのポインター。 SQLSetConnectAttrA、これは ANSI (マルチバイト) 文字列です。 SQLSetConnectAttrW、これは Unicode (wchar_t) 文字列です。|
|`StringLength`|[入力]ValuePtr 文字列、または SQL_NTS の長さ。|

ドライバーが、プラットフォーム定義ダイナミック ライブラリ読み込みメカニズムを使用して、ValuePtr パラメーターによって識別される、ライブラリを読み込もうと (`dlopen()` Linux と macOS、 `LoadLibrary()` on Windows) の一覧にその中に定義されているすべてのプロバイダーを追加プロバイダーがドライバーに呼ばれます。 次のエラーが発生する可能性があります。

| [エラー] | Description |
|:--|:--|
|`CE203`|動的なライブラリを読み込むことができませんでした。|
|`CE203`|ライブラリに"CEKeyStoreProvider"エクスポート シンボルが見つかりませんでした。|
|`CE203`|1 つまたは複数のプロバイダー ライブラリに既に読み込まれています。|

`SQLSetConnectAttr`通常のエラーまたは成功を示す値、および追加情報は、の標準の ODBC 診断メカニズムによって発生したエラーを返します。

> [!NOTE]
> アプリケーション プログラマは、それらを必要とする任意のクエリがすべて接続経由で送信される前に、カスタム プロバイダーが読み込まれたであることを確認する必要があります。 これを行うには、失敗した場合は、エラーが発生されます。

| [エラー] | Description |
|:--|:--|
|`CE200`|キー ストア プロバイダー %1 は見つかりませんでした。 適切なキー ストア プロバイダー ライブラリが読み込まれたことを確認します。|

> [!NOTE]
> キー ストア プロバイダー実装の使用は避けてください`MSSQL`カスタム プロバイダーの名前。 この用語は、Microsoft 専用として予約されていると、将来の組み込みプロバイダーに競合が発生する可能性があります。 カスタム プロバイダーの名前には、この用語を使用すると、ODBC 警告可能性があります。

#### <a name="getting-the-list-of-loaded-providers"></a>読み込まれているプロバイダーの一覧を取得します。

(を含む組み込まれている) ドライバーで現在読み込まれているキー ストア プロバイダーを確認するクライアント アプリケーションにより、この接続属性を取得します。これは、接続した後のみ実行できます。

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```
| 引数 | Description |
|:---|:---|
|`ConnectionHandle`|[入力]接続ハンドルです。 有効な接続ハンドルをする必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから、同じプロセス内の他のアクセス。|
|`Attribute`|[入力]取得する属性:`SQL_COPT_SS_CEKEYSTOREPROVIDER`定数。|
|`ValuePtr`|[出力][次へ] のロード プロバイダー名を返すメモリへのポインター。|
|`BufferLength`|[入力]ValuePtr バッファーの長さ。|
|`StringLengthPtr`|[出力]合計バイト数 (null 終了文字を除く) を返すバッファーへのポインターで返される使用可能な\*ValuePtr です。 ValuePtr が null ポインターの場合は、長さは返されません。 属性値、文字の文字列であり、使用できるバイト数を返す null 終了の長さマイナス BufferLength より大きい場合は、文字、内のデータ\*ValuePtr の長さマイナス BufferLength に切り捨てられます、null 終端文字は、ドライバーが null で終わるとします。|

全体の一覧の取得を許可するのには、すべての Get 操作は、現在のプロバイダーの名前を返し、次のいずれかを内部カウンターをインクリメントします。 このカウンターに到達すると、リストでは、空の文字列の末尾 ("") が返されるとカウンターはリセットされます。後続の Get 操作は、リストの先頭からもう一度行われ、

### <a name="communicating-with-keystore-providers"></a>キー ストア プロバイダーとの通信

`SQL_COPT_SS_CEKEYSTOREDATA`接続属性キー マテリアルなどの更新、追加のパラメーターを構成するために読み込まれたキーストア プロバイダーと通信するクライアント アプリケーションを有効にします。Get に基づく、単純な要求-応答プロトコルに依存して、クライアント アプリケーションとプロバイダー間の通信とセットは、この接続属性の使用を要求します。 通信は、クライアント アプリケーションでのみ開始されます。

> [!NOTE]
> ODBC の性質の ODBC インターフェイスのみで、接続のコンテキストの解像度でデータを設定 (SQLGet/SetConnectAttr) に CEKeyStoreProvider の応答を呼び出します。

アプリケーションは、CEKeystoreData 構造体を使用してドライバーを介してキー ストア プロバイダーと通信します。

```
typedef struct CEKeystoreData {
wchar_t *name;
unsigned int dataSize;
char data[];
} CEKEYSTOREDATA;
```
| 引数 | Description |
|:---|:---|
|`name`|[入力]セット、プロバイダーの名前に、データが送信されます。 取得時に無視されます。 Null で終わる、ワイド文字列です。|
|`dataSize`|[入力]次の構造データの配列のサイズ。|
|`data`|[InOut]によってセットは、プロバイダーに送信されるデータ。 任意のデータがあります。ドライバーは、これを解釈しようを行いません。 Get、時に、プロバイダーからデータを受け取るバッファーを読み取る。|

#### <a name="writing-data-to-a-provider"></a>プロバイダーにデータを書き込む

A`SQLSetConnectAttr`呼び出しを使用して、`SQL_COPT_SS_CEKEYSTOREDATA`属性が指定したキー ストア プロバイダーを「パケット」形式のデータを書き込みます。
```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```
| 引数 | Description |
|:---|:---|
|`ConnectionHandle`| [入力]接続ハンドルです。 有効な接続ハンドルをする必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから、同じプロセス内の他のアクセス。|
|`Attribute`|[入力]設定する属性を:`SQL_COPT_SS_CEKEYSTOREDATA`定数。|
|`ValuePtr`|[入力]CEKeystoreData 構造体へのポインター。 構造体の名前 フィールドでは、データが対象とするプロバイダーを識別します。|
|`StringLength`|[入力]SQL_IS_POINTER 定数|

追加の詳細なエラー情報を使用して取得できる[SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx)です。

> [!NOTE]
> プロバイダーはこれがご希望の場合に特定の接続に書き込まれたデータを関連付けるには、接続ハンドルを使用できます。 これは、接続ごとの構成を実装するために役立ちます。 接続コンテキストを無視し、データを送信するための接続に関係なく同じデータを扱うその可能性がありますもします。 参照してください[コンテキスト関連付け](../../connect/odbc/custom-keystore-providers.md#context-association)詳細についてはします。

#### <a name="reading-data-from-a-provider"></a>プロバイダーからデータを読み込む

呼び出し`SQLGetConnectAttr`を使用して、`SQL_COPT_SS_CEKEYSTOREDATA`属性が「パケット」からのデータを読み取ります*、最後の書き込み先*プロバイダー。 [なし] が、関数のシーケンス エラーが発生します。 キー ストア プロバイダーの実装側は、これを行うが合理的である場合、他の副作用を発生させることがなく読み取り操作のため、プロバイダーを選択した場合の方法として 0 バイトの「ダミー書き込みます」をサポートすることをお勧めします。

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```
| 引数 | Description |
|:---|:---|
|`ConnectionHandle`|[入力]接続ハンドルです。 有効な接続ハンドルをする必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから、同じプロセス内の他のアクセス。|
|`Attribute`|[入力]取得する属性:`SQL_COPT_SS_CEKEYSTOREDATA`定数。|
|`ValuePtr`|[出力]プロバイダーから読み取られるデータが置かれている CEKeystoreData 構造体へのポインター。|
|`BufferLength`|[入力]SQL_IS_POINTER 定数|
|`StringLengthPtr`|[出力]返す BufferLength バッファーへのポインター。 場合 * ValuePtr が null ポインターの長さは返されません。|

呼び出し元では、十分な長さが次の CEKEYSTOREDATA 構造体のバッファーに書き込むために、プロバイダーに割り当てられていることを確認してください。 関数が戻るとき、その dataSize フィールドは、プロバイダーから読み取られるデータの実際の長さで更新されます。 追加の詳細なエラー情報を使用して取得できる[SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx)です。

このインターフェイスには、アプリケーションとキー ストア プロバイダーの間で転送されるデータの形式で追加の要件配置ありません。 各プロバイダーは、必要に応じて、独自のプロトコル/データ形式を定義できます。

キー ストア プロバイダーの実装の例は、次を参照してください[カスタム キー ストア プロバイダー。](../../connect/odbc/custom-keystore-providers.md)

## <a name="limitations-of-the-odbc-driver-when-using-always-encrypted"></a>Always Encrypted を使用する場合は、ODBC ドライバーの制限事項

### <a name="bulk-copy-function-usage"></a>一括コピー関数の使用法
使用、 [SQL 一括コピー関数](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)Always Encrypted で ODBC ドライバーを使用する場合はサポートされていません。 SQL 一括コピー関数で使用される暗号化された列に対して透過的な暗号化/暗号化解除は行われません。

### <a name="asynchronous-operations"></a>非同期操作
ODBC ドライバーの使用を許可中に[非同期操作](../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)Always encrypted によりは、パフォーマンスに影響操作で Always Encrypted が有効にするとします。 呼び出し`sys.sp_describe_parameter_encryption`、ステートメントがブロックしているとすると、サーバーを返す前に、メタデータを返すまで待機するドライバーを暗号化メタデータを決定する`SQL_STILL_EXECUTING`です。

## <a name="always-encrypted-api-summary"></a>Always Encrypted の API の概要

### <a name="connection-string-keywords"></a>接続文字列キーワード

|名前|Description|  
|----------|-----------------|  
|`ColumnEncryption`|指定できる値は`Enabled` /`Disabled`です。<br>`Enabled`-接続に対して Always Encrypted 機能を有効にします。<br>`Disabled`-接続に対して Always Encrypted 機能を無効にします。 <br><br>既定値は `Disabled` です。|  
|`KeyStoreAuthentication` | 有効な値: `KeyVaultPassword`、`KeyVaultClientSecret` |
|`KeyStorePrincipalId` | ときに`KeyStoreAuthentication`  =  `KeyVaultPassword`、有効な Azure Active Directory ユーザー プリンシパル名にこの値を設定します。 <br>ときに`KeyStoreAuthetication`  =  `KeyVaultClientSecret`有効な Azure Active Directory アプリケーション クライアント ID に設定する値 |
|`KeyStoreSecret` | ときに`KeyStoreAuthentication`  =  `KeyVaultPassword`対応するユーザー名のパスワードにこの値を設定します。 <br>ときに`KeyStoreAuthentication`  =  `KeyVaultClientSecret`有効な Azure Active Directory アプリケーション クライアント ID に関連付けられたアプリケーション シークレットにこの値を設定|

### <a name="connection-attributes"></a>接続属性

|名前|型|Description|  
|----------|-------|----------|  
|`SQL_COPT_SS_COLUMN_ENCRYPTION`|接続前|`SQL_COLUMN_ENCRYPTION_DISABLE`(0)--Always Encrypted を無効にします。 <br>`SQL_COLUMN_ENCRYPTION_ENABLE`(1) - Always Encrypted を有効にします。|
|`SQL_COPT_SS_CEKEYSTOREPROVIDER`|接続後|[設定]CEKeystoreProvider をロードしようとしてください。<br>[取得]CEKeystoreProvider 名を返す|
|`SQL_COPT_SS_CEKEYSTOREDATA`|接続後|[設定]CEKeystoreProvider にデータを書き込む<br>[取得]CEKeystoreProvider からデータを読み取る|

### <a name="statement-attributes"></a>ステートメント属性

|名前|Description|  
|----------|-----------------|  
|`SQL_SOPT_SS_COLUMN_ENCRYPTION`|`SQL_CE_DISABLED`(0)--ステートメントの always Encrypted が無効になっています <br>`SQL_CE_RESULTSETONLY`(1)--のみ復号化します。 結果セットと戻り値が復号化、およびパラメーターが暗号化されていません <br>`SQL_CE_ENABLED`(3)--always Encrypted が有効になっており、パラメーターと結果の両方の使用|

### <a name="descriptor-fields"></a>記述子フィールド

|IPD フィールド|サイズ/型|既定値|Description|
|-|-|-|-|  
|`SQL_CA_SS_FORCE_ENCRYPT` (1236)|WORD (2 バイト)|0|ときに 0 (既定): このパラメーターを暗号化するかどうかは暗号化メタデータの可用性によって決定されます。<br><br>0 以外の場合: 暗号化メタデータがこのパラメーターに使用できる場合は、暗号化されています。 エラー [CE300] で、要求が失敗するそれ以外の場合、[Microsoft] [ODBC Driver 13 for SQL Server] の必須の暗号化では、パラメーターが指定されましたが、サーバーによって暗号化メタデータが指定されていません。|

## <a name="see-also"></a>参照

- [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Always Encrypted 関連のブログ](http://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)


