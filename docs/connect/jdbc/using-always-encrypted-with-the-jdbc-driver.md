---
title: "JDBC ドライバーで Always Encrypted を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/30/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 4bc5be85fddcc86de0a3fe845620f5152b568015
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>JDBC ドライバーで Always Encrypted を使用する
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この記事の内容を使用して Java アプリケーションを開発する方法の情報を提供する[Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7)と Microsoft JDBC Driver 6.0 (またはそれ以降) for SQL Server。

Always Encrypted は、機密データを暗号化し、データまたは SQL Server または Azure SQL データベースに暗号化キーを開示することがなくクライアントを許可します。 Always Encrypted は SQL Server のドライバー、Microsoft JDBC Driver 6.0 など (またはそれ以上) を有効になっている、透過的に暗号化およびクライアント アプリケーション内の機密データを復号化することによってこれを実現します。 ドライバーによって、クエリを自動的に決定するパラメーターは (Always Encrypted を使用して保護されている)、機密性の高いデータベース列に対応しているし、SQL Server または Azure SQL Database に、値を渡す前にこれらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7)と[Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。  


## <a name="prerequisites"></a>前提条件

- データベースで Always Encrypted を構成します。 この処理には、Always Encrypted キーのプロビジョニング、および選択したデータベース列の暗号化の設定が含まれます。 Always Encrypted が構成されたデータベースがない場合は、「 [Always Encrypted の作業の開始](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_5)」の手順に従います。
- Microsoft JDBC Driver の確認を行う 6.0 (またはそれ以降) for SQL Server が開発コンピューターにインストールされています。 
-   Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files (JCE 管轄ポリシーファイル (無制限強度)) をダウンロードしてインストールします。  インストール手順、および考えられるエクスポート/インポート問題に関する詳細について、zip ファイルに含まれる Readme を必ず読んでください。  
  
    -   ポリシー ファイルをダウンロードできます sqljdbc41.jar を使用して場合[Java Cryptography Extension (JCE) 無制限強度管轄ポリシーファイル 7 のダウンロード](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)  
  
    -   ポリシー ファイルをダウンロードできます sqljdbc42.jar を使用して場合[Java Cryptography Extension (JCE) 無制限強度管轄ポリシーファイル 8 のダウンロード](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)   
    
## <a name="enabling-always-encrypted-for-application-queries"></a>アプリケーション クエリで Always Encrypted を有効にする  
値を設定して、パラメーターの暗号化と暗号化された列をターゲットとするクエリ結果の暗号化解除を有効にする最も簡単な方法は、 **columnEncryptionSetting**接続文字列キーワードを**有効になっている**です。

JDBC ドライバーで Always Encrypted を有効にする接続文字列の例を次に示します。
  
```  
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;"; 
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
     
```  
  
また、SQLServerDataSource オブジェクトを使用して同等の例を次に示します。  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");  
SQLServerConnection con = (SQLServerConnection) ds.getConnection(); 
```    

Always Encrypted は、個々のクエリに対しても有効にすることができます。 参照してください、**を制御するパフォーマンスの影響の Always Encrypted**以下のセクションです。 暗号化または暗号化解除を正常に行うには、Always Encrypted だけでは不十分です。 次のことを確認する必要もあります。
- アプリケーションが、データベース内の Always Encrypted キーに関するメタデータへのアクセスに必要な *VIEW ANY COLUMN MASTER KEY DEFINITION* および *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* データベース権限を持っている。 詳細については、「Always Encrypted (データベース エンジン)」の「 [Permissions (権限)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7)」セクションを参照してください。
- アプリケーションが、列暗号化キーを保護する列マスター キーにアクセスでき、クエリされたデータベース列を暗号化する。 接続文字列に追加の資格情報を提供する必要があります。 Java キー ストア プロバイダーを使用することに注意してください。 参照してください**を使用する Java キー ストア プロバイダー**詳細についてはします。

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>サーバーに java.sql.Time 値を送信する方法を構成します。

**SendTimeAsDatetime** java.sql.Time 値をサーバーに送信する方法を構成する接続プロパティを使用します。 ときに sendTimeAsDatetime false、値が時間の SQL Server 型として送信されるとき、いつ sendTimeAsDatetime 値が datetime 型として送信されるとき、true を = です。 、Time 列が暗号化される場合、sendTimeAsDatetime プロパティいる必要があります false 暗号化された列は時刻から datetime への変換をサポートしていないために注意してください。 このプロパティは既定値は true で注もため、暗号化された列を使用する場合は、false に設定する必要があります。 それ以外の場合、ドライバーは、例外としてスローされます。 SQLServerConnection クラスでは、このプロパティの値をプログラムから構成するドライバーのバージョン 6.0 以降、次の 2 つの方法があります。
 
* public void setSendTimeAsDatetime (ブール sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

このプロパティの詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx)です。 

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>サーバーへの文字列値を送信する方法を構成します。

**SendStringParametersAsUnicode**接続プロパティを使用して、SQL Server への文字列値を送信する方法を構成します。 場合は"true"、文字列パラメーターに設定は、Unicode 形式でサーバーに送信されます。 場合は"false"、文字列パラメーターに設定は、Unicode ではなく ASCII/MBCS などの Unicode 以外の形式で送信されます。 このプロパティの既定値は"true"です。 Always Encrypted が有効になっているし、char/varchar/varchar(max) 列は暗号化されて、値の**sendStringParametersAsUnicode** (または既定のままにする) 場合に true に設定する必要があります。 このプロパティが false に設定されている場合は、暗号化された char/varchar/varchar(max) 列にデータを挿入するときに、Microsoft JDBC Driver for SQL Server は例外をスローします。 このプロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。 
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>暗号化された列のデータを取得および変更する

有効にした場合は常に暗号化アプリケーション クエリに対して、標準の JDBC Api を使用してを取得または暗号化されたデータベース列のデータを変更することができます。 暗号化された列から取得されたアプリケーションに必要なデータベース権限とアクセス、列マスター _ キーでは、Microsoft JDBC Driver for SQL Server は暗号化できます、暗号化された列をターゲットし、データを復号化は、任意のクエリ パラメーターを想定してSQL Server に対応する JDBC 型のプレーン テキスト値を返すデータ型は、データベース スキーマ内の列に対して設定します。
Always Encrypted が有効でない場合、暗号化された列をターゲットとするパラメーターを含むクエリは失敗します。 暗号化された列をターゲットとするパラメーターがクエリにない場合、クエリでは、暗号化された列からデータを取得できます。 ただし、Microsoft JDBC Driver for SQL Server は暗号化された列から取得された値を復号化を試行しません、アプリケーション (バイト配列) として暗号化されたバイナリのデータが表示されます。

次の表は、Always Encrypted が有効かどうかに応じたクエリの動作をまとめたものです。

|クエリの特性 | Always Encrypted が有効になっており、アプリケーションがキーとキー メタデータにアクセスできる|Always Encrypted が有効になっており、アプリケーションがキーまたはキー メタデータにアクセスできない | Always Encrypted が無効になっている|
|:---|:---|:---|:---|
| 暗号化された列をターゲットとするパラメーターを含むクエリ。 | パラメーター値は透過的に暗号化されます。 | [エラー] | [エラー]|
| 暗号化された列をターゲットとするパラメーターを含まず、暗号化された列からデータを取得するクエリ。| 暗号化された列の結果は透過的に暗号化解除されます。 アプリケーションでは、暗号化された列用に構成された SQL Server 型に対応する JDBC データ型のプレーン テキスト値を受け取ります。 | [エラー] | 暗号化された列の結果は暗号化解除されません。 アプリケーションは、暗号化された値をバイト配列 (byte[]) として受け取ります。
      
 
### <a name="inserting-and-retrieving-encrypted-data-examples"></a>挿入して、暗号化されたデータの例を取得します。 
次の例は、暗号化された列のデータを取得および変更する方法を示しています。 この例では、下のスキーマを含むターゲット テーブルを想定しています。 SSN 列と BirthDate 列が暗号化されていることに注意してください。

```
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1), 
 [SSN] [char](11) COLLATE Latin1_General_BIN2 
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL, 
 [BirthDate] [date] 
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```
 
### <a name="inserting-data-example"></a>データの挿入の例

この例では、Patients テーブルに列を挿入します。 次のことを考慮してください。
- このサンプル コードの暗号化に固有のものは何もありません。 Microsoft JDBC Driver for SQL Server は自動的に検出し、暗号化された列をターゲットとするパラメーターを暗号化します。 これにより、アプリケーションに対して暗号化が透過的に実行されます。 
- 暗号化された列を含め、データベース列に挿入された値は、SQLServerPreparedStatement を使用して、パラメーターとして渡されます。 (ただし、SQL インジェクションを防ぐのに役立つのでを強くお勧め) は、暗号化されていない列に値を送信するときは省略可能なパラメーターを使用して、ときに、暗号化された列をターゲットとする値に必要です。 暗号化された列に挿入された値が渡された場合、クエリ ステートメントに埋め込まれたリテラルとして、Microsoft JDBC Driver for SQL Server はありませんが、ターゲット暗号化された列の値を特定できないために、クエリは失敗値を暗号化します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。
- Microsoft JDBC Driver for SQL Server は暗号化された列から取得されたデータを透過的に暗号化解除と、プログラムによって印刷されるすべての値は、プレーン テキストになります。
- 実行する場合を使用して、参照句、WHERE 句で使用される値必要がある、パラメーターとして渡すことができるように、Microsoft JDBC Driver for SQL Server に透過的に暗号化をデータベースに送信する前にします。 次の例では、SSN は、パラメーターとして渡されますが、LastName が暗号化されていないと、LastName がリテラルとして渡されることを注意してください。
- SSN 列をターゲットとするパラメーターに使用する setter メソッドは、char/varchar SQL Server データ型にマップされる setString() です。 このパラメーターに使用する setter メソッドが、nchar/nvarchar にマップする setNString()、クエリは失敗、Always Encrypted は暗号化された nchar/nvarchar 値から暗号化された char/varchar 値への変換はサポートされていません。  

```
String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
try  
{           
     Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
     try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
     {                  
        String insertRecord="INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)";        
        try (PreparedStatement insertStatement = sourceConnection.prepareStatement(insertRecord))  
        {
            insertStatement.setString(1, "795-73-9838");  
            insertStatement.setString(2, "Catherine");   
            insertStatement.setString(3, "Abel");                   
            insertStatement.setDate(4, Date.valueOf("1996-09-10"));  
            insertStatement.executeUpdate();  
            System.out.println("1 record inserted.\n");  
        }         
     }  
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="retrieving-plaintext-data-example"></a>プレーンテキスト データの取得の例

次の例は、暗号化された値に基づいてデータをフィルター処理し、暗号化された列からプレーンテキスト データを取得する方法を示しています。 次のことを考慮してください。
- Microsoft JDBC Driver for SQL Server 暗号化できるように透過的にそのデータベースに送信する前に、パラメーターとして渡される SSN 列に対してフィルター処理する WHERE 句が必要で使用する値。
- Microsoft JDBC Driver for SQL Server は、SSN 列と BirthDate 列から取得されたデータを透過的に暗号化解除と、プログラムによって印刷されるすべての値は、プレーン テキストになります。

> [!NOTE]  
>  決定論的暗号化を使用して列が暗号化される場合、クエリは列に対して等価比較を実行できます。 詳細については、次を参照してください。、**を選択すると決定性またはランダム化された暗号化**のセクションで、 [Always Encrypted (データベース エンジン)](/sql-docs/docs/relational-databases/security/encryption/always-encrypted-database-engine)トピックです。  

```
String connectionString =  "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;" ;
String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;";  

try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "795-73-9838");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next()) 
    {  
    System.out.println("SSN: " +rs.getString("SSN") + 
    ", FirstName: " + rs.getString("FirstName") + 
    ", LastName:"+ rs.getString("LastName")+
     ", Date of Birth: " + rs.getString("BirthDate"));  
          }  
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>暗号化されたデータの取得の例

Always Encrypted が有効になっていない場合でも、暗号化された列をターゲットとするパラメーターがクエリになければ、クエリでは、暗号化された列からデータを取得できます。

次の例は、暗号化された列から暗号化されたバイナリ データを取得する方法を示しています。 次のことを考慮してください。

- 接続文字列で Always Encrypted が有効になっていないので、クエリは、SSN と BirthDate の暗号化された値をバイト配列として返します (プログラムによって値が文字列に変換されます)。
- Always Encrypted が無効の状態で、暗号化された列からデータを取得するクエリは、暗号化された列をターゲットとするパラメーターがない場合に限り、パラメーターを含むことができます。 上記のクエリは、データベースで暗号化されない LastName によってフィルター処理を行います。 クエリが SSN または BirthDate によってフィルター処理を行った場合、クエリは失敗します。

```
String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;"; 
 
try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "Abel");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next())
    {  
        System.out.println("SSN: " + rs.getString("SSN") +
         ", FirstName: " + rs.getString("FirstName") + 
        ", LastName:"+ rs.getString("LastName")+ 
        ", Date of Birth: " + rs.getString("BirthDate"));  
    } 
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>暗号化された列をクエリする際の一般的な問題を回避する

このセクションでは、Java アプリケーションおよびそれを回避する方法のガイドラインをいくつかの暗号化された列を照会するときに、エラーの一般的なカテゴリがについて説明します。

### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型変換エラー

Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 参照してください[Always Encrypted (データベース エンジン)](/sql-docs/docs/relational-databases/security/encryption/always-encrypted-database-engine)サポートされる型変換の詳細な一覧についてはします。 データ型の変換エラーを回避するには、次のことを確認してください。

- 値を渡す場合、暗号化された列をターゲットとするパラメーターのパラメーターの SQL Server データ型は、いずれかのように同じ対象列またはパラメーターの SQL Server データ型の変換の種類として、適切な setter メソッドを使用します。ターゲット列の型はサポートされています。 SQLServerPreparedStatement、SQLServerCallableStatement クラスおよび SQLServerResultSet クラス固有の SQL Server データ型に対応するパラメーターを渡すに API の新しいメソッドが追加されたことに注意してください。 たとえば、列が暗号化されていない場合は、パラメーターを渡す、datetime2、datetime 列 setTimestamp() メソッドを使用できます。 列が暗号化されている場合は、データベース内の列の型を表す、正確なメソッドを使用する必要があります。 たとえば、setTimestamp() を使用して、暗号化された datetime2 列に値を渡すし、暗号化された datetime 列に値を渡す setDateTime() を使用します。 参照してください[Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)の新しい Api の完全な一覧についてはします。 
- 10 進数と数値の SQL Server データ型の列をターゲットとするパラメーターの有効桁数と小数点以下桁数が、ターゲット列に対して構成された有効桁数と小数点と同じである。 SQLServerPreparedStatement、SQLServerCallableStatement クラスおよび SQLServerResultSet クラス有効桁数と小数点以下桁数の decimal および numeric データ型を表すパラメーター/列のデータ値と共にを受け入れるようにする API の新しいメソッドが追加されたことに注意してください。 参照してください[Always Encrypted API リファレンス、JDBC driver ](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) /オーバー ロードされた新しい Api の完全な一覧についてはします。  
- 対象列の値を変更するクエリで、ターゲット列に対してよりも、datetime2、datetimeoffset、または時刻の SQL Server データ型の列をターゲットとするパラメーターの秒の小数部桁数/小数点されません。 SQLServerPreparedStatement、SQLServerCallableStatement クラスおよび SQLServerResultSet クラスと共にこれらのデータ型を表すパラメーターのデータ値の秒の小数部の桁数/小数点を受け入れるようにする API の新しいメソッドが追加されたことに注意してください。 参照してください[Always Encrypted API リファレンス、JDBC driver ](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) /オーバー ロードされた新しい Api の完全な一覧についてはします。   

### <a name="errors-due-to-incorrect-connection-properties"></a>不適切な接続プロパティによるエラー
このセクションでは、Always Encrypted データを使用するには、正しく接続設定を構成する方法について説明します。 暗号化されたデータ型は、制限付きの変換をサポート、ため 'sendTimeAsDatetime' と 'sendStringParametersAsUnicode' の接続の設定では、暗号化された列の使用で、適切な構成が必要です。 次のことを確認してください。 
- [sendTimeAsDatetime](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx) time 列を暗号化データを挿入する場合、接続の設定が false に設定します。 詳細については、'サーバーに java.sql.Time 値を送信する方法の設定」セクションを参照してください。
- [sendStringParametersAsUnicode](../../connect/jdbc/setting-the-connection-properties.md)接続設定を true (または既定値は、そのまま) ときに、char/varchar/varchar(max) 列を暗号化するデータを挿入します。 詳細については、'、サーバーへの文字列値を送信する方法の設定」セクションを参照してください。

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値ではなくプレーン テキストを渡すことによるエラー

暗号化された列をターゲットとするすべての値は、アプリケーションの内部で暗号化される必要があります。 暗号化された列でプレーンテキスト値を挿入/変更したり、この値によってフィルター処理を行おうとすると、次のようなエラーになります。


```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

このようなエラーを防ぐには、次のことを確認してください。
- always Encrypted は暗号化された列 (接続文字列のまたは特定のクエリ) を対象とするアプリケーション クエリに対して有効にします。
- 準備されたステートメントを使用して、暗号化された列のデータのターゲットを送信するパラメーターです。 次の例では、不正なフィルター処理、暗号化された列 (SSN) でリテラル/定数によってパラメーターとしてリテラルの内側を渡す代わりにクエリを示しています。 このクエリは失敗します。

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");  
```

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアを操作する
パラメーター値の暗号化またはクエリ結果内のデータの暗号化を解除するには、Microsoft JDBC Driver for SQL Server は、ターゲット列に対して構成されている列暗号化キーを取得する必要があります。 列暗号化キーは、暗号化された形式でデータベースのメタデータに格納されます。 各列暗号化キーには、列暗号化キーの暗号化に使用された対応する列マスター キーが含まれます。 データベースのメタデータには、列マスター キーは格納されず、特定の列マスター キーとキー ストア内のキーの場所を含むキー ストアに関する情報のみが含まれます。

列暗号化キーのプレーン テキスト値を取得するには、Microsoft JDBC Driver for SQL Server 最初に関するメタデータを取得、列暗号化キーとその対応する列のマスター _ キーの両方とを使用し、情報、メタデータに、キーにお問い合わせください。を含む列マスター キー ストアと、暗号化された列暗号化キーを復号化します。 Microsoft JDBC Driver for SQL Server がから派生したクラスのインスタンスである – 列のマスター _ キーのストア プロバイダーを使用してキー ストアと通信する**SQLServerColumnEncryptionKeyStoreProvider**クラスです。


### <a name="using-built-in-column-master-key-store-providers"></a>組み込み列マスター キー ストア プロバイダーを使用する
  
Microsoft JDBC Driver for SQL Server は、次の組み込み列マスター キー ストア プロバイダーに付属します。 追加の資格情報または明示的な登録のいずれか必要とするもの (プロバイダーの検索に使用)、特定のプロバイダー名を事前登録されたこれらのプロバイダーの一部は、注意してください。

| クラス | 説明 | プロバイダー (検索) 名 |事前登録されているか。|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Azure Key Vault のキー ストアのプロバイダー。| AZURE_KEY_VAULT|不可|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Windows 証明書ストアのプロバイダー。|MSSQL_CERTIFICATE_STORE|はい
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Java キーストアのプロバイダー|MSSQL_JAVA_KEYSTORE|はい|

事前登録済みのキー ストア プロバイダーはこれらのプロバイダーを使用し、次に注意してくださいアプリケーション コード変更を加える必要はありません。

- ユーザー (またはデータベース管理者) は、列マスター キーのメタデータで構成されているプロバイダー名が正しいこと、および列マスター キー パスが、特定のプロバイダーに対して有効なキー パス形式に準拠していることを確認する必要があります。 CREATE COLUMN MASTER KEY (Transact-SQL) ステートメントを発行した際に有効なプロバイダー名とキー パスを自動的に生成する、SQL Server Management Studio などのツールを使用してキーを構成することをお勧めします。
- アプリケーションがキー ストア内のキーにアクセスできることを確認する必要があります。 これには、キーストアに応じてキーまたはキー ストアへのアクセスをアプリケーションに許可したり、その他のキー ストア固有の構成手順を実行するプロセスが含まれる場合があります。 たとえば、SQLServerColumnEncryptionJavaKeyStoreProvider を使用するためには、場所と接続プロパティのキー ストアのパスワードを入力する必要があります。 

すべてのこれらのキー ストア プロバイダーで詳しく説明します。
  
### <a name="using-azure-key-vault-provider"></a>Azure Key Vault Provider を使用する
Azure Key Vault は、特にアプリケーションが Azure でホストされている場合、Always Encrypted の列マスター キーの格納と管理に便利なオプションです。 Microsoft JDBC Driver for SQL Server では、組み込みのプロバイダー、SQLServerColumnEncryptionAzureKeyVaultProvider、Azure Key Vault に格納されたキーを持つアプリケーションに含まれます。 このプロバイダーの名前は、AZURE_KEY_VAULT です。 Azure Key Vault のストア プロバイダーを使用するために、アプリケーション開発者は Azure で資格情報コンテナーとキーを作成し、キーにアクセスするアプリケーションを構成する必要があります。 Key vault をセットアップして、列マスター _ キーを作成する方法の詳細についてを参照してください[Azure Key Vault – key vault を設定する方法の詳細については、ステップ バイ ステップ](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/)と[AzureKeyVaultで列マスター_キーの作成](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2).  
  
Azure Key Vault を使用するには、クライアント アプリケーションは、SQLServerColumnEncryptionAzureKeyVaultProvider をインスタンス化し、ドライバーに登録する必要があります。 インターフェイス経由でアプリケーションには、JDBC ドライバー デリゲート認証には、key vault からアクセス トークンを取得するためのメソッドを持つ SQLServerKeyVaultAuthenticationCallback が呼び出されます。 Azure Key Vault のストア プロバイダーのインスタンスを作成するアプリケーション開発者と呼ばれる唯一の方法の実装を提供する必要があります**getAccessToken** Azure Key Vault に格納されているキーのアクセス トークンを取得します。  
  
SQLServerKeyVaultAuthenticationCallback と SQLServerColumnEncryptionAzureKeyVaultProvider の初期化の例を次に示します。  
  
```  
// String variables clientID and clientSecret hold the client id and client secret values respectively.  
  
ExecutorService service = Executors.newFixedThreadPool(10);  
SQLServerKeyVaultAuthenticationCallback authenticationCallback = new SQLServerKeyVaultAuthenticationCallback() {  
       @Override  
    public String getAccessToken(String authority, String resource, String scope) {  
        AuthenticationResult result = null;  
        try{  
                AuthenticationContext context = new AuthenticationContext(authority, false, service);  
            ClientCredential cred = new ClientCredential(clientID, clientSecret);  
  
            Future<AuthenticationResult> future = context.acquireToken(resource, cred, null);  
            result = future.get();  
        }  
        catch(Exception e){  
            e.printStackTrace();  
        }  
        return result.getAccessToken();  
    }  
};  
  
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(authenticationCallback, service);  
  
```

SQL Server を使用するための Microsoft JDBC Driver 内でインスタンスを登録するアプリケーションに必要なアプリケーションでは、SQLServerColumnEncryptionAzureKeyVaultProvider のインスタンスが作成された後、SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドです。 強くお勧め、既定の参照名、SQLServerColumnEncryptionAzureKeyVaultProvider.getName() API を呼び出すことによって取得できる AZURE_KEY_VAULT を使用して、インスタンスを登録します。 既定の名前を使用して使用すると、プロビジョニングする SQL Server Management Studio や PowerShell などのツールを使用し、Always Encrypted のキー (ツールは、列マスター _ キーをメタデータ オブジェクトを生成する既定の名前を使用) を管理できます。 次の例で、Azure Key Vault provider の登録を示しています。 SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドの詳細については、次を参照してください。 [Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。 

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();   
keyStoreMap.put(akvProvider.getName(), akvProvider);   
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);   
```
  
> [!IMPORTANT]  
>  JDBC ドライバーの Azure Key Vault の実装 (GitHub) からこれらのライブラリに依存しています。  
>   
>  [azure sdk の java](https://github.com/Azure/azure-sdk-for-java)  
>   
>  [azure active directory-ライブラリ-用の java ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-java)  
  
### <a name="using-windows-certificate-store-provider"></a>Windows 証明書ストアのプロバイダーを使用します。
Windows 証明書ストアに列マスター_キーを格納する、SQLServerColumnEncryptionCertificateStoreProvider を使用できます。 列マスター_キーと列の暗号化キーの定義をデータベースに作成するのにには、SQL Server Management Studio (SSMS) は Always Encrypted ウィザードまたはサポートされている他のツールを使用します。 ある Windows 証明書ストアに自己署名証明書を生成する、同じウィザードを使用できます、常に暗号化されたデータの列マスター_キーとして使用します。 詳細については、列マスター_キーと列の暗号化キーの T-SQL 構文を参照してください[CREATE COLUMN MASTER KEY](/sql-docs/docs/t-sql/statements/create-column-master-key-transact-sql)と[CREATE COLUMN ENCRPTION KEY](/sql-docs/docs/t-sql/statements/create-column-encryption-key-transact-sql)それぞれします。

SQLServerColumnEncryptionCertificateStoreProvider の名前が"MSSQL_CERTIFICATE_STORE"、プロバイダー オブジェクトの getName() API によってクエリを実行できます。 ドライバーによって自動的に登録し、アプリケーションを変更せずにシームレスに使用されることができます。

> [!IMPORTANT]  
>  JDBC ドライバーの SQLServerColumnEncryptionCertificateStoreProvider 実装は Windows オペレーティング システムのみで使用可能と、ドライバー パッケージで使用できる sqljdbc_auth.dll に依存しています。  このプロバイダーを使用するには、JDBC ドライバーがインストールされているコンピューター上の Windows システム パス上のディレクトリに sqljdbc_auth.dll ファイルをコピーします。 または、java.libary.path システム プロパティを設定して sqljdbc_auth.dll のディレクトリを指定することもできます。 32 ビットの Java 仮想マシン (JVM) を実行している場合は、オペレーティング システムのバージョンが x64 であっても、x86 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 64 ビットの JVM を x64 プロセッサ上で実行している場合は、x64 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 たとえば、32 ビットの JVM を使用している既定のディレクトリに、JDBC ドライバーがインストールされている場合は、Java アプリケーションの起動時に次の仮想マシン (VM) 引数を使用して、DLL の場所を指定できます。  
`-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`
        
### <a name="using-java-key-store-provider"></a>Java キー ストア プロバイダーを使用します。  
JDBC ドライバーには組み込みキー ストア Java キー ストア プロバイダー実装します。 ドライバーは自動的にインスタンス化し、Java キーのストアのプロバイダーを登録、 **keyStoreAuthentication**接続文字列プロパティは、接続文字列内に存在し、"JavaKeyStorePassword"に設定されている (を参照してください詳細は下記)。 Java キー ストア プロバイダーの名前は、MSSQL_JAVA_KEYSTORE です。 この名前は、SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API によってもクエリを実行できます。 

宣言によって、ドライバーは Java キー ストアに認証が必要な資格情報を指定するクライアント アプリケーションを許可するのには、次の 3 つの新しい接続文字列キーワードが導入されました。 ドライバーの特定の接続、接続文字列の次の 3 つのプロパティの値に基づいて、プロバイダーの初期化とします。 
  
 **keyStoreAuthentication:**を使用するキー ストアを識別します。 Microsoft JDBC Driver 6.0 for SQL Server でこのプロパティを通してのみ Java キー ストアに認証できます。 Java キー ストアのこのプロパティの値は"JavaKeyStorePassword"をする必要があります。   
  
 **keyStoreLocation:**列マスター _ キーを格納する Java キーストア ファイルへのパス。 パスがキーストア ファイル名が含まれることに注意してください。  
  
 **keyStoreSecret:**キーストアをキーと同様に使用するシークレット/パスワードです。 Java キー ストアを使用するため、キーストアとキーのパスワード必要があります、同じであることに注意してください。  

接続文字列でこれらの資格情報を提供することを次に例を示します。

    String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
    
これらの設定には、SQLServerDataSource オブジェクトを使用して設定/取得することができます。 参照してください[Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)詳細についてはします。     
  
JDBC ドライバーでは、これらの資格情報が接続のプロパティに存在する場合、SQLServerColumnEncryptionJavaKeyStoreProvider が自動的にインスタンス化します。 
  
### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Java キー ストアの列のマスター _ キーを作成します。
SQLServerColumnEncryptionJavaKeyStoreProvider JKS または PKCS12 キーストアのタイプで使用できます。 このプロバイダーで使用するキーを作成またはインポートするには、Java を使用して[keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html)ユーティリティです。 キーストアをそれ自体と同じパスワード、キーを持っていることに注意してください。 公開キーと keytool ユーティリティを使用して関連付けられた秘密キーを作成する方法の例を次に示します。

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks    

このコマンドは、公開キーを作成し、自己署名証明書の関連する秘密キーと共に ' keystore.jks' キーストアに格納されます X.509 でラップします。 キーストア内のこのエントリは、エイリアス 'AlwaysEncryptedKey' によって識別されます。 

使用して、同じ PKCS12 storetype の例を次に示します。 

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword   

キーストアの場合は型 PKCS12 keytool ユーティリティは、キーのパスワードとキーのパスワードを要求していないことを SQLServerColumnEncryptionJavaKeyStoreProvider ある必要があります、キーストアと、キーと - keypass オプションで指定する必要があります、同じパスワードです。

.Pfx 形式で Windows 証明書ストアから証明書をエクスポートし、SQLServerColumnEncryptionJavaKeyStoreProvider で使用することもできます。 エクスポートした証明書は JKS キーストア型として Java キー ストアにインポートすることもできます。 

Keytool エントリを作成した後は、キー ストア プロバイダー名とキーのパスを必要があるデータベースで列マスター_キーのメタデータを作成する必要があります。 列マスター キー メタデータを作成する方法の詳細については、次を参照してください。 [CREATE COLUMN MASTER KEY](/sql-docs/docs/t-sql/statements/create-column-master-key-transact-sql)です。 SQLServerColumnEncryptionJavaKeyStoreProvider、キーのパスは、キーの別名だけです。 SQLServerColumnEncryptionJavaKeyStoreProvider の名前は 'MSSQL_JAVA_KEYSTORE' です。 SQLServerColumnEncryptionJavaKeyStoreProvider クラスの getName() パブリック API を使用してこの名前をクエリすることもできます。 

列マスター _ キーを作成するための T-SQL 構文です。

```  
CREATE COLUMN MASTER KEY [<CMK_name>]  
WITH  
(  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',  
    KEY_PATH = N'<key_alias>'  
)  
```  

に対して、'AlwaysEncryptedKey' 上記で作成された、列マスター_キー定義になります。

```  
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```  
    
> [!NOTE]  
>  組み込み SQL server management Studio 機能できません列マスター _ キーの定義を作成、Java キー ストアの T-SQL コマンドを使用する必要があります。  
  
### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Java キー ストアの列暗号化キーを作成します。
SQL Server management Studio またはその他のツールいないできることを Java キー ストアで列マスター_キーを使用して暗号化キー列を作成するに注意してください。 クライアント アプリケーションは、SQLServerColumnEncryptionJavaKeyStoreProvider クラスを使用してプログラムから、列暗号化キーを作成する必要があります。 詳細については、セクション 'を使用して列マスター キー ストア プロバイダーのプログラムによるキーのプロビジョニング' を参照してください。 

  
### <a name="implementing-a-custom-column-master-key-store-provider"></a>カスタム列マスター キー ストア プロバイダーを実装する
既存のプロバイダーでサポートされていないキー ストアで列マスター_キーを格納する場合は、SQLServerColumnEncryptionKeyStoreProvider クラスを拡張しを使用してプロバイダーを登録して、カスタム プロバイダーを実装することができます、SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドです。
  
```  
public class MyCustomKeyStore extends SQLServerColumnEncryptionKeyStoreProvider{  
    private String name = "MY_CUSTOM_KEYSTORE";
    
    public void setName(String name)
    {
        this.name = name;
    }
    
    public String getName()
    {
        return name;
    }

    public byte[] encryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)  
    {  
        // Logic for encrypting the column encryption key  
    }  
    
    public byte[] decryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)  
    {  
        // Logic for decrypting the column encryption key  
    }  
}  
  
```  
  
 プロバイダーを登録します。  
  
```  
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();  
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();  
keyStoreMap.put(storeProvider.getName(), storeProvider);  
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);  
  
```  
  
## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>プログラムによるキーのプロビジョニングに列マスター キー ストア プロバイダーを使用する

暗号化された列にアクセスするときに、Microsoft JDBC Driver for SQL Server は透過的に検索して、列暗号化キーの暗号化を解除するには、右側の列マスター _ キー ストア プロバイダーを呼び出します。 一般的に、通常のアプリケーション コードは列マスター キー ストア プロバイダーを直接呼び出しません。 ただし、プロバイダーを明示的にインスタンス化して呼び出し、プログラムを使用して Always Encrypted キーをプロビジョニングおよび管理することができます。これにより、(たとえば、一部の列マスター キーの回転として) 暗号化された列暗号化キーを生成したり、列暗号化キーを暗号化解除することができます。 詳細については、「 [Overview of Key Management for Always Encrypted](/sql-docs/docs/relational-databases/security/encryption/overview-of-key-management-for-always-encrypted)(Always Encrypted のキー管理の概要)」を参照してください。
カスタム キー ストア プロバイダーを使用する場合に限り、独自のキー管理ツールの実装が必要になることがあります。 Windows 証明書ストアまたは Azure Key Vault に格納されているキーを使用する場合は、管理およびキーをプロビジョニングする SQL Server Management Studio や PowerShell などの既存のツールを使用することができます。 Java キー ストアに格納されたキーを使用する場合は、キーをプログラムでプロビジョニングする必要があります。 次の例では、Java キー ストアに格納されているキーを使用してキーの暗号化に SQLServerColumnEncryptionJavaKeyStoreProvider クラスの使用を示しています。

```  
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programatically for the Java Key Store.
 */
public class AlwaysEncrypted
{
    // Alias of the key stored in the keystore.
    private static String keyAlias = "<proide key alias>";

    // Name by which the column master key will be known in the database.
    private static String columnMasterKeyName = "MyCMK";

    // Name by which the column encryption key will be known in the database.
    private static String columnEncryptionKey = "MyCEK";

    // The location of the keystore. 
    private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    // The password of the keystore and the key.
    private static char[] keyStoreSecret = "********".toCharArray();

    /**
     * Name of the encryption algorithm used to encrypt the value of
     * the column encryption key. The algorithm for the system providers must be RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args)
    {
        String connectionString = GetConnectionString();
        try
        {
            // Note: if you are not using try-with-resources statements (as here),
            // you must remember to call close() on any Connection, Statement,
            // ResultSet objects that you create.

            // Open a connection to the database.
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))
            {
                // Instantiate the Java Key Store provider.
                SQLServerColumnEncryptionKeyStoreProvider storeProvider = 
                        new SQLServerColumnEncryptionJavaKeyStoreProvider(
                                keyStoreLocation,
                                keyStoreSecret);

                byte [] encryptedCEK=getEncryptedCEK(storeProvider);

                /**
                 * Create column encryption key 
                 * For more details on the syntax refer: 
                 * https://msdn.microsoft.com/library/mt146372.aspx
                 * Encrypted column encryption key first needs to be converted into varbinary_literal from bytes, 
                 * for which DatatypeConverter.printHexBinary is used
                 */
                String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY " 
                        + columnEncryptionKey
                        + " WITH VALUES ( "
                        + " COLUMN_MASTER_KEY = " 
                        + columnMasterKeyName
                        + " , ALGORITHM =  '" 
                        + algorithm
                        + "' , ENCRYPTED_VALUE =  0x" 
                        + DatatypeConverter.printHexBinary(encryptedCEK)
                        + " ) ";

                try (Statement cekStatement = sourceConnection.createStatement())
                {
                    cekStatement.executeUpdate(createCEKSQL);
                    System.out.println("Column encryption key created with name : " + columnEncryptionKey);
                }
            }
        }
        catch (Exception e)
        {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    // To avoid storing the sourceConnection String in your code,
    // you can retrieve it from a configuration file.
    private static String GetConnectionString()
    {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +
                "databaseName=ae2;user=sa;password=********;";

        return connectionUrl;
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException
    {
        /**
         * Following arguments needed by  SQLServerColumnEncryptionJavaKeyStoreProvider
         * 1) keyStoreLocation : 
         *      Path where keystore is located, including the keystore file name. 
         * 2) keyStoreSecret : 
         *      Password of the keystore and the key.  
         */
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(
                keyAlias,
                algorithm,
                plainCEK);

        return encryptedCEK;
    }
}

```  
  
## <a name="force-encryption-on-input-parameters"></a>入力パラメーターで暗号化を強制します。
  
強制的に暗号化機能は、Always Encrypted を使用する場合に、パラメーターの暗号化を強制します。 強制的に暗号化が使用され、SQL Server パラメーターを暗号化する必要がないドライバーに通知をパラメーターを使用して、クエリは失敗します。 攻撃を受けた SQL Server がクライアントに不正な暗号化メタデータを提供すると、データ漏えいが引き起こされる可能性がありますが、このプロパティは、そのようなセキュリティ攻撃に対する保護を強化します。 SQLServerPreparedStatement クラスおよび SQLServerCallableStatement クラスおよび更新プログラムのセット * 方法\*強制暗号化設定を指定するブール型の引数を受け入れるように SQLServerResultSet クラスのメソッドはオーバー ロードします。 この引数の値が false の場合、ドライバーはパラメーターの暗号化を強制しません。 強制的に暗号化が設定されている場合は true、クエリにパラメーターはのみ送信先の列が暗号化され、接続またはステートメントでは、Always Encrypted が有効です。 これにより、データが誤ってに送られるようにない SQL Server プレーン テキストとしてを暗号化することが予想される場合、セキュリティの層を追加します。  
  
 強制暗号化設定ではオーバー ロード、SQLServerPreparedStatement、SQLServerCallableStatement のメソッドの詳細については、次を参照してください[Always Encrypted API リファレンス、JDBC driver。](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスの影響を制御する

Always Encrypted はクライアント側暗号化テクノロジであるため、ほとんどのパフォーマンス オーバーヘッドは、データベースではなくクライアント側で発生します。 暗号化および暗号化解除の操作のコストとは別に、クライアント側のパフォーマンス オーバーヘッドのその他の原因を次に示します。
- クエリ パラメーターのメタデータを取得するためのデータベースへの追加のラウンド トリップ。
- 列マスター キーにアクセスするための列マスター キー ストアの呼び出し。

このセクションでは、SQL Server とのパフォーマンスに上記の 2 つの要因の影響を制御する方法の Microsoft JDBC Driver で組み込みのパフォーマンスの最適化について説明します。

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>クエリ パラメーターのメタデータを取得するためのラウンド トリップを制御する

Always Encrypted が有効な場合、接続、既定では、Microsoft JDBC Driver for SQL Server が呼び出す[sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396)パラメーター化各クエリを渡す、クエリ ステートメント (必要はありませんパラメーターの値) を SQL Server。 [sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396)を調べるため、これらの各の返された場合、暗号化に関連することができる情報、Microsoft JDBC Driver for SQL Server およびすべてのパラメーターを暗号化する必要がある場合に、クエリ ステートメントの分析パラメーター値を暗号化します。 上記の動作により、クライアント アプリケーションに対する高度な透明性が確保されます。 アプリケーション (およびアプリケーション開発者) はパラメーターとして SQL Server の暗号化された列をターゲットとする値を Microsoft JDBC Driver に渡される限り、暗号化された列にアクセスするクエリを認識する必要はありません。


#### <a name="setting-always-encrypted-at-the-query-level"></a>クエリ レベルで Always Encrypted を設定する

パラメーター化クエリに対して暗号化メタデータを取得することによるパフォーマンスへの影響を制御するには、Always Encrypted を接続に対して設定する代わりに、個々のクエリに対して有効にします。 これにより、暗号化された列をターゲットとするパラメーターを含むことがわかっているクエリに対してのみ、sys.sp_describe_parameter_encryption が呼び出されるように設定できます。 ただし、これにより、暗号化の透明度が損なわれることに注意してください。データベース列の暗号化プロパティを変更する場合は、スキーマの変更に合わせてアプリケーション コードの変更が必要になる可能性があります。


個々 のクエリの Always Encrypted の動作を制御するにデータの送信し、受信した読み取りと書き込みを指定する SQLServerStatementColumnEncryptionSetting、列挙型を渡すことによって個々 のステートメント オブジェクトを構成する必要があります。その特定のステートメントに対して暗号化された列。 有用なガイドラインを次に示します。
- クライアントがデータベース接続を介して送信するほとんどのクエリが、暗号化された列をアクセスする場合:
    - ColumnEncryptionSetting 接続文字列キーワードが有効に設定します。
    - 暗号化された列にアクセスしない個々 のクエリの SQLServerStatementColumnEncryptionSetting.Disabled を設定します。 これにより、sys.sp_describe_parameter_encryption の呼び出しと、結果セット内の値を暗号化解除しようとする試みの両方が無効になります。
    - 暗号化を必要とするすべてのパラメーターはありませんが、暗号化された列からデータを取得する個々 のクエリの SQLServerStatementColumnEncryptionSetting.ResultSet を設定します。 これにより、sys.sp_describe_parameter_encryption の呼び出しと、パラメーター暗号化が無効になります。 クエリは、暗号化列の結果を暗号化解除できます。
- クライアントがデータベース接続を介して送信するほとんどのクエリが、暗号化された列をアクセスしない場合:
    - ColumnEncryptionSetting 接続文字列キーワードを無効に設定します。
    - 個々 のクエリに対して暗号化を必要とするパラメーターの SQLServerStatementColumnEncryptionSetting.Enabled を設定します。 これにより、sys.sp_describe_parameter_encryption の呼び出しと、暗号化された列から取得されたクエリ結果の暗号化解除の両方が有効になります。
    - 暗号化を必要とするすべてのパラメーターはありませんが、暗号化された列からデータを取得するクエリに対して SQLServerStatementColumnEncryptionSetting.ResultSet を設定します。 これにより、sys.sp_describe_parameter_encryption の呼び出しと、パラメーター暗号化が無効になります。 クエリは、暗号化列の結果を暗号化解除できます。

暗号化をバイパスし、プレーン テキスト データにアクセスする SQLServerStatementColumnEncryptionSetting 設定を使用できないことに注意してください。 ステートメントで列の暗号化を構成する方法の詳細については、次を参照してください。 [Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。  

次の例では、データベース接続に対して Always Encrypted が無効になっています。 アプリケーションが実行するクエリに、暗号化されていない LastName 列をターゲットとするパラメーターが含まれています。 このクエリは、どちらも暗号化されている SSN 列と BirthDate 列からデータを取得します。 このような場合、暗号化メタデータを取得するために sys.sp_describe_parameter_encryption を呼び出す必要ありません。 ただし、アプリケーションが 2 つの暗号化された列からプレーンテキスト値を受け取ることができるよう、クエリ結果の暗号化解除を有効にする必要があります。 SQLServerStatementColumnEncryptionSetting.ResultSet 設定を使用して、いることを確認しています。

```
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://localhost;databaseName=ae;user=sa;password=******;"
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=" + keyStoreLocation + ";"
        + "keyStoreSecret=******;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);

String filterRecord="SELECT FirstName, LastName, SSN, BirthDate FROM " + tblName + " WHERE LastName = ?";  
PreparedStatement selectStatement = connection.prepareStatement(
        filterRecord, 
        ResultSet.TYPE_FORWARD_ONLY, 
        ResultSet.CONCUR_READ_ONLY, 
        connection.getHoldability(), 
        SQLServerStatementColumnEncryptionSetting.ResultSetOnly);
selectStatement.setString(1, "Abel");  
ResultSet rs = selectStatement.executeQuery();  
while(rs.next()) {  
    System.out.println("First name: " + rs.getString("FirstName"));  
    System.out.println("Last name: " + rs.getString("LastName"));  
    System.out.println("SSN: " + rs.getString("SSN"));  
    System.out.println("Date of Birth: " + rs.getDate("BirthDate"));  
}  
rs.close();
selectStatement.close();
connection.close();
```


### <a name="column-encryption-key-caching"></a>列暗号化キーのキャッシュ

列暗号化キーの暗号化を解除するための列マスター キー ストアへの呼び出しの数を減らすためには、Microsoft JDBC Driver for SQL Server は、メモリ内には、プレーン テキスト列暗号化キーをキャッシュします。 暗号化された列暗号化キー値をデータベース メタデータから受け取った後、ドライバーは、暗号化されたキー値に対応するプレーンテキストの列暗号化キーをまず見つけようとします。 ドライバーは、暗号化された列暗号化キー値がキャッシュ内に見つからない場合にのみ、列マスター キーを含むキー ストアを呼び出します。

列暗号化キーのエントリの有効期間の値は、SQLServerConnection クラス setColumnEncryptionKeyCacheTtl()、API を使用して、キャッシュで構成できます。 キャッシュ内の列の暗号化キーのエントリの既定の有効期間値は、2 時間です。 オフにするにキャッシュ値 0 を使用します。 設定する値の有効期間を使用する次の API:
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
   
たとえば、10 分間の有効期間の値を設定するには、次のように使用します。
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)

時間の単位として日、時間、分または秒のみがサポートされていること、注意してください。  


## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>SQLServerBulkCopy を使用して暗号化されたデータのコピー

SQLServerBulkCopy、既に暗号化され、データの暗号化を解除せずに、別のテーブルの 1 つのテーブルに格納されているデータをコピーできます。 この手順は次のとおりです。

- ターゲット テーブルの暗号化構成が、ソース テーブルの構成と同じであることを確認します。 具体的には、両方のテーブルで同じ列が暗号化されており、同じ暗号化タイプおよび同じ暗号化キーを使用してこれらの列が暗号化されている必要があります。 注: いずれかのターゲット列が、対応するソース列と異なる方法で暗号化されている場合、コピー操作の後でターゲット テーブル内のデータを暗号化解除することはできません。 データは破損します。
- Always Encrypted を有効にせずに、ソース テーブルとターゲット テーブルへの両方のデータベース接続を構成します。 
- AllowEncryptedValueModifications オプションを設定します。 参照してください[JDBC ドライバーで一括コピーを使用して](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)詳細についてはします。
 
注: は、データが実際に暗号化されている場合、または同じの暗号化を使用して正しく暗号化されている場合、Microsoft JDBC Driver for SQL Server が参照しないため、データベースが破損する可能性が、AllowEncryptedValueModifications を指定するときに警告を使用します。型、アルゴリズムとキーが対象列とします。

## <a name="see-also"></a>参照  
 [Always Encrypted (Database Engine) (Always Encrypted (データベース エンジン))](/sql-docs/docs/relational-databases/security/encryption/always-encrypted-database-engine)  
  
  
