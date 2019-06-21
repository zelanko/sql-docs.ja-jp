---
title: SQL Server 用 PHP ドライバーと共に Always Encrypted を使用する | Microsoft Docs
ms.date: 01/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
manager: mbarwin
ms.openlocfilehash: 5c82c32922712b377fd732b6745b1761e9f32a82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126764"
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>SQL Server 用 PHP ドライバーと共に Always Encrypted を使用する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>適用対象
 -   Microsoft SQL Server 用 Drivers 5.2 for PHP
 
## <a name="introduction"></a>概要

この記事では、[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) と [SQL Server 用 PHP ドライバー](../../connect/php/Microsoft-php-driver-for-sql-server.md)を使用して PHP アプリケーションを開発する方法について説明します。

Always Encrypted を使用すると、クライアント アプリケーションは SQL Server または Azure SQL データベースにデータまたは暗号化キーを開示することなく、機密データを暗号化することができます。 ODBC Driver for SQL Server など、Always Encrypted が有効なドライバーは、クライアント アプリケーション内の機密データを透過的に暗号化および暗号化解除します。 ドライバーは、どのクエリ パラメーターが機密データベース列 (Always Encrypted を使用して保護される) に対応するかを自動的に決定し、SQL Server または Azure SQL データベースにデータを渡す前にこれらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、「 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。 SQL Server 用 PHP ドライバーでは、機密データを暗号化する SQL Server 用 ODBC ドライバーを利用します。

## <a name="prerequisites"></a>Prerequisites

 -   データベースで Always Encrypted を構成します。 この構成には、Always Encrypted キーのプロビジョニング、および選択したデータベース列の暗号化の設定が含まれます。 Always Encrypted が構成されたデータベースがない場合は、「 [Always Encrypted の作業の開始](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted)」の手順に従います。 特に、ご利用のデータベースには、列マスターキー (CMK) 用、列暗号化キー (CEK) 用、およびその CEK を使用して暗号化された 1 つまたは複数の列を含むテーブル用のメタデータ定義を含める必要があります。
 -   ODBC Driver for SQL Server バージョン 17 以降が開発用コンピューターにインストールされていることを確認します。 詳細については、次を参照してください。 [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)します。

## <a name="enabling-always-encrypted-in-a-php-application"></a>PHP アプリケーションで Always Encrypted を有効にする

暗号化された列をターゲットとするパラメーターの暗号化と、クエリ結果の暗号化解除を有効にする最も簡単な方法としては、`ColumnEncryption` 接続文字列キーワードの値を `Enabled` に設定します。 SQLSRV と PDO_SQLSRV ドライバーで Always Encrypted を有効にするの例を次に示します。

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

暗号化または暗号化解除を正常に行うには、Always Encrypted を有効にするだけでは不十分です。さらに、次のようになっていることを確認する必要があります。
 -   アプリケーションが、データベース内の Always Encrypted キーに関するメタデータへのアクセスに必要な VIEW ANY COLUMN MASTER KEY DEFINITION および VIEW ANY COLUMN ENCRYPTION KEY DEFINITION データベース権限を持っています。 詳細については、[データベース権限](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions)に関するページをご覧ください。
 -   アプリケーションで、クエリ対象の暗号化された列の CEK を保護する CMK にアクセスできる。 この要件は、CMK を格納するキー ストア プロバイダーに依存します。 詳細については、「[列マスター キー ストアを操作する](#working-with-column-master-key-stores)」をご覧ください。

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>暗号化された列のデータを取得および変更する

接続で Always Encrypted を有効すると、標準の SQLSRV Api を使用することができます (を参照してください[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)) または PDO_SQLSRV Api (を参照してください[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)) を取得またはデータを変更するには暗号化されたデータベースの列。 ご利用のアプリケーションが必要なデータベース権限を備えていて、列マスター キーにアクセスできると仮定すると、ドライバーによって、暗号化された列をターゲットとするクエリ パラメータが暗号化され、暗号化された列から取得したデータの暗号化が解除されます。これらの動作は列が暗号化されていないかのようにアプリケーションに対して透過的に行われます。

Always Encrypted が有効でない場合、暗号化された列をターゲットとするパラメーターを含むクエリは失敗します。 暗号化された列をターゲットとするパラメーターがクエリにない場合は、暗号化された列からデータを取得できます。 ただし、ドライバーによって暗号化の解除は試みられず、アプリケーションでは暗号化されたバイナリ データを (バイト配列として) 受け取ることになります。

次の表は、Always Encrypted が有効かどうかに応じたクエリの動作をまとめたものです。

|クエリの特性|Always Encrypted が有効になっており、アプリケーションがキーとキー メタデータにアクセスできる|Always Encrypted が有効になっており、アプリケーションがキーまたはキー メタデータにアクセスできない|Always Encrypted が無効になっている|
|---|---|---|---|
|暗号化された列をターゲットとするパラメーター。|パラメーター値は透過的に暗号化されます。|Error|Error|
|暗号化された列をターゲットとするパラメーターを含まない、暗号化された列からのデータの取得。|暗号化された列の結果は透過的に暗号化解除されます。 アプリケーションでは、プレーン テキスト列の値を受け取ります。 |Error|暗号化された列の結果は暗号化解除されません。 アプリケーションは、暗号化された値をバイト配列として受け取ります。|
 
次の例は、暗号化された列のデータを取得および変更する方法を示しています。 この例では、次のスキーマを持つテーブルを想定しています。 SSN 列と BirthDate 列は暗号化されています。
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

### <a name="data-insertion-example"></a>データ挿入の例

次の例では、SQLSRV と PDO_SQLSRV ドライバーを使用して、患者のテーブルに行を挿入する方法を示します。 次の点に注意してください。
 -   このサンプル コードの暗号化に固有のものは何もありません。 暗号化された列をターゲットとする SSN および BirthDate パラメーターの値が、ドライバーによって自動的に検出されて、暗号化されます。 このメカニズムにより、アプリケーションに対して暗号化が透過的に実行されます。
 -   暗号化された列を含め、データベース列に挿入された値は、バインドされたパラメーターとして渡されます。 暗号化されていない列に値を送信する場合、パラメーターの使用は省略可能です (ただし、SQL インジェクションを防ぐのに役立つので、強くお勧めします) が、暗号化された列をターゲットとする値に対しては必須です。 SSN 列または BirthDate 列に挿入された値がクエリ ステートメントに埋め込まれたリテラルとして渡された場合、ドライバーではクエリ内のリテラルの暗号化または処理が試行されないため、クエリは失敗します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。
 -   バインド パラメーターを使用して値を挿入するときにデータベースには、ターゲット列のデータ型と同じまたは、対象列のデータ型への変換がサポートされている SQL 型を渡す必要があります。 この要件は、Always Encrypted、いくつかの型変換をサポートしているため (詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md))。 2 つの PHP ドライバー、SQLSRV と PDO_SQLSRV、それぞれがユーザーの値の SQL 型を決定を支援するためのメカニズムです。 そのため、ユーザーは、SQL 型を明示的に指定する必要はありません。
  -   SQLSRV ドライバーをユーザーが 2 つのオプション。
   -   確認および適切な SQL 型を設定する PHP driver に依存します。 この場合、ユーザーが使用する必要があります`sqlsrv_prepare`と`sqlsrv_execute`パラメーター化クエリを実行します。
   -   SQL 型を明示的に設定します。
  -   PDO_SQLSRV ドライバーの場合、ユーザーにパラメーターの SQL 型を明示的に設定するオプションはありません。 PDO_SQLSRV ドライバーは、パラメーターをバインドするときに、SQL 型を決定するユーザーを自動的に役立ちます。
 -   SQL 型を特定するドライバー、いくつかの制限が適用されます。
  -   SQLSRV ドライバー:
   -   暗号化された列の SQL 型を判定するドライバーは、ユーザーが、ユーザーを使用する必要があります`sqlsrv_prepare`と`sqlsrv_execute`します。
   -   場合`sqlsrv_query`が優先すると、ユーザーがすべてのパラメーターの SQL 型を指定する責任を負います。 指定された SQL 型には、文字列型の場合は、文字列の長さとスケールと有効桁数の decimal 型を含める必要があります。
  -   PDO_SQLSRV ドライバー:
   -   ステートメント属性`PDO::SQLSRV_ATTR_DIRECT_QUERY`パラメーター化されたクエリはサポートされていません。
   -   ステートメント属性`PDO::ATTR_EMULATE_PREPARES`パラメーター化されたクエリはサポートされていません。
   
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

### <a name="plaintext-data-retrieval-example"></a>プレーンテキスト データの取得の例

次の例では、暗号化された値と SQLSRV と PDO_SQLSRV ドライバーを使用して暗号化された列からプレーン テキスト データの取得に基づくデータのフィルター処理を示します。 次の点に注意してください。
 -   バインド パラメーターを使用して SSN 列に対してフィルター処理するために WHERE 句で使用される値は、サーバーに送信する前にドライバーが透過的に暗号化できるように、パラメーターとして渡す必要があります。
 -   バインドされたパラメーターを持つクエリを実行するときに PHP ドライバーで、ユーザーが明示的に SQLSRV ドライバーを使用する場合に、SQL 型が指定されていない限り、ユーザーの SQL 型が自動的に決定します。
 -   ドライバーが SSN 列と BirthDate 列から取得されたデータを透過的に暗号化解除するので、プログラムで出力される値はすべてプレーンテキストになります。
 
注: 暗号化が決定論的である場合にのみ、クエリで暗号化された列に対する等価比較を実行できます。 詳細については、「[明確な暗号化またはランダム化された暗号化の選択](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption)」を参照してください。

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
 -   接続文字列で Always Encrypted が有効になっていないので、クエリは、SSN と BirthDate の暗号化された値をバイト配列として返します (プログラムによって値が文字列に変換されます)。
 -   Always Encrypted が無効の状態で、暗号化された列からデータを取得するクエリは、暗号化された列をターゲットとするパラメーターがない場合に限り、パラメーターを含むことができます。 次のクエリは、データベースで暗号化されない LastName によってフィルター処理を行います。 クエリが SSN または BirthDate によってフィルター処理を行った場合、クエリは失敗します。
 
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

ここでは、暗号化された列を PHP アプリケーションからクエリする際のエラーの一般的なカテゴリと、その対処方法に関するいくつかのガイドラインを示します。

#### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型の変換エラー

Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 サポートされている型の変換の詳細な一覧については、「[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。 データ型の変換エラーを回避するには、次の操作を行います。
 -   SQLSRV ドライバーを使用する場合`sqlsrv_prepare`と`sqlsrv_execute`列のサイズおよび小数点以下桁数のパラメーターの数と共に、SQL 型が自動的に決定されます。
 -   列のサイズとパラメーターの 10 進桁数を持つ SQL 型も自動的に決定されます、PDO_SQLSRV ドライバーを使用して、クエリを実行する、
 -   SQLSRV ドライバーを使用する場合`sqlsrv_query`クエリを実行します。
  -   パラメーターの SQL 型については、ターゲットとする列の型とまったく同じであるか、または SQL 型から列の型への変換がサポートされている。
  -   `decimal` と `numeric` の SQL Server データ型の列をターゲットとするパラメーターの有効桁数と小数点以下桁数が、ターゲット列に対して構成する有効桁数と小数点と同じである。
  -   ターゲット列を変更するクエリで、`datetime2`、`datetimeoffset`、または `time` の SQL Server データ型の列をターゲットとするパラメーターの有効桁数が、ターゲット列の有効桁数以下である。
 -   PDO_SQLSRV ステートメント属性を使用しないでください`PDO::SQLSRV_ATTR_DIRECT_QUERY`または`PDO::ATTR_EMULATE_PREPARES`パラメーター化されたクエリ
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値の代わりにプレーンテキストを渡すことによるエラー

暗号化された列をターゲットとする値はいずれも、サーバーに送信する前に暗号化する必要があります。 暗号化された列でプレーンテキスト値の挿入、変更、フィルター処理を行おうとすると、エラーになります。 このようなエラーを防ぐには、次のことを確認してください。
 -   Always Encrypted が有効に (接続文字列に設定、`ColumnEncryption`キーワードを`Enabled`)。
 -   バインド パラメーターを使用して、暗号化された列をターゲットとするデータを送信すること。 次の例では、暗号化された列 (SSN) でリテラル/定数によって正しくフィルター処理するクエリを示しています。
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスの影響を制御する

Always Encrypted はクライアント側暗号化テクノロジであるため、ほとんどのパフォーマンス オーバーヘッドは、データベースではなくクライアント側で発生します。 暗号化および暗号化解除の操作のコストとは別に、クライアント側のパフォーマンス オーバーヘッドのその他の原因を次に示します。
 -   クエリ パラメーターのメタデータを取得するためのデータベースへの追加のラウンド トリップ。
 -   列マスター キーにアクセスするための列マスター キー ストアの呼び出し。
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>クエリ パラメーターのメタデータを取得するためのラウンド トリップ

既定では、接続に対して Always Encrypted が有効になっている場合、ODBC Driver は、各パラメーター化クエリに対して [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) を呼び出し、クエリ ステートメント (パラメーター値を除く) を SQL Server に渡します。 このストアド プロシージャでは、クエリ ステートメントを分析して、パラメーターを暗号化する必要があるかどうかが判断され、必要がある場合は、ドライバーでパラメーターを暗号化できるようにするため、パラメーターごとに暗号化関連の情報が返されます。

PHP ドライバーは、パラメーターをバインドするユーザーを許可するため、SQL を指定せず、準備されたステートメントを入力、Always Encrypted が有効な接続パラメーターをバインドするときに PHP ドライバーを呼び出す[SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md)で、SQL 型、列のサイズ、および 10 進数字を取得するパラメーターです。 呼び出しに使用し、メタデータ[SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md)します。 これらの余分な`SQLDescribeParam`ユーザーは、ODBC ドライバーは、クライアント側の情報を既に格納されているためには、呼び出しには、データベースに追加のラウンドト リップは必要ないとき`sys.sp_describe_parameter_encryption`が呼び出されました。

前述の動作により、次のような高度な透過性が確保されます: 暗号化された列をターゲットとする値がパラメーターでドライバーに渡される限り、クライアント アプリケーション (およびアプリケーション開発者) は、どのクエリが暗号化された列にアクセスするかを認識する必要がありません。

ODBC Driver for SQL Server とは異なりステートメントまたはクエリ レベルで Always Encrypted を有効にするはまだサポートされていません PHP ドライバー。 

### <a name="column-encryption-key-caching"></a>列暗号化キーのキャッシュ

列暗号化キー (CEK) を暗号化解除するための列マスター キー ストアの呼び出し回数を減らすために、ドライバーによってプレーンテキスト CEK がメモリにキャッシュされます。 データベース メタデータから暗号化された CEK (ECEK) を受け取った後、ODBC ドライバーでは、まず、キャッシュ内の暗号化されたキー値に対応するプレーンテキスト CEK の検索が試みられます。 ドライバーでは、キャッシュ内で対応するプレーンテキスト CEK が見つからない場合にのみ、CMK を含むキー ストアが呼び出されます。

注: ODBC Driver for SQL Server では、2 時間のタイムアウト後にキャッシュ内のエントリが削除されます。 この動作は、つまり、ECEK が指定されている場合、ドライバーはアプリケーションの有効期間中または 2 時間間隔のうち、どちらか短い方の期間中に 1 回だけキー ストアと交信するということです。

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアを操作する

データを暗号化または暗号化解除する場合、ターゲット列に対して構成された CEK がドライバーによって取得される必要があります。 CEK は、データベース メタデータ内に暗号化された形式 (ECEK) で格納されます。 各 CEK には、暗号化する際に使用された対応する CMK があります。 [データベース メタデータ](../../t-sql/statements/create-column-master-key-transact-sql.md)に CMK 自体は格納されません。これにはキー ストアの名前と、キー ストアが CMK を検索するために使用できる情報のみが含まれます。

ECEK のプレーンテキスト値を取得するために、ドライバーでは、まず、CEK とそれに対応する CMK の両方に関するメタデータが取得されます。次に、この情報を使用して CMK を含むキー ストアへのアクセスが行われ、ECEK の暗号化を解除するよう要求が出されます。 ドライバーとキー ストアの通信は、キー ストア プロバイダーを使用して行われます。

Microsoft driver 5.3.0 for PHP for SQL Server、Windows 証明書ストアのプロバイダーと Azure Key Vault のみがサポートされています。 ODBC ドライバー (カスタム キーストア プロバイダー) でサポートされるその他のキーストア プロバイダーはまだサポートされていません。

### <a name="using-the-windows-certificate-store-provider"></a>Windows 証明書ストア プロバイダーの使用

Windows 用の ODBC Driver for SQL Server には、`MSSQL_CERTIFICATE_STORE` と呼ばれる Windows 証明書ストア用の組み込みの列マスター キー ストア プロバイダーが含まれています (このプロバイダーは macOS または Linux では使用できません)。このプロバイダーを使用すると、CMK はクライアント コンピューター上にローカルに格納され、ドライバーでそれを使用するためにアプリケーションで追加の構成を行う必要はありません。 ただし、アプリケーションには、ストア内の証明書とその秘密キーへのアクセス権が必要です。 詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

### <a name="using-azure-key-vault"></a>Azure Key Vault の使用

Azure Key Vault では、暗号化キー、パスワード、および Azure を使用してその他のシークレットを格納する方法を提供および Always Encrypted のキーを格納するために使用できます。 ODBC Driver for SQL Server (バージョン 17 以降) には、Azure Key Vault の組み込みのマスター _ キー ストア プロバイダーが含まれています。 次の接続オプションは、Azure Key Vault の構成の処理: `KeyStoreAuthentication`、 `KeyStorePrincipalId`、および`KeyStoreSecret`します。 
 -   `KeyStoreAuthentication` 2 つの可能な文字列値のいずれかを実行できます:`KeyVaultPassword`と`KeyVaultClientSecret`します。 これらの値は、認証資格情報の種類は他の 2 つのキーワードで使用を制御します。
 -   `KeyStorePrincipalId` Azure Key Vault にアクセスしようとしました。 アカウントの識別子を表す文字列を受け取ります。 
     -   場合`KeyStoreAuthentication`に設定されている`KeyVaultPassword`、し`KeyStorePrincipalId`ユーザーが Azure active Directory の名前を指定する必要があります。
     -   場合`KeyStoreAuthentication`に設定されている`KeyVaultClientSecret`、し`KeyStorePrincipalId`アプリケーション クライアント ID である必要があります
 -   `KeyStoreSecret` 資格情報シークレットを表す文字列を受け取ります。 
     -   場合`KeyStoreAuthentication`に設定されている`KeyVaultPassword`、し`KeyStoreSecret`ユーザーのパスワードをする必要があります。 
     -   場合`KeyStoreAuthentication`に設定されている`KeyVaultClientSecret`、し`KeyStoreSecret`に関連付けられたアプリケーション クライアント id アプリケーション シークレットをある必要があります。

すべての 3 つのオプションは、Azure Key Vault を使用する接続文字列に存在する必要があります。 さらに、`ColumnEncryption`に設定する必要があります`Enabled`します。 場合`ColumnEncryption`に設定されている`Disabled`Azure Key Vault のオプションが存在するが、エラーを発生させずに、スクリプトが続行されますが、暗号化は実行されません。

次の例では、Azure Key Vault を使用して SQL Server に接続する方法を示します。

SQLSRV:

Azure Active Directory アカウントを使用します。
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultPassword", "KeyStorePrincipalId"=>$AADUsername, "KeyStoreSecret"=>$AADPassword);
$conn = sqlsrv_connect($server, $connectionInfo);
```
Azure のアプリケーション クライアント ID とシークレットを使用します。
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultClientSecret", "KeyStorePrincipalId"=>$applicationClientID, "KeyStoreSecret"=>$applicationClientSecret);
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV: Azure Active Directory アカウントの使用。
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultPassword; KeyStorePrincipalId = $AADUsername; KeyStoreSecret = $AADPassword;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```
Azure のアプリケーション クライアント ID とシークレットを使用します。
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultClientSecret; KeyStorePrincipalId = $applicationClientID; KeyStoreSecret = $applicationClientSecret;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Always Encrypted を使用するときの PHP ドライバーの制限事項

SQLSRV と PDO_SQLSRV:
 -   Linux または macOS は Windows 証明書ストアのプロバイダーをサポートしていません
 -   パラメーターの暗号化の強制適用
 -   ステートメント レベルで Always Encrypted を有効にします。 
 -   Linux および macOS ("en_US などで Always Encrypted 機能と非 UTF8 のロケールを使用する場合。ISO-8859-1")、システムについてコード ページ 1252 がインストールされている場合を除き、しない動作可能性があります、暗号化された char (n) 列にデータを null または空の文字列を挿入します。
 
SQLSRV のみ:
 -   使用して`sqlsrv_query`SQL 型を指定せずにバインディング パラメーター
 -   使用して`sqlsrv_prepare`SQL ステートメントのバッチにパラメーターをバインドします。  
 
PDO_SQLSRV のみ:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` パラメーター化クエリで指定されたステートメント属性
 -   `PDO::ATTR_EMULATE_PREPARE` パラメーター化クエリで指定されたステートメント属性
 -   SQL ステートメントのバッチにパラメーターのバインド
 
PHP ドライバーでは、SQL Server とデータベースの ODBC ドライバーによって課される制限も継承します。 参照してください[Always Encrypted を使用する場合は、ODBC ドライバーの制限事項](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)と[常に暗号化の機能詳細](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details)します。  
  
## <a name="see-also"></a>参照  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
