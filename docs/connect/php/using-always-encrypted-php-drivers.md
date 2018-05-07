---
title: SQL Server 用 PHP ドライバーで Always Encrypted を使用して |Microsoft ドキュメント
ms.date: 01/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
manager: mbarwin
ms.openlocfilehash: 93b14d81411e3045d9d6f3a67ce03db281f41f68
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>SQL Server 用 PHP ドライバーで Always Encrypted を使用します。
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>適用
 -   Microsoft Drivers 5.2 for PHP for SQL Server
 
## <a name="introduction"></a>概要

この資料は、PHP を使用してアプリケーションを開発する方法に関する情報を提供[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[SQL Server 用 PHP ドライバー](../../connect/php/Microsoft-php-driver-for-sql-server.md)です。

Always Encrypted を使用すると、クライアント アプリケーションは SQL Server または Azure SQL データベースにデータまたは暗号化キーを開示することなく、機密データを暗号化することができます。 Always Encrypted が有効になっているドライバーなど、SQL Server 用 ODBC ドライバーは透過的に暗号化し、クライアント アプリケーション内の機密データを復号化します。 ドライバーは、どのクエリ パラメーターが機密データベース列 (Always Encrypted を使用して保護される) に対応するかを自動的に決定し、SQL Server または Azure SQL データベースにデータを渡す前にこれらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、「 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。 SQL Server 用 PHP ドライバーでは、機密データを暗号化する SQL Server 用 ODBC ドライバーを利用します。

## <a name="prerequisites"></a>前提条件

 -   データベースで Always Encrypted を構成します。 この構成は、Always Encrypted キーのプロビジョニング、選択したデータベース列の暗号化を設定する必要があります。 Always Encrypted が構成されたデータベースがない場合は、「 [Always Encrypted の作業の開始](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted)」の手順に従います。 具体的には、データベースは、列マスター_キー (CMK)、列暗号化キー (CEK)、およびその CEK を使用して暗号化された 1 つまたは複数の列を含むテーブルのメタデータ定義を含める必要があります。
 -   ODBC Driver for SQL Server 17 またはそれ以降のバージョンが、開発用コンピューターにインストールされていることを確認してください。 詳細については、「 [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)です。

## <a name="enabling-always-encrypted-in-a-php-application"></a>PHP アプリケーションで Always Encrypted を有効にします。

暗号化された列とクエリ結果の復号化をターゲットとするパラメーターの暗号化を有効にする最も簡単な方法は、の値を設定して、`ColumnEncryption`接続文字列キーワードを`Enabled`です。 SQLSRV と PDO_SQLSRV ドライバーで Always Encrypted を有効にする例を次に示します。

SQLSRV:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled");
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

暗号化または暗号化解除を成功させるための十分なは Always Encrypted を有効にします。また、ことを確認する必要があります。
 -   アプリケーションには、VIEW ANY COLUMN MASTER KEY DEFINITION および VIEW ANY COLUMN ENCRYPTION KEY DEFINITION データベースのアクセス許可、データベースで Always Encrypted キーに関するメタデータにアクセスする必要があります。 詳細については、「[データベース権限](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions)です。
 -   アプリケーションは、照会された暗号化列で Cek を保護する CMK にアクセスできます。 この要件は、CMK を格納するキー ストア プロバイダーに依存します。 詳細については、次を参照してください。[列マスター キー ストアの操作](#working-with-column-master-key-stores)です。

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>暗号化された列のデータを取得および変更する

接続で Always Encrypted を有効すると、標準の SQLSRV Api を使用することができます (を参照してください[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)) または PDO_SQLSRV Api (を参照してください[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)) を取得またはデータを変更するには暗号化されたデータベースの列です。 ドライバー、アプリケーションが必要なデータベース権限を持ってし、列マスター _ キーにアクセスできると仮定した場合、暗号化された列をターゲットにし、動作に透過的に暗号化された列から取得されたデータを復号化するクエリ パラメーターを暗号化します列が暗号化されていない場合、アプリケーションです。

Always Encrypted が有効でない場合は、暗号化された列をターゲットとするパラメーターを持つクエリが失敗します。 クエリには、暗号化された列をターゲットとするパラメーターがあるない限り、データはまだ、暗号化された列から取得できます。 ただし、ドライバーは、暗号化の解除を試行していないと、アプリケーションは、暗号化されたバイナリ データ (バイト配列として) を受け取ります。

次の表は、Always Encrypted が有効かどうかに応じて、クエリの動作をまとめたものです。

|クエリの特性 |Always Encrypted が有効にし、アプリケーションがキーとキー メタデータにアクセスできる |Always Encrypted が有効にし、アプリケーションがキーまたはキー メタデータにアクセスできない |Always Encrypted が無効になります | |暗号化された列をターゲットとするパラメーターです |。パラメーターの値は透過的に暗号化します |。エラー |エラー | |データを取得する、暗号化された列からしないで暗号化された列をターゲットとするパラメーターです |。暗号化された列からの結果は透過的に暗号化解除します。 アプリケーションでは、プレーン テキスト列の値を受け取ります。 |エラー |暗号化された列からの結果は暗号化解除されません。 アプリケーションはバイト配列として暗号化された値を受け取ります |。
 
次の例は、暗号化された列のデータを取得および変更する方法を示しています。 例には、次のスキーマを持つテーブルがあるとします。 SSN と BirthDate 列は暗号化されます。
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
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="data-insertion-example"></a>データの挿入の例

次の例では、SQLSRV と PDO_SQLSRV ドライバーを使用して、患者のテーブルに行を挿入する方法を示します。 次の点に注意してください。
 -   このサンプル コードの暗号化に固有のものは何もありません。 ドライバーは自動的に検出し、暗号化された列をターゲット SSN と BirthDate パラメーターの値を暗号化します。 このメカニズムでは、アプリケーションに対して透過的な暗号化を行います。
 -   暗号化された列を含め、データベース列に挿入された値は、バインドされたパラメーターとして渡されます。 中にパラメーターを使用する省略可能な (ただし、SQL インジェクションを防ぐのに役立つのでを強くお勧め) は、暗号化されていない列に値を送信するときは、暗号化された列をターゲットとする値に必要です。 SSN または BirthDate 列に挿入された値は、クエリ ステートメントに埋め込まれたリテラルとして渡された、ドライバーが暗号化またはその他のクエリ内のリテラルの処理を行いませんため、クエリは失敗します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。
 -   バインド パラメーターを使用して値を挿入するときにデータベースに対象列のデータ型と同じであるか、ターゲット列のデータ型を持つ変換はサポートされて SQL 型を渡す必要があります。 この要件がいくつかの型変換は常に暗号化がサポートされるため (詳細については、「 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md))。 2 つの PHP ドライバー、SQLSRV と PDO_SQLSRV、それぞれが、ユーザーが値の SQL 型を判別できるようにするメカニズムです。 そのため、ユーザーは SQL 型を明示的に指定する必要はありません。
  -   SQLSRV ドライバーをユーザーが 2 つのオプション。
   -   特定し、右側の SQL 型を設定する PHP driver に依存します。 この場合、ユーザーが使用する必要があります`sqlsrv_prepare`と`sqlsrv_execute`パラメーター化クエリを実行します。
   -   SQL 型を明示的に設定します。
  -   PDO_SQLSRV ドライバーのユーザーにパラメーターの SQL 型を明示的に設定するオプションはありません。 PDO_SQLSRV ドライバーでは、ユーザーが SQL の型パラメーターをバインドするときに自動的に役立ちます。
 -   SQL 型を特定のドライバー、いくつかの制限が適用されます。
  -   SQLSRV ドライバーの場合:
   -   ユーザーは、暗号化された列の SQL 型を決定するドライバーが、ユーザーを使用する必要があります`sqlsrv_prepare`と`sqlsrv_execute`です。
   -   場合`sqlsrv_query`が優先、ユーザーがすべてのパラメーターの SQL 型を指定することを担当します。 指定された SQL 型には、文字列型の場合は、文字列の長さと、スケールと 10 進数型の有効桁数を含める必要があります。
  -   PDO_SQLSRV ドライバー。
   -   ステートメント属性`PDO::SQLSRV_ATTR_DIRECT_QUERY`パラメーター化クエリではサポートされていません。
   -   ステートメント属性`PDO::ATTR_EMULATE_PREPARES`パラメーター化クエリではサポートされていません。
   
SQLSRV ドライバーと[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel;
$birthDate = "1996-10-19";
$params = array($ssn, $firstName, $lastName, $birthDate);
// during sqlsrv_prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = sqlsrv_prepare($conn, $query, $params);
sqlsrv_execute($stmt);
```

SQLSRV ドライバーと[sqlsrv_query](../../connect/php/sqlsrv-query.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel";
$birthDate = "1996-10-19";
// need to provide the SQL types for ALL parameters  
// note the SQL types (including the string length) have to be the same at the column definition
$params = array(array(&$ssn, null, null, SQLSRV_SQLTYPE_CHAR(11)),
                array(&$firstName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$lastName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$birthDate, null, null, SQLSRV_SQLTYPE_DATE));
sqlsrv_query($conn, $query, $params);
```

PDO_SQLSRV ドライバーと[pdo::prepare](../../connect/php/pdo-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Able";
$birthDate = "1996-10-19";
// during PDO::prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
$stmt->bindParam(2, $firstName);
$stmt->bindParam(3, $lastName);
$stmt->bindParam(4, $birthDate);
$stmt->execute();
```

### <a name="plaintext-data-retrieval-example"></a>プレーン テキスト データの取得の例

次の例では、暗号化された値、および SQLSRV と PDO_SQLSRV ドライバーを使用して暗号化された列からプレーン テキスト データの取得に基づくデータのフィルター処理を示します。 次の点に注意してください。
 -   SSN 列に対してフィルター処理する WHERE 句が必要で渡されるバインド パラメーターを使用して、ドライバーを透過的に暗号化をサーバーに送信する前にできるようにするために使用する値。
 -   バインドされたパラメーターを持つクエリを実行するときに、SQLSRV ドライバーを使用する場合に、ユーザーが SQL 型に明示的を指定しない限り、PHP のドライバーがそのユーザーの SQL 型を自動的に決まります。
 -   プログラムによって印刷されるすべての値はプレーン テキストでは、ドライバーは、SSN と BirthDate 列から取得されたデータを透過的に暗号化解除するためです。
 
注: クエリは必要暗号化が決定的な場合にのみ暗号化された列に対して等価比較を実行できます。 詳細については、次を参照してください。[を選択すると決定性またはランダム化された暗号化](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption)です。

SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = sqlsrv_prepare($conn, $query, array(&$ssn));
// during sqlsrv_execute, the driver encrypts the ssn value and passes it to the database
sqlsrv_execute($stmt);
// fetch like usual
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
// during PDOStatement::execute, the driver encrypts the ssn value and passes it to the database
$stmt->execute();
// fetch like usual
$row = $stmt->fetch();
```

### <a name="ciphertext-data-retrieval-example"></a>暗号化テキスト データの取得の例

Always Encrypted が有効になっていない場合でも、暗号化された列をターゲットとするパラメーターがクエリになければ、クエリでは、暗号化された列からデータを取得できます。

次の例では、SQLSRV と PDO_SQLSRV ドライバーを使用して暗号化された列から暗号化されたバイナリ データの取得を示します。 次の点に注意してください。
 -   接続文字列で Always Encrypted が有効になっていない、クエリは、(プログラムは、値を文字列に変換されます)、バイト配列として SSN と BirthDate の暗号化された値を返します。
 -   Always Encrypted が無効の状態で、暗号化された列からデータを取得するクエリは、暗号化された列をターゲットとするパラメーターがない場合に限り、パラメーターを含むことができます。 データベースは暗号化されない LastName によって次のクエリのフィルター。 クエリが SSN または BirthDate によってフィルター処理、クエリは失敗します。
 
SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = sqlsrv_prepare($conn, $query, array(&$lastName));
sqlsrv_execute($stmt);
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $lastName);
$stmt->execute();
$row = $stmt->fetch();
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>暗号化された列をクエリする際の一般的な問題を回避する

このセクションでは、PHP アプリケーションとそれを回避する方法のいくつかのガイドラインから暗号化された列を照会するときに、エラーの一般的なカテゴリがについて説明します。

#### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型の変換エラー

Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 参照してください[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)サポートされる型変換の詳細な一覧についてはします。 データ型の変換エラーを回避するには、次の操作を行います。
 -   SQLSRV ドライバーを使用したときに`sqlsrv_prepare`と`sqlsrv_execute`列のサイズおよびパラメーターの 10 進数字の数と共に、SQL 型が自動的に決定されます。
 -   列のサイズと、パラメーターの 10 進数を SQL 型も自動的に決定されます、PDO_SQLSRV ドライバーを使用して、クエリを実行する、
 -   SQLSRV ドライバーを使用したときに`sqlsrv_query`クエリを実行します。
  -   SQL の型パラメーターがか正確に対象の列の型と同じまたは SQL 型から列の型への変換はサポートされています。
  -   有効桁数と小数点以下桁数の列をターゲットとするパラメーター、`decimal`と`numeric`SQL Server データ型と同じでは、有効桁数と小数点以下桁数が、ターゲット列に対して構成します。
  -   列をターゲットとするパラメーターの有効桁数`datetime2`、 `datetimeoffset`、または`time`SQL Server データ型は、対象列を変更するクエリ内のターゲット列の有効桁数より大きい値ではありません。
 -   PDO_SQLSRV ステートメント属性を使用しないでください`PDO::SQLSRV_ATTR_DIRECT_QUERY`または`PDO::ATTR_EMULATE_PREPARES`パラメーター化されたクエリ
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値の代わりにプレーンテキストを渡すことによるエラー

暗号化された列を対象とする任意の値は、サーバーに送信される前に暗号化する必要があります。 挿入、変更、またはエラーで、暗号化された列の結果のプレーン テキスト値でフィルター処理を試行します。 このようなエラーを防ぐためには、ことを確認します。
 -   Always Encrypted が有効に (接続文字列で、設定、`ColumnEncryption`キーワードを`Enabled`)。
 -   暗号化された列をターゲットとするデータを送信するのにには、バインド パラメーターを使用します。 次の例は、暗号化された列 (SSN) でリテラル/定数で正しくフィルター処理するクエリを示しています。
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスの影響を制御する

常に暗号化がクライアント側暗号化テクノロジであるため、データベースではなく、クライアント側でほとんどのパフォーマンスのオーバーヘッドが発生します。 暗号化および暗号化解除の操作のコストとは別のパフォーマンスのオーバーヘッドがクライアント側の他の原因を示します。
 -   クエリ パラメーターのメタデータを取得するデータベースへのラウンドト リップ追加します。
 -   列マスター キーにアクセスするための列マスター キー ストアの呼び出し。
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>ラウンドト リップをクエリ パラメーターのメタデータを取得するには

接続に対して Always Encrypted が有効になっている場合、ODBC ドライバーは、既定では、呼び出す[sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)パラメーター化各クエリのクエリ ステートメント (パラメーター値) を除く SQL Server を渡す. このストアド プロシージャを調べる場合は、すべてのパラメーターを暗号化する必要がある場合に、クエリ ステートメントを分析し、それらを暗号化するドライバーを許可するには、各パラメーターの暗号化に関連する情報を返します。

SQL を指定しなくても、準備されたステートメントで次のように入力します PHP ドライバーのパラメーターをバインドするユーザーを許可するため、Always Encrypted が有効な接続でパラメーターをバインドするときに PHP のドライバーを呼び出す[SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md)で、。パラメーターを SQL 型、列のサイズおよび小数点以下桁数を取得します。 呼び出してメタデータを使用し、 [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md)です。 これらの余分な`SQLDescribeParam`として ODBC ドライバーが既に保存された情報は、クライアント側の呼び出しは、データベースへの余分なラウンド トリップを不要と`sys.sp_describe_parameter_encryption`が呼び出されました。

上記の動作が高いことを確認、クライアント アプリケーション (およびアプリケーション開発者) への透過性のレベルは暗号化された列をターゲットとする値がドライバーに渡される限り、暗号化された列にアクセスするクエリについて注意する必要はありませんパラメーター。

ODBC Driver for SQL Server とは異なり、ステートメントまたはクエリ レベルで Always Encrypted を有効にするはまだサポートされていません PHP ドライバーでします。 

### <a name="column-encryption-key-caching"></a>列暗号化キーのキャッシュ

列暗号化キー (CEK) の暗号化を解除するための列マスター キー ストアへの呼び出しの数を減らすためには、ドライバーは、メモリ内でプレーン テキスト Cek をキャッシュします。 受信したら、暗号化された CEK (を使用して ECEK) データベースのメタデータから、ODBC ドライバーは、まず見つけようとキャッシュの暗号化されたキー値に対応するプレーン テキスト CEK です。 ドライバーは、キャッシュに対応するプレーン テキスト CEK を見つけられない場合にのみ、CMK を含むキー ストアを呼び出します。

注: ODBC Driver for SQL Server では、キャッシュ内のエントリは 2 時間のタイムアウト後に削除されます。 この動作は、ことを指定を使用して ECEK のドライバーは、2 時間ごと、またはアプリケーションの有効期間中に 1 回だけキー ストアを取引先担当者は、小さい方を意味します。

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアを操作する

暗号化と、データを暗号化解除、ドライバーは、ターゲット列に対して構成されている、CEK を取得する必要があります。 Cek は、暗号化された形式 (ECEKs) で、データベースのメタデータに格納されます。 各 CEK には、暗号化に使用された対応する CMK があります。 [データベース メタデータ](../../t-sql/statements/create-column-master-key-transact-sql.md)CMK 自体は格納されません、CMK を検索するキー ストアが使用できる情報をキー ストアの名前にはのみが含まれます。

使用して ECEK のプレーン テキスト値を取得するドライバー最初取得 CEK とその対応する CMK の両方に関するメタデータしこの情報を使用して、CMK を含むキー ストアに接続しを使用して ECEK の暗号化を解除することを要求します。 ドライバーは、キー ストア プロバイダーを使用してキー ストアと通信します。

Microsoft Driver 5.2.0 for PHP for SQL Server、Windows 証明書ストアのプロバイダーのみがサポートされます。 2 つ他のキー ストア プロバイダー (Azure Key Vault およびカスタム キー ストア プロバイダー) は、ODBC ドライバーでサポートはまだサポートされていません。

### <a name="using-the-windows-certificate-store-provider"></a>Windows 証明書ストアのプロバイダーを使用します。

ODBC Driver for SQL Server on Windows には、Windows 証明書ストア、という名前の組み込み列マスター キー ストア プロバイダーが含まれています。`MSSQL_CERTIFICATE_STORE`です。 (このプロバイダーは macOS または Linux で使用できません) です。このプロバイダーと、クライアント コンピューターに CMK をローカルに格納されてし、アプリケーションによって追加の構成は、ドライバーで使用する必要はありません。 ただし、アプリケーションでは、ストアに証明書とその秘密キーへのアクセスが必要です。 詳細については、 [Create and Store Column Master Keys (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(列マスター キーの作成と格納 (Always Encrypted)) を参照してください。

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Always Encrypted を使用する場合は、PHP ドライバーの制限事項

SQLSRV と PDO_SQLSRV:
 -   Linux/MacOS サポート
  -   Linux/MacOS では、Windows 証明書ストアのプロバイダーとは PHP ドライバーで現在サポートされている唯一のキー ストア プロバイダーがサポートされません。
 -   パラメーターの暗号化を適用
 -   ステートメント レベルで Always Encrypted を有効にします。 
 
SQLSRV のみ:
 -   使用して`sqlsrv_query`SQL 型を指定せずにバインディング パラメーター
 -   使用して`sqlsrv_prepare`SQL ステートメントのバッチにパラメーターをバインドします。  
 
PDO_SQLSRV のみ:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` パラメーター化クエリで指定されたステートメント属性
 -   `PDO::ATTR_EMULATE_PREPARE` パラメーター化クエリで指定されたステートメント属性
 -   SQL ステートメントのバッチにパラメーターのバインド
 
PHP ドライバーでは、SQL Server とデータベースの場合は、ODBC ドライバーでの使用制限も継承します。 参照してください[Always Encrypted を使用する場合は、ODBC ドライバーの制限事項](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)と[Always Encrypted 機能の詳細](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details)です。  
  
## <a name="see-also"></a>参照  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
