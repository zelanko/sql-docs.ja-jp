---
title: SQL Server 用 ODBC ドライバーと共に Always Encrypted を使用する | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2018
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02e306b8-9dde-4846-8d64-c528e2ffe479
ms.author: v-chojas
manager: craigg
author: MightyPen
ms.openlocfilehash: dfe1777044234ec43c13f738fa1b0de896f96616
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828270"
---
# <a name="using-always-encrypted-with-the-odbc-driver-for-sql-server"></a>SQL Server 用 ODBC ドライバーと共に Always Encrypted を使用する
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

### <a name="applicable-to"></a>適用対象

- ODBC Driver 13.1 for SQL Server
- ODBC Driver 17 for SQL Server

### <a name="introduction"></a>概要

この記事では、情報を使用する ODBC アプリケーションを開発する方法には[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)します。

Always Encrypted を使用すると、クライアント アプリケーションは SQL Server または Azure SQL データベースにデータまたは暗号化キーを開示することなく、機密データを暗号化することができます。 ODBC Driver for SQL Server など、Always Encrypted が有効なドライバーは、クライアント アプリケーション内の機密データを透過的に暗号化および暗号化解除することで、この処理を実行します。 ドライバーは、どのクエリ パラメーターが機密データベース列 (Always Encrypted を使用して保護される) に対応するかを自動的に決定し、SQL Server または Azure SQL データベースにデータを渡す前にこれらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、「 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。

### <a name="prerequisites"></a>Prerequisites

データベースで Always Encrypted を構成します。 この処理には、Always Encrypted キーのプロビジョニング、および選択したデータベース列の暗号化の設定が含まれます。 Always Encrypted が構成されたデータベースがない場合は、「 [Always Encrypted の作業の開始](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted)」の手順に従います。 具体的には、データベースでは、列マスター_キー (CMK)、列暗号化キー (CEK)、およびその CEK を使用して暗号化された 1 つまたは複数の列を含むテーブルのメタデータ定義を含める必要があります。

### <a name="enabling-always-encrypted-in-an-odbc-application"></a>ODBC アプリケーションで Always Encrypted を有効にします。

パラメーターの暗号化と暗号化の結果セット列の暗号化解除の両方を有効にする最も簡単な方法は、の値を設定して、`ColumnEncryption`接続文字列キーワードを**有効**します。 Always Encrypted を有効にする接続文字列の例を次に示します。

```
SQLWCHAR *connString = L"Driver={ODBC Driver 13 for SQL Server};Server={myServer};Trusted_Connection=yes;ColumnEncryption=Enabled;";
```

常に暗号化された可能性がありますもまたは有効に DSN の構成で同じキーと値 (存在する場合は、接続文字列の設定によって上書きされます) を使用してプログラムで、`SQL_COPT_SS_COLUMN_ENCRYPTION`接続前の属性。 この方法を設定することには、接続文字列または DSN に設定された値よりも優先されます。

```
 SQLSetConnectAttr(hdbc, SQL_COPT_SS_COLUMN_ENCRYPTION, (SQLPOINTER)SQL_COLUMN_ENCRYPTION_ENABLE, 0);
```

接続を有効にすると、個々 のクエリの Always Encrypted の動作を調整することがあります。 参照してください[、パフォーマンスへの影響の Always Encrypted を制御する](#controlling-the-performance-impact-of-always-encrypted)以下の詳細についてはします。

Always Encrypted の有効化が不十分である暗号化または暗号化解除を成功させるために注意してください。また、ことを確認する必要があります。

- アプリケーションが、データベース内の Always Encrypted キーに関するメタデータへのアクセスに必要な *VIEW ANY COLUMN MASTER KEY DEFINITION* および *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* データベース権限を持っている。 詳細については、次を参照してください。[データベース権限](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions)します。

- アプリケーションは、クエリ対象の暗号化された列の Cek を保護するための CMK にアクセスできます。 これは、CMK を格納するキーストア プロバイダーに依存します。 参照してください[列マスター キー ストアの操作](#working-with-column-master-key-stores)詳細についてはします。

### <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>暗号化された列のデータを取得および変更する

接続で Always Encrypted を有効すると、標準の ODBC Api を使用することができます (を参照してください[ODBC サンプル コード](https://code.msdn.microsoft.com/windowsapps/ODBC-sample-191624ae/sourcecode?fileId=51137&pathId=1980325953)または[ODBC プログラマ リファレンス](https://msdn.microsoft.com/library/ms714177(v=vs.85).aspx)) を取得または暗号化されたデータベース列のデータを変更します。 データベース権限と、列マスター _ キーにアクセスできる、ドライバーは暗号化された列をターゲットし、する動作に透過的に暗号化された列から取得されたデータを復号化するすべてのクエリ パラメーターを暗号化に必要なアプリケーションがある場合、列が暗号化されていない場合、アプリケーション。

Always Encrypted が有効でない場合、暗号化された列をターゲットとするパラメーターを含むクエリは失敗します。 暗号化された列をターゲットとするパラメーターがクエリにない場合は、暗号化された列からデータを取得できます。 ただし、ドライバーは、暗号化の解除を試行しませんし、アプリケーション (バイト配列) として暗号化されたバイナリ データが表示されます。

次の表は、Always Encrypted が有効かどうかに応じたクエリの動作をまとめたものです。

|クエリの特性 | Always Encrypted が有効になっており、アプリケーションがキーとキー メタデータにアクセスできる|Always Encrypted が有効になっており、アプリケーションがキーまたはキー メタデータにアクセスできない | Always Encrypted が無効になっている|
|:---|:---|:---|:---|
| 暗号化された列をターゲットとするパラメーター。 | パラメーター値は透過的に暗号化されます。 | [エラー] | [エラー]|
| 暗号化された列をターゲットとするパラメーターを含まない、暗号化された列からのデータの取得。| 暗号化された列の結果は透過的に暗号化解除されます。 アプリケーションでは、プレーン テキスト列の値を受け取ります。 | [エラー] | 暗号化された列の結果は暗号化解除されません。 アプリケーションは、暗号化された値をバイト配列として受け取ります。

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

- 暗号化された列を含め、データベース列に挿入された値は、バインドされたパラメーターとして渡されます (「[SQLBindParameter 関数](https://msdn.microsoft.com/library/ms710963(v=vs.85).aspx)」を参照してください)。 暗号化されていない列に値を送信する場合、パラメーターの使用は省略可能です (ただし、SQL インジェクションを防ぐのに役立つので、強くお勧めします) が、暗号化された列をターゲットとする値に対しては必須です。 SSN または BirthDate 列に挿入された値は、クエリ ステートメントに埋め込まれているリテラルとして渡された、ドライバーは、暗号化、またはそれ以外のクエリ内のリテラルの処理を試行しませんので、クエリは失敗します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。

- SSN 列に挿入されるパラメーターの SQL 型が、SQL_CHAR にマップするに設定されている、 **char** SQL Server データ型 (`rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);`)。 パラメーターの型が、SQL_WCHAR にマップするに設定されたかどうか**nchar**、Always Encrypted は nchar の暗号化された値から暗号化された char 値へのサーバー側の変換はサポートされていない、クエリは失敗します。 参照してください[ODBC プログラマ リファレンス - 付録 d: データ型](https://msdn.microsoft.com/library/ms713607.aspx)については、データ型マッピングします。

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

- SQLBindParameter を使用して SSN 列に対してフィルター処理するために WHERE 句で使用される値は、サーバーに送信する前にドライバーが透過的に暗号化できるように、パラメーターとして渡す必要があります。

- ドライバーが SSN 列と BirthDate 列から取得されたデータを透過的に暗号化解除するので、プログラムで出力される値はすべてプレーンテキストになります。

> [!NOTE]
> クエリは、暗号化は確定的な場合にのみ、暗号化された列に対して等価比較を実行できます。 詳細については、「[明確な暗号化またはランダム化された暗号化の選択](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption)」を参照してください。

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

次の例は、暗号化された列から暗号化されたバイナリ データを取得する方法を示しています。 次のことを考慮してください。

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

ここでは、暗号化された列を ODBC アプリケーションからクエリする際のエラーの一般的なカテゴリと、その対処方法に関するいくつかのガイドラインを示します。

##### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型の変換エラー

Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 サポートされている型の変換の詳細な一覧については、「[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。 データ型変換エラーを避けるためには、SQLBindParameter を暗号化された列をターゲットとするパラメーターを使用すると、次の点を確認することを確認します。

- SQL の型パラメーターがか正確に対象の列の型と同じまたは SQL 型から列の型への変換がサポートされています。

- `decimal` と `numeric` の SQL Server データ型の列をターゲットとするパラメーターの有効桁数と小数点以下桁数が、ターゲット列に対して構成された有効桁数と小数点と同じである。

- ターゲット列を変更するクエリで、`datetime2`、`datetimeoffset`、または `time` の SQL Server データ型の列をターゲットとするパラメーターの有効桁数が、ターゲット列の有効桁数以下である。  

##### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値の代わりにプレーンテキストを渡すことによるエラー

暗号化された列を対象とする任意の値は、サーバーに送信される前に暗号化する必要があります。 暗号化された列でプレーンテキスト値の挿入、変更、フィルター処理を行おうとすると、エラーになります。 このようなエラーを防ぐには、次のことを確認してください。

- Always Encrypted が有効に (DSN、接続文字列の前に、接続を設定して、`SQL_COPT_SS_COLUMN_ENCRYPTION`特定の接続の接続属性、または`SQL_SOPT_SS_COLUMN_ENCRYPTION`の特定のステートメントのステートメント属性)。

- SQLBindParameter を使用して、暗号化された列をターゲットとするデータを送信すること。 次の例は、SQLBindParameter に引数としてリテラルを渡す代わりに、暗号化された列 (SSN) でリテラル/定数によって不正なフィルター処理を行うクエリを示しています。

```
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

### <a name="precautions-when-using-sqlsetpos-and-sqlmoreresults"></a>SQLSetPos および SQLMoreResults を使用しているときの注意事項

#### <a name="sqlsetpos"></a>SQLSetPos

`SQLSetPos` API SQLBindCol にバインドされていると、どの行にデータのフェッチ以前のバッファーを使用して結果セット内の行を更新する、アプリケーションを使用できます。 暗号化された固定長型の非対称の埋め込みの動作、によるものが予期せず、行の他の列での更新プログラムの実行中にこれらの列のデータを変更することです。 AE の値が、バッファー サイズより小さい場合に固定長の文字の値が埋め込まれます。

この問題を軽減するには、使用、`SQL_COLUMN_IGNORE`フラグの一部として更新されません列を無視する`SQLBulkOperations`を使用する場合と`SQLSetPos`カーソル ベースの更新プログラム。  両方のパフォーマンスと、バッファーにバインドされている列の切り捨てを回避するために、アプリケーションによっては直接変更されないすべての列を無視する必要があります*小さい*(DB) の実際のサイズよりもします。 詳細については、次を参照してください。 [SQLSetPos 関数リファレンス](https://msdn.microsoft.com/library/ms713507(v=vs.85).aspx)します。

#### <a name="sqlmoreresults--sqldescribecol"></a>SQLMoreResults & SQLDescribeCol

アプリケーション プログラムを呼び出すことが[SQLDescribeCol](https://msdn.microsoft.com/library/ms716289(v=vs.85).aspx)を準備されたステートメントで列のメタデータを返します。  Always Encrypted が有効になっているときに呼び出す`SQLMoreResults`*する前に*呼び出す`SQLDescribeCol`により[sp_describe_first_result_set](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)呼び出される正しく返さないプレーン テキスト暗号化された列のメタデータ。 この問題を回避するには、呼び出す`SQLDescribeCol`準備されたステートメントで*する前に*呼び出す`SQLMoreResults`します。

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスの影響を制御する

Always Encrypted はクライアント側暗号化テクノロジであるため、ほとんどのパフォーマンス オーバーヘッドは、データベースではなくクライアント側で発生します。 暗号化および暗号化解除の操作のコストとは別に、クライアント側のパフォーマンス オーバーヘッドのその他の原因を次に示します。

- クエリ パラメーターのメタデータを取得するためのデータベースへの追加のラウンド トリップ。

- 列マスター キーにアクセスするための列マスター キー ストアの呼び出し。

このセクションでは、ODBC Driver for SQL Server の組み込みのパフォーマンス最適化、および上記の 2 つの要因によるパフォーマンスへの影響を制御する方法について説明します。

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>クエリ パラメーターのメタデータを取得するためのラウンド トリップを制御する

既定では、接続に対して Always Encrypted が有効になっている場合、ドライバーは、各パラメーター化クエリに対して [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) を呼び出し、クエリ ステートメント (パラメーター値を除く) を SQL Server に渡します。 このストアド プロシージャを調べる場合は、すべてのパラメーターを暗号化する必要がある場合、クエリ ステートメントを分析し、暗号化することができるように、各パラメーターの暗号化に関連する情報を返します。 上記の動作により、クライアント アプリケーションへの透過性の概要: アプリケーション (およびアプリケーション開発者) に暗号化された列をターゲットとする値が渡される限り、暗号化された列にアクセスするクエリを意識する必要はありませんパラメーターでドライバー。

### <a name="per-statement-always-encrypted-behavior"></a>ステートメントあたりの動作を常に暗号化します。

パラメーター化クエリの暗号化メタデータの取得のパフォーマンスに与える影響を制御するには、接続で有効な場合は、個々 のクエリに対して Always Encrypted の動作を変更できます。 これにより、行うことができます`sys.sp_describe_parameter_encryption`がわかっているクエリがある暗号化された列をターゲットとするパラメーターに対してのみが呼び出されます。 ただし、これにより、暗号化の透明度が損なわれることに注意してください。データベース内の別の列を暗号化する場合は、スキーマの変更に合わせてアプリケーション コードの変更が必要になる可能性があります。

ステートメントの Always Encrypted の動作を制御する設定 SQLSetStmtAttr を呼び出す、`SQL_SOPT_SS_COLUMN_ENCRYPTION`ステートメント属性値は次のいずれかを使用します。

|ReplTest1|[説明]|
|-|-|
|`SQL_CE_DISABLED` (0)|ステートメントの暗号化が常に無効になっています|
|`SQL_CE_RESULTSETONLY` (1)|暗号化解除のみです。 結果セットと戻り値は復号化、およびパラメーターが暗号化されていません。|
|`SQL_CE_ENABLED` (3) | 暗号化が常に有効になっており、パラメーターと結果の両方に使用|

Always Encrypted との接続から作成された新しいステートメント ハンドルには、SQL_CE_ENABLED に既定値が有効になります。 使用して接続から作成された SQL_CE_DISABLED に既定値を無効になります (およびに Always Encrypted を有効にすることはできません。)

ほとんどのクライアント アプリケーションのクエリは、暗号化された列にアクセスする場合、次を推奨します。

- `ColumnEncryption` 接続文字列キーワードを `Enabled` に設定します。

- 設定、`SQL_SOPT_SS_COLUMN_ENCRYPTION`属性を`SQL_CE_DISABLED`で暗号化された列にアクセスしないステートメント。 両方の呼び出しを無効にするにはこの`sys.sp_describe_parameter_encryption`結果の値を暗号化解除しようと設定します。
    
- 設定、`SQL_SOPT_SS_COLUMN_ENCRYPTION`属性を`SQL_CE_RESULTSETONLY`の暗号化を必要とする任意のパラメーターはありませんが、暗号化された列からデータを取得するステートメント。 呼び出し元が無効になりますこの`sys.sp_describe_parameter_encryption`とパラメーターの暗号化。 暗号化された列を含む結果は引き続き暗号化を解除します。

## <a name="always-encrypted-security-settings"></a>セキュリティの設定は常に暗号化

### <a name="force-column-encryption"></a>列の暗号化

パラメーターの暗号化を適用する設定、 `SQL_CA_SS_FORCE_ENCRYPT` SQLSetDescField 関数を呼び出すことによって実装パラメーター記述子 (IPD) のフィールドします。 0 以外の値により、関連付けられたパラメーターの暗号化メタデータは返されませんときにエラーが返されます。

```
SQLHDESC ipd;
SQLGetStmtAttr(hStmt, SQL_ATTR_IMP_PARAM_DESC, &ipd, 0, 0);
SQLSetDescField(ipd, paramNum, SQL_CA_SS_FORCE_ENCRYPT, (SQLPOINTER)TRUE, SQL_IS_SMALLINT);   
```

パラメーターの暗号化が不要であることが SQL Server からドライバーに通知された場合、このパラメーターを使用するクエリは失敗します。 攻撃を受けた SQL Server がクライアントに不正な暗号化メタデータを提供すると、データ漏えいが引き起こされる可能性がありますが、これにより、そのようなセキュリティ攻撃に対する保護を強化します。

### <a name="column-encryption-key-caching"></a>列暗号化キーのキャッシュ

列暗号化キーを復号化するための列マスター キー ストアへの呼び出しの数を減らすためには、ドライバーは、メモリ内でプレーン テキスト Cek をキャッシュします。 CEK キャッシュとは、ドライバーにグローバルであり、任意の 1 つの接続に関連付けられていません。 データベース メタデータから、ECEK を受信した後、ドライバーは、最初、キャッシュの暗号化されたキー値に対応するプレーン テキスト CEK を検索を試みます。 ドライバーは、キャッシュに対応するプレーン テキスト CEK を見つけられない場合にのみ、CMK を含むキー ストアを呼び出します。

> [!NOTE]
> ODBC Driver for SQL Server では、キャッシュ内のエントリが 2 時間のタイムアウト後に削除されます。 つまり、指定された ECEK の場合は、ドライバーが 2 時間ごと、またはアプリケーションの有効期間中に 1 回だけキー ストアを接続、か小さい方です。

SQL Server 用 ODBC ドライバーの 17.1 以降、CEK のキャッシュのタイムアウトを使って調整できる、`SQL_COPT_SS_CEKCACHETTL`接続属性は、キャッシュに残りますが、CEK の秒数を指定します。 キャッシュのグローバルな性質では、この属性は、ドライバーの有効な接続ハンドルのいずれかから調整できます。 ときに TTL を小さくと、キャッシュと、新しい ttl 値を超過する既存の Cek も削除されます。 0 の場合は、Cek はキャッシュされません。

### <a name="trusted-key-paths"></a>信頼されたキー パス

SQL Server 用 ODBC ドライバーの 17.1 以降、`SQL_COPT_SS_TRUSTEDCMKPATHS`接続属性は、要求は常に暗号化操作では、キーのパスで識別される、Cmk の指定されたリストのみを使用するアプリケーションを使用できます。 既定では、この属性は、null の場合、これは、ドライバーが任意のキーのパスを受け入れることを意味です。 この機能を使用する次のように設定します。`SQL_COPT_SS_TRUSTEDCMKPATHS`が許可されているキーのパスを一覧表示されます。 null で区切られた、null で終わるワイド文字列を指すようにします。 この属性によって示されるメモリはこのサーバーのメタデータで指定された CMK パスは大文字小文字、かどうかとなるドライバーが確認されますが設定されます---接続ハンドルを使用して暗号化または復号化の操作中に有効なままする必要があります。リスト。 一覧で、CMK パスでない場合、操作は失敗します。 アプリケーションでは、この属性の属性をもう一度設定しなくても、信頼済みの Cmk のリストを変更するには、ポイント メモリの内容を変更できます。

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアを操作する

暗号化またはデータを復号化は、ドライバーは、ターゲット列に対して構成されている、CEK を取得する必要があります。 Cek は、暗号化された形式 (ECEKs) で、データベースのメタデータに格納されます。 各 CEK には、暗号化に使用された対応する CMK があります。 [データベース メタデータ](../../t-sql/statements/create-column-master-key-transact-sql.md)自体 CMK を格納しません、キーストアとキーストアは、CMK の検索に使用できる情報の名前にはのみが含まれます。

ECEK のプレーン テキスト値を取得するドライバー最初取得 CEK とその対応する CMK の両方に関するメタデータし、CMK を格納しているキーストアにお問い合わせくださいこの情報を使用して、ECEK の暗号化解除を要求します。 ドライバーは、キーストア プロバイダーを使用するキーストアと通信します。

### <a name="built-in-keystore-providers"></a>組み込みのキーストア プロバイダー

ODBC Driver for SQL Server は、次の組み込みのキーストア プロバイダーが付属します。

| [オブジェクト名] | [説明] | (メタデータ) のプロバイダー名 |可用性|
|:---|:---|:---|:---|
|Azure Key Vault |Azure Key Vault でのストアの Cmk | `AZURE_KEY_VAULT` |Windows、macOS、Linux|
|Windows 証明書ストア|Windows ストアの Cmk をローカルに保存します。| `MSSQL_CERTIFICATE_STORE`|Windows|

- ユーザー (またはデータベース管理者) は、列マスター キーのメタデータで構成されているプロバイダー名が正しいこと、および列マスター キー パスが、特定のプロバイダーに対するキー パス形式に準拠していることを確認する必要があります。 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md) ステートメントを発行した際に有効なプロバイダー名とキー パスを自動的に生成する、SQL Server Management Studio などのツールを使用してキーを構成することをお勧めします。

- アプリケーションがキー ストア内のキーにアクセスできることを確認する必要があります。 これには、キーストアに応じてキーまたはキー ストアへのアクセスをアプリケーションに許可したり、その他のキー ストア固有の構成手順を行ったりするプロセスが含まれる場合があります。 など、Azure Key Vault にアクセスするには、キーストアに正しい資格情報を提供する必要があります。

### <a name="using-the-azure-key-vault-provider"></a>Azure Key Vault プロバイダーを使用する

Azure Key Vault は、特にアプリケーションが Azure でホストされている場合、Always Encrypted の列マスター キーの格納と管理に便利なオプションです。 Linux、macOS、および Windows 上の SQL Server 用 ODBC ドライバーには、Azure Key Vault の組み込み列マスター キー ストア プロバイダーが含まれています。 参照してください[Azure Key Vault - ステップ バイ ステップ](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/)、 [Key Vault の概要](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)、および[Azure Key Vault で列マスター_キーの作成](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2)Azure のキーの構成の詳細については資格情報コンテナーの Always Encrypted の。

> [!NOTE]
> Linux、macOS、ドライバーのバージョン 17.2 以降で`libcurl`このプロバイダーの使用が必要ですが、ドライバーを使用したその他の操作は必要ないために、明示的な依存関係はありません。 エラーが発生する場合に関する`libcurl`がインストールされていることを確認します。

ドライバーでは、次の資格情報の種類を使用して Azure Key Vault への認証がサポートされています。

- ユーザー名/パスワード – この方法で、資格情報には、Azure Active Directory ユーザーとパスワードの名前が。

- この方法でクライアント ID/シークレット: 資格情報は、アプリケーション クライアント ID とアプリケーション シークレットが。

列の暗号化の AKV に格納されている Cmk を使用するドライバーを許可するのには、次の接続文字列専用のキーワードを使用します。

|[資格情報の種類]| `KeyStoreAuthentication` |`KeyStorePrincipalId`| `KeyStoreSecret` |
|-|-|-|-|
|ユーザー名/パスワード| `KeyVaultPassword`|ユーザー プリンシパル名|パスワード|
|クライアント ID/シークレット| `KeyVaultClientSecret`|クライアント ID|シークレット|

#### <a name="example-connection-strings"></a>接続文字列の例

次の接続文字列は、2 つの資格情報の種類で、Azure Key Vault に認証する方法を示します。

**クライアント Id/シークレット**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultClientSecret;KeyStorePrincipalId=<clientId>;KeyStoreSecret=<secret>
```

**ユーザー名/パスワード**

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultPassword;KeyStorePrincipalId=<username>;KeyStoreSecret=<password>
```

AKV を使用して、CMK の記憶域には、他の ODBC アプリケーションの変更は必要ありません。

### <a name="using-the-windows-certificate-store-provider"></a>Windows 証明書ストア プロバイダーの使用

Windows 上の SQL Server 用 ODBC ドライバーには、Windows 証明書ストア、という名前の組み込み列マスター キー ストア プロバイダーが含まれています。`MSSQL_CERTIFICATE_STORE`します。 (このプロバイダーは macOS または Linux で使用できません) です。このプロバイダーでは、CMK がクライアント コンピューターでローカルに格納されているし、ドライバーで使用するために必要な追加の構成、アプリケーションではありません。 ただし、アプリケーションと、ストアに証明書とその秘密キーにアクセスできる場合があります。 詳しくは、「[列マスター キーを作成して保存する (Always Encrypted)](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted)」をご覧ください。

### <a name="using-custom-keystore-providers"></a>カスタム キーストア プロバイダーの使用

ODBC Driver for SQL Server には、CEKeystoreProvider インターフェイスを使用してカスタムのサード パーティ製キーストア プロバイダーもサポートしています。 これにより、アプリケーションを読み込み、クエリ、および暗号化された列へのアクセスに、ドライバーによって使用できるように、キーストア プロバイダーを構成できます。 アプリケーションが SQL Server での記憶域の Cek を暗号化し、ODBC; で暗号化された列にアクセスする以外のタスクを実行するにはキーストア プロバイダーとやり取りも直接可能性があります。詳細については、次を参照してください。[カスタム キーストア プロバイダー](../../connect/odbc/custom-keystore-providers.md)します。

2 つの接続属性は、カスタムのキーストア プロバイダーとの対話に使用されます。 これらは次のとおりです。

- `SQL_COPT_SS_CEKEYSTOREPROVIDER`

- `SQL_COPT_SS_CEKEYSTOREDATA`

前者は後者の場合は、アプリケーション プロバイダーの通信を可能に読み込まれたキーストアのプロバイダーの列挙を読み込んで使用されます。 これらの接続属性は、前に、またはアプリケーション プロバイダーの操作では、SQL Server との通信を含まないため、接続を確立した後、いつでも使用できます。 ただし、ドライバーがまだ読み込まれていない、ため、設定と接続する前にこれらの属性を取得は、ドライバー マネージャーによって処理するキーを押さないし、期待どおりの結果を生成しない可能性があります。

#### <a name="loading-a-keystore-provider"></a>キーストア プロバイダーの読み込み

設定、`SQL_COPT_SS_CEKEYSTOREPROVIDER`接続属性が含まれるキーストア プロバイダーを利用できるように、プロバイダー ライブラリを読み込むクライアント アプリケーションを使用します。

```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```
| 引数 | [説明] |
|:---|:---|
|`ConnectionHandle`|[入力]接続ハンドルです。 有効な接続ハンドルである必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから同じプロセス内の他のアクセス。|
|`Attribute`|[入力]設定する属性:`SQL_COPT_SS_CEKEYSTOREPROVIDER`定数。|
|`ValuePtr`|[入力]プロバイダー ライブラリのファイル名を指定する null で終わる文字列へのポインター。 SQLSetConnectAttrA、これは、ANSI の (マルチバイト) 文字列です。 SQLSetConnectAttrW、これは Unicode (wchar_t) 文字列です。|
|`StringLength`|[入力]ValuePtr 文字列、または SQL_NTS の長さ。|

ドライバーが読み込みメカニズム プラットフォーム定義されているダイナミック ライブラリを使用して ValuePtr パラメーターで識別されるライブラリの読み込みを試行 (`dlopen()` Linux と macOS、 `LoadLibrary()` Windows 上) の一覧にその中に定義されているすべてのプロバイダーを追加します。ドライバーに既知のプロバイダー。 次のエラーが発生することがあります。

| [エラー] | [説明] |
|:--|:--|
|`CE203`|ダイナミック ライブラリを読み込むことができませんでした。|
|`CE203`|ライブラリで"CEKeyStoreProvider"エクスポート シンボルが見つかりませんでした。|
|`CE203`|1 つまたは複数のプロバイダー ライブラリに既に読み込まれています。|

`SQLSetConnectAttr` 通常のエラーまたは成功を示す値、および追加情報が使用できる標準の ODBC 診断メカニズムを使用して発生したエラーを返します。

> [!NOTE]
> アプリケーション プログラマでは、それらを必要とする任意のクエリがすべて接続経由で送信される前に、カスタム プロバイダーが読み込まれたことを確認する必要があります。 このようにしないと、エラーが発生します。

| [エラー] | [説明] |
|:--|:--|
|`CE200`|キーストア プロバイダー %1 が見つかりません。 適切なキーストア プロバイダー ライブラリが読み込まれたことを確認します。|

> [!NOTE]
> キーストア プロバイダー実装の使用を避ける必要があります`MSSQL`カスタム プロバイダーの名前。 この用語は、Microsoft 専用として予約されていると、将来の組み込みプロバイダーで競合が発生する可能性があります。 カスタム プロバイダーの名前には、この用語を使用して、ODBC の警告が可能性があります。

#### <a name="getting-the-list-of-loaded-providers"></a>読み込まれているプロバイダーの一覧を取得します。

クライアント アプリケーションなど構築された。 ドライバーに現在読み込まれてキーストア プロバイダーを確認することができるこの接続属性を取得します。これは、接続した後のみ実行できます。

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```
| 引数 | [説明] |
|:---|:---|
|`ConnectionHandle`|[入力]接続ハンドルです。 有効な接続ハンドルである必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから同じプロセス内の他のアクセス。|
|`Attribute`|[入力]取得する属性:`SQL_COPT_SS_CEKEYSTOREPROVIDER`定数。|
|`ValuePtr`|[出力]次のプロバイダー名を返すメモリへのポインター。|
|`BufferLength`|[入力]ValuePtr バッファーの長さ。|
|`StringLengthPtr`|[出力](Null 終了文字を除く) バイトの合計数を返すバッファーへのポインターで返される使用可能な\*ValuePtr します。 ValuePtr が null ポインターの場合は、長さは返されません。 属性値が文字の文字列と、返される使用可能なバイト数が null 終了の長さマイナス BufferLength より大きい場合、文字でデータ\*ValuePtr がの長さマイナス BufferLength に切り捨てられます、null 終端文字は、ドライバーが null で終わるとします。|

全体の一覧の取得を許可するのには、すべての Get 操作は、現在のプロバイダー名を返し、次の内部のカウンターをインクリメントします。 このカウンターが空の文字列、リストの末尾に達すると ("") が返されると、カウンターがリセットされます。一連の Get 操作は、リストの先頭からもう一度に進みます。

### <a name="communicating-with-keystore-providers"></a>キーストア プロバイダーとの通信

`SQL_COPT_SS_CEKEYSTOREDATA`接続属性が材料などのキーの更新、追加のパラメーターを構成するために読み込まれたキーストア プロバイダーと通信するクライアント アプリケーションを使用します。クライアント アプリケーションとプロバイダー間の通信に依存して、Get に基づく単純な要求-応答プロトコルと、この接続属性を使用して要求を設定します。 通信は、クライアント アプリケーションによってのみ開始されます。

> [!NOTE]
> ODBC の性質により、ODBC インターフェイスのみでは接続コンテキストの解像度でデータを設定 (SQLGet/SetConnectAttr) に CEKeyStoreProvider の応答を呼び出します。

アプリケーションは、CEKeystoreData 構造によってドライバーを通じてキーストア プロバイダーと通信します。

```
typedef struct CEKeystoreData {
wchar_t *name;
unsigned int dataSize;
char data[];
} CEKEYSTOREDATA;
```
| 引数 | [説明] |
|:---|:---|
|`name`|[入力]プロバイダーの名前、設定時にデータを送信します。 取得時に無視されます。 Null で終わる、ワイド文字の文字列。|
|`dataSize`|[入力]次の構造のデータ配列のサイズ。|
|`data`|[InOut]によって、プロバイダーに送信されるデータのセット。 任意のデータがあります。ドライバーは、それを解釈する操作を行わない。 Get、時に、プロバイダーからデータを受信するバッファーを読み取る。|

#### <a name="writing-data-to-a-provider"></a>プロバイダーにデータを書き込む

A`SQLSetConnectAttr`を使用して呼び出す、`SQL_COPT_SS_CEKEYSTOREDATA`属性が指定されたキーストア プロバイダーを「パケット」形式のデータを書き込みます。
```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```
| 引数 | [説明] |
|:---|:---|
|`ConnectionHandle`| [入力]接続ハンドルです。 有効な接続ハンドルである必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから同じプロセス内の他のアクセス。|
|`Attribute`|[入力]設定する属性:`SQL_COPT_SS_CEKEYSTOREDATA`定数。|
|`ValuePtr`|[入力]CEKeystoreData 構造体へのポインター。 構造体の名前 フィールドでは、データが対象とするプロバイダーを識別します。|
|`StringLength`|[入力]SQL_IS_POINTER 定数|

追加の詳細なエラー情報を使用して取得できる[SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx)します。

> [!NOTE]
> これがご希望の場合、プロバイダーに固有の接続に書き込まれたデータを関連付ける接続ハンドルを使用できます。 これは接続ごとの構成を実装するために役立ちます。 接続コンテキストを無視し、データを送信するための接続に関係なく同じデータを扱うこと可能性がありますもします。 参照してください[コンテキスト関連付け](../../connect/odbc/custom-keystore-providers.md#context-association)詳細についてはします。

#### <a name="reading-data-from-a-provider"></a>プロバイダーからデータを読み取る

呼び出し`SQLGetConnectAttr`を使用して、`SQL_COPT_SS_CEKEYSTOREDATA`属性の読み取りからのデータ「パケット」 *、最後の書き込み先*プロバイダー。 [なし] が、関数のシーケンス エラーが発生します。 キーストア プロバイダーの実装側は、そのためには理にかなっている場合、その他の副作用を発生させることがなく読み取り操作のプロバイダーを選択した場合の方法として、0 バイトの「ダミー書き込み」をサポートすることが推奨されます。

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```
| 引数 | [説明] |
|:---|:---|
|`ConnectionHandle`|[入力]接続ハンドルです。 有効な接続ハンドルである必要がありますが、1 つの接続ハンドル経由で読み込まれるプロバイダーから同じプロセス内の他のアクセス。|
|`Attribute`|[入力]取得する属性:`SQL_COPT_SS_CEKEYSTOREDATA`定数。|
|`ValuePtr`|[出力]プロバイダーからのデータを読み取る CEKeystoreData 構造へのポインターが配置されます。|
|`BufferLength`|[入力]SQL_IS_POINTER 定数|
|`StringLengthPtr`|[出力]BufferLength を返すバッファーへのポインター。 場合 * ValuePtr が null ポインターの長さは返されません。|

呼び出し元は、プロバイダーに書き込むため CEKEYSTOREDATA 構造に従って、十分な長さのバッファーが割り当てられることを確認してください。 戻り時に、dataSize フィールドは、プロバイダーから読み取られるデータの実際の長さで更新されます。 追加の詳細なエラー情報を使用して取得できる[SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx)します。

このインターフェイスは、キーストア プロバイダー アプリケーション間で転送されるデータの形式で追加の要件を配置ありません。 各プロバイダーは、そのニーズに応じて、独自のプロトコル/データ形式を定義できます。

キーストア プロバイダの実装の例は、次を参照してください[カスタム キーストア プロバイダー。](../../connect/odbc/custom-keystore-providers.md)

## <a name="limitations-of-the-odbc-driver-when-using-always-encrypted"></a>Always Encrypted を使用する場合は、ODBC ドライバーの制限事項

### <a name="asynchronous-operations"></a>非同期操作
ODBC ドライバーが使用できるように、中に[非同期操作](../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)、Always encrypted はパフォーマンスに影響する操作に Always Encrypted が有効にするとします。 呼び出し`sys.sp_describe_parameter_encryption`暗号化メタデータを特定のステートメントがブロックしているとすると、ドライバーは、サーバーを返す前に、メタデータを返すまで待機する`SQL_STILL_EXECUTING`します。

### <a name="retrieve-data-in-parts-with-sqlgetdata"></a>SQLGetData を使用して、パーツ内のデータを取得します。
ODBC Driver 17 for SQL Server では、暗号化前に文字とバイナリ列は、SQLGetData を使用してパーツを取得できません。 列全体のデータを格納するための十分な長さのバッファーを使って、SQLGetData を 1 つだけの呼び出しを行んだことができます。

### <a name="send-data-in-parts-with-sqlputdata"></a>SQLPutData を使用して、パーツでデータを送信します。
SQLPutData と部分では、データの挿入や比較を送信できません。 全体のデータを格納するバッファーと、SQLPutData に 1 つだけの呼び出しを実現できますが。 暗号化された列に長いデータを挿入するためには、入力データ ファイルを使用した次のセクションで説明されている、一括コピー API を使用します。

### <a name="encrypted-money-and-smallmoney"></a>暗号化された money と smallmoney
暗号化された**money**または**smallmoney**列は、パラメーターの対象となることはできません、ODBC データ型のオペランド型の競合エラーを発生させる、それらの型にマップされますの関連であるためです。

## <a name="bulk-copy-of-encrypted-columns"></a>暗号化された列の一括コピー

使用、 [SQL 一括コピー関数](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)と**bcp** SQL Server 用 ODBC Driver 17 以降ユーティリティで Always Encrypted でサポートされます。 プレーン テキスト (挿入時に暗号化およびで復号化された取得) と (そのまま転送) の暗号化テキストの両方を挿入できるし、一括コピー (bcp_ *) Api を使用して取得し、 **bcp**ユーティリティ。

- Varbinary (max) の形式 (たとえば、別のデータベースに読み込む一括) で暗号化テキストを取得せずに接続する、`ColumnEncryption`オプション (またはに設定する`Disabled`) BCP OUT 操作を実行します。

- 挿入しプレーン テキストを取得し、ドライバーが暗号化および復号化、必要な設定としてを透過的に実行できるようにする`ColumnEncryption`に`Enabled`だけで十分です。 BCP API の機能は、それ以外の場合変更されません。

- Varbinary (max) の形式 (例: 取得された上) で暗号化テキストを挿入、設定、`BCPMODIFYENCRYPTED`オプションを TRUE にして、BCP IN 操作を実行します。 結果として得られるデータを復号可能なためには、転送先の列の CEK が元の暗号化テキストの取得元と同じことを確認します。

使用する場合、 **bcp**ユーティリティ: コントロールに、`ColumnEncryption`設定、-d オプションを使用して、目的の値を含む DSN を指定します。 暗号化テキストを挿入することを確認、`ALLOW_ENCRYPTED_VALUE_MODIFICATIONS`ユーザーの設定を有効にします。

次の表は、暗号化された列で動作しているときに操作の概要を示します。

|`ColumnEncryption`|BCP の方向|[説明]|
|----------------|-------------|-----------|
|`Disabled`|(クライアント) に|暗号化テキストを取得します。 観察対象のデータ型は**varbinary (max)** します。|
|`Enabled`|(クライアント) に|プレーン テキストを取得します。 ドライバーは、列のデータを復号化されます。|
|`Disabled`|IN (サーバー) に|暗号化テキストを挿入します。 これは、復号化される不透明読み込まなくても暗号化されたデータを移動するためものです。 場合、操作は失敗、`ALLOW_ENCRYPTED_VALUE_MODIFICATIONS`オプション、ユーザーが設定されていないまたは BCPMODIFYENCRYPTED 接続ハンドルが設定されていません。 詳しくは以下をご覧ください。|
|`Enabled`|IN (サーバー) に|プレーン テキストを挿入します。 ドライバーは列のデータを暗号化します。|

### <a name="the-bcpmodifyencrypted-option"></a>BCPMODIFYENCRYPTED オプション

データの破損を防ぐためには、サーバー通常により暗号化された列に直接暗号化テキストを挿入して、したがってこれを行うには失敗します。ただし、設定、BCP API を使用して暗号化されたデータの一括読み込みの`BCPMODIFYENCRYPTED` [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)暗号化テキストを直接挿入するにより、オプションを TRUE に設定で暗号化されたデータの破損のリスクを軽減し、`ALLOW_ENCRYPTED_VALUE_MODIFICATIONS`ユーザー アカウントのオプション。 それでも、キー、データが一致する必要があり、一括挿入した後、さらに使用する前に挿入するデータの一部の読み取り専用チェックを実行することをお勧めします。

詳しくは、「[Always Encrypted で保護された機微なデータの移行](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md)」をご覧ください。

## <a name="always-encrypted-api-summary"></a>Always Encrypted API の概要

### <a name="connection-string-keywords"></a>接続文字列キーワード

|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|`ColumnEncryption`|許容値は`Enabled` /`Disabled`します。<br>`Enabled` -- 接続の Always Encrypted 機能を有効にします。<br>`Disabled` -- 接続の Always Encrypted 機能を無効にします。 <br><br>既定値は `Disabled` です。|  
|`KeyStoreAuthentication` | 有効な値: `KeyVaultPassword`、`KeyVaultClientSecret` |
|`KeyStorePrincipalId` | ときに`KeyStoreAuthentication`  =  `KeyVaultPassword`、有効な Azure Active Directory ユーザー プリンシパル名にこの値を設定します。 <br>ときに`KeyStoreAuthetication`  =  `KeyVaultClientSecret`有効な Azure Active Directory アプリケーション クライアント ID にこの値を設定 |
|`KeyStoreSecret` | ときに`KeyStoreAuthentication`  =  `KeyVaultPassword`対応するユーザー名のパスワードにこの値を設定します。 <br>ときに`KeyStoreAuthentication`  =  `KeyVaultClientSecret`有効な Azure Active Directory アプリケーション クライアント ID に関連付けられているアプリケーションのシークレットにこの値を設定|

### <a name="connection-attributes"></a>接続属性

|[オブジェクト名]|型|[説明]|  
|----------|-------|----------|  
|`SQL_COPT_SS_COLUMN_ENCRYPTION`|接続前|`SQL_COLUMN_ENCRYPTION_DISABLE` (0)--Always Encrypted を無効にします。 <br>`SQL_COLUMN_ENCRYPTION_ENABLE` (1): Always Encrypted を有効にします。|
|`SQL_COPT_SS_CEKEYSTOREPROVIDER`|接続後|[設定]CEKeystoreProvider をロードしようとしてください。<br>[取得]CEKeystoreProvider 名を返す|
|`SQL_COPT_SS_CEKEYSTOREDATA`|接続後|[設定]CEKeystoreProvider にデータを書き込む<br>[取得]CEKeystoreProvider からデータを読み取る|
|`SQL_COPT_SS_CEKCACHETTL`|接続後|[設定]CEK のキャッシュの TTL 設定します。<br>[取得]現在の CEK キャッシュ TTL を取得します。|
|`SQL_COPT_SS_TRUSTEDCMKPATHS`|接続後|[設定]信頼されている CMK パス ポインターを設定します。<br>[取得]現在の信頼された CMK パス ポインターを取得します。|

### <a name="statement-attributes"></a>ステートメント属性

|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|`SQL_SOPT_SS_COLUMN_ENCRYPTION`|`SQL_CE_DISABLED` (0)--ステートメントの always Encrypted が無効になっています <br>`SQL_CE_RESULTSETONLY` (1)--のみ復号化します。 結果セットと戻り値は復号化、およびパラメーターが暗号化されていません。 <br>`SQL_CE_ENABLED` (3): always Encrypted が有効になっており、パラメーターと結果の両方に使用|

### <a name="descriptor-fields"></a>記述子フィールド

|IPD フィールド|サイズやタイプ|既定値|[説明]|
|-|-|-|-|  
|`SQL_CA_SS_FORCE_ENCRYPT` (1236)|WORD (2 バイト)|0|ときに 0 (既定): このパラメーターを暗号化するかどうかは、暗号化メタデータの可用性によって決まります。<br><br>0 以外の場合: このパラメーターの暗号化メタデータがある場合は暗号化されます。 エラー [CE300] で、要求が失敗するそれ以外の場合、[Microsoft] [ODBC Driver 13 for SQL Server] の必須の暗号化では、パラメーターが指定されましたが、サーバーによって暗号化メタデータが指定されていません。|

### <a name="bcpcontrol-options"></a>bcp_control オプション

|オプション名|既定値|[説明]|
|-|-|-|
|`BCPMODIFYENCRYPTED` (21)|FALSE|TRUE の場合は、暗号化された列に挿入する varbinary (max) 値を許可します。 FALSE の場合は、正しい種類と暗号化メタデータを指定しない限り、カーソルをできないようにします。|

## <a name="see-also"></a>参照

- [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Always Encrypted 関連のブログ](http://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)

