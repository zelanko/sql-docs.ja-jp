---
title: JDBC ドライバーで Always Encrypted の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 3/14/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88bcc472734964bc890f788d3878b6e1513f4ee4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>JDBC ドライバーで Always Encrypted の使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

このページを使用して Java アプリケーションを開発する方法の情報を提供する[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と Microsoft JDBC Driver 6.0 (またはそれ以降) for SQL Server。

Always Encrypted は、機密データを暗号化し、データまたは SQL Server または Azure SQL データベースに暗号化キーを開示することがなくクライアントを許可します。 Always Encrypted は SQL Server のドライバー、Microsoft JDBC Driver 6.0 など (またはそれ以上) を有効になっている、透過的に暗号化およびクライアント アプリケーション内の機密データを復号化することによってこの動作を実現します。 ドライバーによって、クエリを自動的に決定するパラメーターが Always Encrypted のデータベース列に対応しており、SQL Server または Azure SQL データベースに送信する前に、これらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。

## <a name="prerequisites"></a>前提条件
- Microsoft JDBC Driver の確認を行う 6.0 (またはそれ以降) for SQL Server が開発コンピューターにインストールされています。 
- Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files (JCE 管轄ポリシーファイル (無制限強度)) をダウンロードしてインストールします。  で考えられるエクスポート/インポート問題に関するインストール手順と関連する詳細の zip ファイルに含まれる Readme を参照してください。  

    - ポリシー ファイルをダウンロードできる場合は mssql jdbc-X.X.X.jre7.jar または sqljdbc41.jar を使用して、 [Java Cryptography Extension (JCE) 無制限強度管轄ポリシーファイル 7 のダウンロード](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)

    - ポリシー ファイルをダウンロードできる場合は mssql jdbc-X.X.X.jre8.jar または sqljdbc42.jar を使用して、 [Java Cryptography Extension (JCE) 無制限強度管轄ポリシーファイル 8 のダウンロード](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)

    - 場合は mssql jdbc X.X.X.jre9.jar を使用すると、ポリシー ファイル必要はありませんをダウンロードします。 Java 9 では、管轄ポリシーでは、無制限強度の暗号化が既定値です。

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアの操作
暗号化または暗号化された列のデータを復号化には、SQL Server は、列暗号化キーを保持します。 列暗号化キーは、暗号化された形式でデータベースのメタデータに格納されます。 各列暗号化キーは、列暗号化キーの暗号化に使用される対応する列マスター _ キーを持ちます。 データベースのメタデータでは、列のマスター _ キーは含まれません。 これらのキーは、クライアントでのみ保持されます。 ただし、データベースのメタデータに、クライアントの基準とした列のマスター _ キーを保存する場所に関する情報が含まれて。 たとえば、データベースのメタデータ可能性がありますというキーストアを保持する列マスター_キーが Windows 証明書ストアとの暗号化し、復号化に使用される特定の証明書が Windows 証明書ストア内の特定のパスであります。 クライアントでは、Windows 証明書ストアにその証明書へのアクセスが含まれる場合は、証明書を取得、できます。 証明書は、列暗号化キーを復号化に使用できます。 その暗号化キーを使用して、その列の暗号化キーを使用する暗号化された列のデータを暗号化または復号化することができます。

Microsoft JDBC Driver for SQL Server がから派生したクラスのインスタンスでは、列のマスター _ キーのストア プロバイダーを使用してキー ストアと通信する**SQLServerColumnEncryptionKeyStoreProvider**です。

### <a name="using-built-in-column-master-key-store-providers"></a>組み込み列マスター キー ストア プロバイダーを使用する
Microsoft JDBC Driver for SQL Server は、次の組み込み列マスター キー ストア プロバイダーに付属します。 (プロバイダーの検索に使用されている) 特定のプロバイダー名に事前登録されているこれらのプロバイダーの一部と、追加の資格情報または明示的な登録のいずれか必要とするものです。

| クラス | Description | プロバイダー (検索) 名 |事前登録されているか。|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Azure Key Vault のキー ストアのプロバイダー。| AZURE_KEY_VAULT|いいえ|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Windows 証明書ストアのプロバイダー。|MSSQL_CERTIFICATE_STORE|はい
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Java キーストアのプロバイダー|MSSQL_JAVA_KEYSTORE|はい|

事前登録済みのキー ストア プロバイダーでは、これらのプロバイダーを使用し、次の項目に注意してくださいアプリケーション コード変更を加える必要はありません。

- (または、DBA) 列マスター_キーのメタデータで構成されているプロバイダー名が正しいと列マスター_キーのパスを指定したプロバイダーに対して有効なキー パスの形式に準拠しているかどうかを確認する必要があります。 CREATE COLUMN MASTER KEY (TRANSACT-SQL) ステートメントを発行するときに、有効なプロバイダー名とキーのパスを自動的に生成する SQL Server Management Studio などのツールを使用してキーを構成することをお勧めします。
- アプリケーションは、キーストアにキーにアクセスできることを確認します。 このタスクは、アプリケーションのキーや、キーストアに応じて、キーストアへのアクセスを許可またはその他のキー ストア固有の構成手順を実行するにする必要があります。 たとえば、SQLServerColumnEncryptionJavaKeyStoreProvider を使用するため、場所と接続プロパティのキー ストアのパスワードを入力する必要があります。 

すべてのこれらのキー ストア プロバイダーは、次のセクションで詳しく説明します。 Always Encrypted を使用する 1 つのキー ストア プロバイダーを実装する必要があるだけです。

### <a name="using-azure-key-vault-provider"></a>Azure Key Vault プロバイダーを使用する
Azure Key Vault は、格納および (特に、アプリケーションが Azure でホストされている) 場合は、Always Encrypted の列マスター _ キーを管理する便利なオプションです。 Microsoft JDBC Driver for SQL Server では、組み込みプロバイダー、SQLServerColumnEncryptionAzureKeyVaultProvider、Azure Key Vault に格納されたキーを持つアプリケーションに含まれます。 このプロバイダーの名前は、AZURE_KEY_VAULT です。 Azure Key Vault のストア プロバイダーを使用するために、アプリケーション開発者は Azure Key Vault に資格情報コンテナーとキーを作成し、Azure Active Directory でアプリの登録を作成する必要があります。 登録済みのアプリケーションは、許可された権限を取得、復号化、暗号化、キーのラップを解除、キーのラップを確認してください Always Encrypted で使用するために作成した、key vault に対して定義されているアクセス ポリシーでなければなりません。 Key vault を設定し、列マスター _ キーを作成する方法の詳細については、次を参照してください。 [Azure Key Vault – ステップ バイ ステップ](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/)と[Azure Key Vault で列マスター_キーの作成](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault)です。

それらを再作成する T-SQL スクリプトに独自の特定の例のようになりますこのページで、Azure Key Vault を作成した場合の例は、ベースの列マスター_キーと SQL Server Management Studio を使用して列暗号化キー、 **KEY_パス**と**ENCRYPTED_VALUE**:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',
    KEY_PATH = N'https://<MyKeyValutName>.vault.azure.net:443/keys/Always-Encrypted-Auto1/c61f01860f37302457fa512bb7e7f4e8'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x01BA000001680074507400700073003A002F002F006400610076006...
)
```

Azure Key Vault を使用するには、クライアント アプリケーションは、SQLServerColumnEncryptionAzureKeyVaultProvider をインスタンス化し、ドライバーに登録する必要があります。

SQLServerColumnEncryptionAzureKeyVaultProvider の初期化の例を次に示します。  

```
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID**アプリの登録の Azure Active Directory インスタンス内のアプリケーション id を指定します。 **clientKey**キーのパスワードがそのアプリケーションは、API のアクセスは、Azure Key Vault で登録されています。

アプリケーションでは、SQLServerColumnEncryptionAzureKeyVaultProvider のインスタンスが作成された後、アプリケーションは、SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドを使用して、ドライバーでインスタンスを登録する必要があります。 既定の参照名、SQLServerColumnEncryptionAzureKeyVaultProvider.getName() API を呼び出すことによって取得できる AZURE_KEY_VAULT を使用して、インスタンスが登録されているを強くお勧めします。 既定の名前を使用して使用すると、プロビジョニングや Always Encrypted のキー (ツールは、列マスター _ キーをメタデータ オブジェクトを生成する既定の名前を使用) を管理する SQL Server Management Studio や PowerShell などのツールを使用できます。 次の例では、Azure Key Vault のプロバイダーの登録を示します。 SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドの詳細については、次を参照してください。 [Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Azure Key Vault のキー ストア プロバイダーを使用する場合、JDBC ドライバーの Azure Key Vault の実装をアプリケーションに含める必要があります (GitHub) からのこれらのライブラリに依存しています。
>
>  [azure-sdk-for-java](https://github.com/Azure/azure-sdk-for-java)
>
>  [azure-activedirectory-library-for-java libraries](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Maven プロジェクトでこれらの依存関係を含める方法の例は、次を参照してください[ダウンロード ADAL4J と AKV 依存関係の Apache Maven。](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>Windows 証明書ストアのプロバイダーを使用します。
Windows 証明書ストアに列マスター_キーを格納する、SQLServerColumnEncryptionCertificateStoreProvider を使用できます。 列マスター_キーと列の暗号化キーの定義をデータベースに作成するのにには、SQL Server Management Studio (SSMS) は Always Encrypted ウィザードまたはサポートされている他のツールを使用します。 常に暗号化されたデータの列マスター_キーとして使用できる Windows 証明書ストアに自己署名証明書を生成するのには、同じウィザードを使用できます。 列マスター_キーと列暗号化キー T-SQL 構文の詳細については、次を参照してください。 [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)と[CREATE COLUMN ENCRPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md)それぞれします。

SQLServerColumnEncryptionCertificateStoreProvider の名前は、MSSQL_CERTIFICATE_STORE でプロバイダー オブジェクトの getName() API によってクエリを実行できます。 ドライバーによって自動的に登録し、アプリケーションを変更せずにシームレスに使用されることができます。

再作成する T-SQL スクリプトに、固有の例のようになりますこのページで、Windows証明書ストアを作成した場合の例は、ベースの列マスター_キーとSQLServerManagementStudioを使用して列暗号化キー、**KEY_PATH**と**ENCRYPTED_VALUE**:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/My/A2A91F59C461B559E4D962DA9D2BC6131B32CB91'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E0074007500730065007200...
)
```

> [!IMPORTANT]
> この記事で他のキー ストア プロバイダーは、ドライバーでサポートされているすべてのプラットフォームで使用できますが、JDBC ドライバーの SQLServerColumnEncryptionCertificateStoreProvider 実装は Windows オペレーティング システムでのみ使用可能なです。 ドライバー パッケージで使用できる sqljdbc_auth.dll に依存していること。 このプロバイダーを使用するには、JDBC ドライバーがインストールされているコンピューター上の Windows システム パス上のディレクトリに sqljdbc_auth.dll ファイルをコピーします。 または、java.libary.path システム プロパティを設定して sqljdbc_auth.dll のディレクトリを指定することもできます。 32 ビットの Java 仮想マシン (JVM) を実行している場合は、オペレーティング システムのバージョンが x64 であっても、x86 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 64 ビットの JVM を x64 プロセッサ上で実行している場合は、x64 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 たとえば、32 ビットの JVM を使用している既定のディレクトリに、JDBC ドライバーがインストールされている場合は、Java アプリケーションの起動時に次の仮想マシン (VM) 引数を使用して、DLL の場所を指定できます。 `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>Java キー ストア プロバイダーを使用します。
JDBC driver Java キー ストアの組み込みキー ストア プロバイダー実装が付属します。 場合、 **keyStoreAuthentication**接続文字列プロパティが接続文字列内に存在、"JavaKeyStorePassword"に設定されていると、ドライバーは自動的にインスタンス化し、Java キー ストアのプロバイダーを登録します。 Java キー ストア プロバイダーの名前は、MSSQL_JAVA_KEYSTORE です。 この名前は、SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API を使用してもクエリを実行できます。 

Java キー ストアへの認証に、ドライバーが必要な資格情報を指定するクライアント アプリケーションを許可する 3 つの接続文字列プロパティがあります。 ドライバーでは、これら 3 つの接続文字列プロパティの値に基づいて、プロバイダーを初期化します。

**keyStoreAuthentication:** を使用する Java キー ストアを識別します。 Microsoft JDBC Driver for SQL Server 6.0 以降を Java キー ストアにこのプロパティを通してのみ認証できます。 Java キー ストアのこのプロパティの値がある必要があります`JavaKeyStorePassword`です。

**keyStoreLocation:** 列マスター _ キーを格納する Java キーストア ファイルへのパス。 パスには、キーストア ファイル名が含まれています。

**keyStoreSecret:** キーストアをキーと同様に使用するシークレット/パスワードです。 Java キー ストアを使用するため、キーストアとキーのパスワードでなければなりません。

接続文字列でこれらの資格情報を提供する例を次に示します。

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

取得または SQLServerDataSource オブジェクトを使用してこれらの設定を設定することもできます。 詳細については、次を参照してください。 [Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。

JDBC ドライバーでは、これらの資格情報が接続のプロパティに存在する場合、SQLServerColumnEncryptionJavaKeyStoreProvider が自動的にインスタンス化します。

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Java キー ストアの列マスター_キーを作成します。
SQLServerColumnEncryptionJavaKeyStoreProvider JKS または PKCS12 キーストアのタイプで使用できます。 このプロバイダーで使用するキーを作成またはインポートするには、Java を使用して[keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html)ユーティリティです。 キーストアをそれ自体と同じパスワード、キーが必要です。 公開キーと keytool ユーティリティを使用して関連付けられた秘密キーを作成する方法の例を次に示します。

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

このコマンドは、公開キーを作成し、それに関連付けられた秘密キーと共に ' keystore.jks' キーストアに格納されている証明書の自己署名 X.509 でラップします。 キーストア内のこのエントリは、エイリアス 'AlwaysEncryptedKey' によって識別されます。

次に、同じ型を使用して、PKCS12 ストアの例を示します。

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

キーストアを PKCS12 型の場合は、keytool ユーティリティは、キーのパスワードを要求していないと、キーのパスワードを SQLServerColumnEncryptionJavaKeyStoreProvider ある必要があります、キーストアと、キーと同じように-keypass オプションで指定する必要があります。パスワードです。

.Pfx 形式で Windows 証明書ストアから証明書をエクスポートし、SQLServerColumnEncryptionJavaKeyStoreProvider で使用することもできます。 エクスポートした証明書は JKS キーストア型として Java キー ストアにインポートすることもできます。

Keytool エントリを作成した後で、データベースでは、キー ストア プロバイダー名とキーのパスが必要な列マスター キー メタデータを作成します。 列マスター_キーのメタデータを作成する方法の詳細については、次を参照してください。 [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)です。 SQLServerColumnEncryptionJavaKeyStoreProvider のキーのパスは、キーのエイリアス名だけであり、SQLServerColumnEncryptionJavaKeyStoreProvider の名前 'MSSQL_JAVA_KEYSTORE'。 SQLServerColumnEncryptionJavaKeyStoreProvider クラスの getName() パブリック API を使用してこの名前をクエリすることもできます。 

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
> 組み込みの SQL Server management Studio の機能は、Java キー ストアの列マスター _ キーの定義を作成できません。 T-SQL コマンドをプログラムで使用する必要があります。

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Java キー ストアの列暗号化キーを作成します。
Java キー ストア内の列マスター _ キーを使用して暗号化キーの列を作成するのには、SQL Server Management Studio またはその他のツールを使用できません。 クライアント アプリケーションは、SQLServerColumnEncryptionJavaKeyStoreProvider クラスを使用してプログラムから、列暗号化キーを作成する必要があります。 詳細については、次を参照してください。[列マスター キー ストア プロバイダーを使用して、プログラムによるキーのプロビジョニングの](#using-column-master-key-store-providers-for-programmatic-key-provisioning)します。

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
暗号化された列にアクセスするときに、Microsoft JDBC Driver for SQL Server は透過的に検索して、列暗号化キーの暗号化を解除するには、右側の列マスター _ キー ストア プロバイダーを呼び出します。 一般的に、通常のアプリケーション コードは列マスター キー ストア プロバイダーを直接呼び出しません。 ただし、インスタンスを作成してプロビジョニングや Always Encrypted キーを管理するプログラムでプロバイダーに連絡することができます。 この手順は、暗号化された列暗号化キーを生成およびなど一部の列マスター_キーの回転として列の暗号化キーを復号化を行うことがあります。 詳細については、「 [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Always Encrypted のキー管理の概要)」を参照してください。

カスタム キー ストア プロバイダーを使用する場合、独自のキー管理ツールを実装する必要があります。 Windows 証明書ストアまたは Azure Key Vault に格納されているキーを使用する場合は、管理およびキーをプロビジョニングする SQL Server Management Studio や PowerShell などの既存のツールを使用することができます。 Java キー ストアに格納されたキーを使用する場合は、キーをプログラムでプロビジョニングする必要があります。 次の例では、Java キー ストアに格納されているキーを使用してキーの暗号化に SQLServerColumnEncryptionJavaKeyStoreProvider クラスを使用してを示します。

```
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
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
                 * For more details on the syntax, see:
                 * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql
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
         * Following arguments needed by SQLServerColumnEncryptionJavaKeyStoreProvider
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

## <a name="enabling-always-encrypted-for-application-queries"></a>アプリケーション クエリで Always Encrypted を有効にする
パラメーターの暗号化と暗号化された列をターゲットとするクエリ結果の暗号化解除を有効にする最も簡単な方法は、の値を設定して、 **columnEncryptionSetting**接続文字列キーワードを**有効**.

次の接続文字列は、JDBC ドライバーで Always Encrypted を有効にする例を示します。

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
```

次のコードは、SQLServerDataSource オブジェクトを使用して同等の例を示します。

```
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Always Encrypted は、個々のクエリに対しても有効にすることができます。 詳細については、次を参照してください。 [Always Encrypted のパフォーマンスに与える影響を制御する](#controlling-the-performance-impact-of-always-encrypted)です。 Always Encrypted を有効にするでは、暗号化または暗号化解除を成功させるのには満たされません。 次のことを確認する必要もあります。
- アプリケーションが、データベース内の Always Encrypted キーに関するメタデータへのアクセスに必要な *VIEW ANY COLUMN MASTER KEY DEFINITION* および *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* データベース権限を持っている。 詳細については、「 [Always Encrypted (データベース エンジン) のアクセス許可](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions)です。
- アプリケーションは、クエリされたデータベース列の暗号化、列暗号化キーを保護する列マスター _ キーにアクセスできます。 Java キー ストア プロバイダーを使用するのには、接続文字列に追加の資格情報を提供する必要があります。 詳細については、次を参照してください。[を使用する Java キー ストア プロバイダー](#using-java-key-store-provider)です。

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>サーバーに java.sql.Time 値を送信する方法を構成します。
**SendTimeAsDatetime** java.sql.Time 値をサーバーに送信する方法を構成する接続プロパティを使用します。 時刻の値は false に設定すると、SQL Server 時の型として送信されます。 True、値が datetime 型として送信されるときに設定するとします。 Time 列が暗号化されている場合、 **sendTimeAsDatetime**暗号化された列は時刻から datetime への変換をサポートしていないために、プロパティが false に設定する必要があります。 このプロパティは既定値は true、によってがあるため、暗号化された列を使用する場合は、false に設定する必要にも注意してください。 それ以外の場合、ドライバーでは、例外をスローします。 プログラムからこのプロパティの値を構成する 2 つのメソッドを SQLServerConnection クラスは、ドライバーのバージョン 6.0 以降、あります。
 
* public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

このプロパティの詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>サーバーへの文字列値を送信する方法を構成します。
**SendStringParametersAsUnicode**接続プロパティを使用して、SQL Server への文字列値を送信する方法を構成します。 場合は true の場合、文字列パラメーターに設定は、Unicode 形式でサーバーに送信されます。 場合は false の場合、文字列パラメーターに設定は、ASCII または Unicode ではなく、MBCS などの Unicode 以外の形式で送信されます。 このプロパティの既定値は true です。 Always Encrypted が有効になっているし、char/varchar/varchar(max) 列は暗号化されて、値の**sendStringParametersAsUnicode** false に設定する必要があります。 このプロパティ設定されている場合は true、ドライバーは例外をスロー Unicode 文字が含まれている暗号化された char/varchar/varchar(max) 列からデータを復号化するときにします。 このプロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>取得して、暗号化された列のデータの変更
有効にした場合は常に暗号化アプリケーション クエリに対して、標準の JDBC Api を使用してを取得または暗号化されたデータベース列のデータを変更することができます。 アプリケーションが必要なデータベース権限を持って、列マスター_キーにアクセスできる場合、ドライバーは暗号化された列をターゲットし、は、暗号化された列から取得されるデータを復号化するすべてのクエリ パラメーターを暗号化します。

Always Encrypted が有効でない場合、暗号化された列をターゲットとするパラメーターを含むクエリは失敗します。 クエリ データを取得できます暗号化された列から、クエリには、暗号化された列をターゲットとするパラメーターがあるない限り、します。 ただし、ドライバーは暗号化された列から取得された値を復号化を試行しません、アプリケーション (バイト配列) として暗号化されたバイナリのデータが表示されます。

次の表は、Always Encrypted が有効かどうかに応じてクエリの動作をまとめたものです。

|クエリの特性 | Always Encrypted が有効になっており、アプリケーションがキーとキー メタデータにアクセスできる|Always Encrypted が有効になっており、アプリケーションがキーまたはキー メタデータにアクセスできない | Always Encrypted が無効になっている|
|:---|:---|:---|:---|
| 暗号化された列をターゲットとするパラメーターを含むクエリ。 | パラメーター値は透過的に暗号化されます。 | [エラー] | [エラー]|
| 暗号化された列をターゲットとするパラメーターなしの暗号化された列からデータを取得するクエリ。| 暗号化された列の結果は透過的に暗号化解除されます。 アプリケーションでは、暗号化された列用に構成された SQL Server 型に対応する JDBC データ型のプレーン テキスト値を受け取ります。 | [エラー] | 暗号化された列の結果は暗号化解除されません。 アプリケーションは、暗号化された値をバイト配列 (byte[]) として受け取ります。

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>挿入して、暗号化されたデータの例を取得します。 
次の例は、暗号化された列のデータを取得および変更する方法を示しています。 例では、次のスキーマと SSN と BirthDate の暗号化された列を持つ対象のテーブルと仮定します。 という名前の列マスター _ キーを構成してある場合は、"MyCMK"と列の暗号化キーという"MyCEK"(前のキー ストア プロバイダーのセクションで説明) に従って、このスクリプトを使用してテーブルを作成することができます。

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

各 Java のコード例で説明した場所にキー ストア固有のコードを挿入する必要があります。

Azure Key Vault キー ストア プロバイダー。 使用する場合

```
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

Windows 証明書ストアのキー ストア プロバイダー。 使用する場合

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

Java キー ストアのキー ストア プロバイダー。 使用する場合

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>データの挿入の例
この例では、Patients テーブルに列を挿入します。 次の項目に注意してください。
- このサンプル コードの暗号化に固有のものは何もありません。 Microsoft JDBC Driver for SQL Server は自動的に検出し、暗号化された列をターゲットとするパラメーターを暗号化します。 この動作では、アプリケーションに対して透過的な暗号化を行います。
- 暗号化された列を含め、データベース列に挿入された値は、SQLServerPreparedStatement を使用して、パラメーターとして渡されます。 (ただし、SQL インジェクションを防ぐのに役立つのでを強くお勧め) は、暗号化されていない列に値を送信するときは省略可能なパラメーターを使用して、ときに、暗号化された列をターゲットとする値に必要です。 暗号化された列に挿入された値は、クエリ ステートメントに埋め込まれたリテラルとして渡された、ドライバーは暗号化された列の値を決定できないし、値が暗号化されることはできませんので、クエリは失敗します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。
- Microsoft JDBC Driver for SQL Server は暗号化された列から取得されたデータを透過的に暗号化解除と、プログラムによって印刷されるすべての値は、プレーン テキストになります。
- いる場合は、WHERE 句、ドライバーを透過的に暗号化して、データベースに送信する前にするようにパラメーターとして渡される WHERE 句が必要で使用される値を使用して検索します。 次の例では、SSN はパラメーターとして渡されますが、LastName が暗号化されていないと、LastName はリテラルとして渡されます。
- SSN 列をターゲットとするパラメーターに使用する setter メソッドは、char/varchar SQL Server データ型にマップされる setString() です。 このパラメーターに使用する setter メソッドが、nchar/nvarchar にマップする setNString()、クエリは失敗、Always Encrypted は暗号化された nchar/nvarchar 値から暗号化された char/varchar 値への変換はサポートされていません。

```
try
{
    <Insert keystore-specific code here>

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

### <a name="retrieving-plaintext-data-example"></a>プレーン テキスト データの取得の例
次の例では、暗号化された値と暗号化された列からプレーン テキスト データの取得に基づくデータのフィルター処理を示します。 次の項目に注意してください。
- Microsoft JDBC Driver for SQL Server 暗号化できるように透過的にそのデータベースに送信する前に、パラメーターとして渡される、WHERE 句を SSN 列に対してフィルター処理する必要がありますで使用される値。
- Microsoft JDBC Driver for SQL Server は、SSN 列と BirthDate 列から取得されたデータを透過的に暗号化解除と、プログラムによって印刷されるすべての値は、プレーン テキストになります。

> [!NOTE]
> 列が決定的な暗号化を使用して暗号化されている場合、クエリは、それらの等値比較を実行できます。 詳細については、次を参照してください。[で Always Encrypted (データベース エンジン) を選択すると決定性またはランダム化された暗号化](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption)です。

```
try
{
    <Insert keystore-specific code here>

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    try (Connection sourceConnection = DriverManager.getConnection(connectionString))
    {
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
    }
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>暗号化されたデータの取得例
Always Encrypted が有効になっていない場合でも、暗号化された列をターゲットとするパラメーターがクエリになければ、クエリでは、暗号化された列からデータを取得できます。

次の例では、暗号化された列から暗号化されたバイナリ データの取得を示します。 次の項目に注意してください。
- Always Encrypted が有効でないため、接続文字列に、クエリは (プログラムは、値を文字列に変換されます) のバイト配列として SSN と BirthDate の暗号化された値を返します。
- Always Encrypted が無効の状態で、暗号化された列からデータを取得するクエリは、暗号化された列をターゲットとするパラメーターがない場合に限り、パラメーターを含むことができます。 データベースは暗号化されない LastName によって次のクエリのフィルター。 クエリが SSN または BirthDate によってフィルター処理を行った場合、クエリは失敗します。

```
try
{
    String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    try (Connection sourceConnection = DriverManager.getConnection(connectionString))
    {
        String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;";

        try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))
        {
            selectStatement.setString(1, "Abel");
            ResultSet rs = selectStatement.executeQuery();
            while (rs.next())
            {
                System.out.println("SSN: " + rs.getString("SSN") +
                    ", FirstName: " + rs.getString("FirstName") +
                    ", LastName:"+ rs.getString("LastName") +
                    ", Date of Birth: " + rs.getString("BirthDate"));
            }
        }
    }
}
catch (Exception e)
{
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>暗号化された列をクエリする際の一般的な問題を回避する
このセクションでは、Java アプリケーションおよびそれを回避する方法のガイドラインをいくつかの暗号化された列を照会するときに、エラーの一般的なカテゴリがについて説明します。

### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型の変換エラー
Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 参照してください[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)サポートされる型変換の詳細な一覧についてはします。 ここでは、データ型変換エラーを避けるために行うことができます。 次のことを確認してください。

- 暗号化された列をターゲットとするパラメーターの値を渡す場合は、適切な setter メソッドを使用します。 パラメーターの SQL Server データ型は、対象列の型と同じでは正確に、SQL Server データ型のパラメーターの列のターゲット型への変換はサポートされていることを確認します。 API のメソッドは、特定の SQL Server データ型に対応するパラメーターを渡す、SQLServerPreparedStatement、SQLServerCallableStatement、および SQLServerResultSet クラスに追加されました。 たとえば、列が暗号化されていない場合、datetime2、datetime 型の列、パラメーターを渡す setTimestamp() メソッドを使用することができます。 列が暗号化されている場合は、データベース内の列の型を表す、正確なメソッドを使用する必要があります。 たとえば、setTimestamp() を使用して、暗号化された datetime2 列に値を渡すし、暗号化された datetime 列に値を渡す setDateTime() を使用します。 参照してください[Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)の新しい Api の完全な一覧についてはします。
- 10 進数と数値の SQL Server データ型の列をターゲットとするパラメーターの有効桁数と小数点以下桁数が、ターゲット列に対して構成された有効桁数と小数点と同じである。 API のメソッドは、有効桁数と小数点以下桁数の decimal および numeric データ型を表すパラメーター/列のデータ値と共にを受け入れるように、SQLServerPreparedStatement、SQLServerCallableStatement、および SQLServerResultSet クラスに追加されました。 参照してください[Always Encrypted API リファレンス、JDBC driver ](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) /オーバー ロードされた新しい Api の完全な一覧についてはします。  
- datetime2、datetimeoffset、または時刻の SQL Server データ型の列をターゲットとするパラメーターの秒の小数部桁数/小数点が対象列の値を変更するクエリ内のターゲット列の秒の小数部桁数/小数点より大きい. API のメソッドは、秒の小数部桁数/小数点と共にこれらのデータ型を表すパラメーターのデータ値を受け入れるように、SQLServerPreparedStatement、SQLServerCallableStatement、および SQLServerResultSet クラスに追加されました。 新しい/オーバー ロードされた Api の完全な一覧を参照してください。 [Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。   

### <a name="errors-due-to-incorrect-connection-properties"></a>不適切な接続プロパティによるエラー
このセクションでは、Always Encrypted データを使用するには、正しく接続設定を構成する方法について説明します。 暗号化されたデータの種類、制限付きの変換をサポートするため、 **sendTimeAsDatetime**と**sendStringParametersAsUnicode**接続設定は、暗号化された列を使用する場合、適切な構成を必要があります。 次のことを確認してください。 
- [sendTimeAsDatetime](setting-the-connection-properties.md) time 列を暗号化データを挿入する場合、接続の設定が false に設定します。 詳細については、次を参照してください。[サーバーに java.sql.Time 値を送信する方法を構成する](configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。
- [sendStringParametersAsUnicode](setting-the-connection-properties.md)接続設定を true (または既定値は、そのまま) ときに、char/varchar/varchar(max) 列を暗号化するデータを挿入します。

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値の代わりにプレーンテキストを渡すことによるエラー
暗号化された列をターゲットとするすべての値は、アプリケーションの内部で暗号化される必要があります。 挿入または変更するか、暗号化された列でプレーン テキスト値でフィルター処理しようとすると、このようなエラーが発生します。

```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

このようなエラーを防ぐには、次のことを確認してください。
- always Encrypted は暗号化された列 (接続文字列のまたは特定のクエリ) を対象とするアプリケーション クエリに対して有効にします。
- 準備されたステートメントを使用して、暗号化された列のデータのターゲットを送信するパラメーターです。 次の例は、不正なフィルター処理、暗号化された列 (SSN) でリテラル/定数によって内のリテラルをパラメーターとして渡すのではなく、クエリを示しています。 このクエリは失敗します。

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>入力パラメーターで暗号化を強制します。
強制的に暗号化機能は、Always Encrypted を使用する場合に、パラメーターの暗号化を強制します。 強制的に暗号化が使用され、SQL Server パラメーターを暗号化する必要がないドライバーに通知をパラメーターを使用して、クエリは失敗します。 攻撃を受けた SQL Server がクライアントに不正な暗号化メタデータを提供すると、データ漏えいが引き起こされる可能性がありますが、このプロパティは、そのようなセキュリティ攻撃に対する保護を強化します。 セット * メソッドを SQLServerPreparedStatement クラスおよび SQLServerCallableStatement クラスおよび更新プログラムで\*強制暗号化設定を指定するブール型の引数を受け入れるように SQLServerResultSet クラスのメソッドはオーバー ロードします。 この引数の値が false の場合、ドライバーはパラメーターの暗号化を強制しません。 強制的に暗号化が設定されている場合は、true、クエリにパラメーターが場合にのみ送信先の列が暗号化され、接続またはステートメントでは、Always Encrypted が有効です。 このプロパティを使用すると、セキュリティを確保すること、ドライバーは誤ってデータを送信しない SQL Server プレーン テキストとしてを暗号化することが予想される場合の層を追加します。

強制暗号化設定ではオーバー ロード、SQLServerPreparedStatement、SQLServerCallableStatement のメソッドの詳細については、次を参照してください[Always Encrypted API リファレンス、JDBC driver。](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスに与える影響を制御します。
常に暗号化がクライアント側暗号化テクノロジであるため、データベースではなく、クライアント側でほとんどのパフォーマンスのオーバーヘッドが発生します。 別の暗号化と復号化の操作のコストは、クライアント側のパフォーマンス オーバーヘッドの他のソースがあります。
- クエリ パラメーターのメタデータを取得するためのデータベースへの追加のラウンド トリップ。
- 列マスター キーにアクセスするための列マスター キー ストアの呼び出し。

このセクションでは、SQL Server のパフォーマンスに上記の 2 つの要因の影響を制御する方法を Microsoft JDBC Driver で組み込みのパフォーマンスの最適化について説明します。

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>クエリ パラメーターのメタデータを取得するためのラウンド トリップを制御する
接続に対して Always Encrypted が有効になっている場合は、既定では、ドライバーが呼び出す[sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)パラメーター化各クエリのクエリ ステートメント (パラメーター値) を除く SQL Server を渡します。 [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)を調べるには、パラメーターを暗号化する必要がある場合と、その各それがパラメーター値を暗号化するドライバーを許可する、暗号化関連の情報を返します、クエリ ステートメントを分析します。 この動作により、クライアント アプリケーションへの透過性の高いレベルです。 アプリケーションでは、ドライバーに暗号化された列をターゲットとする値を渡すパラメーターを使用する限り、アプリケーション (およびアプリケーション開発者) は暗号化された列にアクセスするクエリを知る必要ありません。

### <a name="setting-always-encrypted-at-the-query-level"></a>クエリ レベルで Always Encrypted を設定する
パラメーター化クエリに対して暗号化メタデータを取得する操作のパフォーマンスに与える影響を制御するには、有効にできます Always Encrypted 接続用に設定する代わりに個々 のクエリ。 こうするとその sys.sp_describe_parameter_encryption を確認することができますが、暗号化された列をターゲットとするパラメーターがあることがわかっているクエリに対してのみ呼び出されます。 ただし、暗号化の透明性を軽減するための手順を実行している: データベースの列の暗号化プロパティを変更する場合にスキーマの変更に合わせてアプリケーションのコードを変更するたい場合があります。

個々 のクエリの Always Encrypted の動作を制御するにデータの送信し、受信した読み取りと書き込みを指定する SQLServerStatementColumnEncryptionSetting、列挙型を渡すことによって個々 のステートメント オブジェクトを構成する必要があります。その特定のステートメントに対して暗号化された列。 有用なガイドラインを次に示します。
- クライアント アプリケーションがデータベース接続を介して送信するほとんどのクエリは、暗号化された列にアクセスする場合は、次のガイドラインを使用します。
    - 設定、 **columnEncryptionSetting**接続文字列キーワードを**有効**です。
    - 暗号化された列にアクセスしない個々 のクエリの SQLServerStatementColumnEncryptionSetting.Disabled を設定します。 この設定は、結果セット内の値の暗号化を解除しようだけでなく、sys.sp_describe_parameter_encryption の呼び出しに無効になります。
    - 暗号化を必要とする任意のパラメーターはありませんが、暗号化された列からデータを取得する個々 のクエリに対して SQLServerStatementColumnEncryptionSetting.ResultSet を設定します。 この設定は、sys.sp_describe_parameter_encryption の呼び出しとパラメーターの暗号化に無効になります。 クエリは、暗号化列の結果を暗号化解除できます。
- クライアント アプリケーションがデータベース接続を介して送信するほとんどのクエリは、暗号化された列をアクセスしない場合、は、次のガイドラインを使用します。
    - 設定、 **columnEncryptionSetting**接続文字列キーワードを**無効になっている**です。
    - 個々 のクエリに対して暗号化を必要とするパラメーターの SQLServerStatementColumnEncryptionSetting.Enabled を設定します。 この設定は、sys.sp_describe_parameter_encryption の呼び出しと暗号化された列から取得されたクエリ結果の暗号化解除の両方に有効になります。
    - 暗号化を必要とする任意のパラメーターはありませんが、暗号化された列からデータを取得するクエリに対して SQLServerStatementColumnEncryptionSetting.ResultSet を設定します。 この設定は、sys.sp_describe_parameter_encryption の呼び出しとパラメーターの暗号化に無効になります。 クエリは、暗号化列の結果を暗号化解除できます。

SQLServerStatementColumnEncryptionSetting 設定は、暗号化をバイパスし、プレーン テキスト データへのアクセスに使用できません。 ステートメントで列の暗号化を構成する方法の詳細については、次を参照してください。 [Always Encrypted API リファレンス、JDBC driver](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)です。  

次の例では常に暗号化がデータベース接続のため無効です。 アプリケーションの問題が暗号化されていない LastName 列をターゲットとするパラメーターを持つクエリ。 このクエリは、どちらも暗号化されている SSN 列と BirthDate 列からデータを取得します。 このような場合、暗号化メタデータを取得するために sys.sp_describe_parameter_encryption を呼び出す必要ありません。 ただし、クエリ結果の暗号化解除は、アプリケーションは、次の 2 つの暗号化された列からプレーン テキスト値を受信できるように有効にする必要があります。 SQLServerStatementColumnEncryptionSetting.ResultSet 設定はことを確認するために使用します。

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
列暗号化キーの暗号化を解除するための列マスター キー ストアへの呼び出しの数を減らすためには、Microsoft JDBC Driver for SQL Server は、メモリ内には、プレーン テキスト列暗号化キーをキャッシュします。 暗号化された列暗号化キーの値をデータベース メタデータから受信した後、ドライバーは、まず、暗号化されたキーの値に対応するプレーン テキスト列暗号化キーを検索を試みます。 ドライバーは、キャッシュ内で暗号化された列暗号化キーの値が見つからない場合にのみ、列マスター _ キーを含むキーストアを呼び出します。

列暗号化キーのエントリの有効期間の値は、SQLServerConnection クラス setColumnEncryptionKeyCacheTtl()、API を使用して、キャッシュで構成できます。 キャッシュ内の列の暗号化キーのエントリの既定の有効期間値は、2 時間です。 キャッシュを無効にするには、0 の値を使用します。 任意の有効期間値を設定するには、次の API を使用します。

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

たとえば、10 分間の有効期間の値を設定するには、次のように使用します。

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

日数、時間、分、または秒は、時間の単位としてサポートされます。  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>SQLServerBulkCopy を使用して暗号化されたデータのコピー
SQLServerBulkCopy、暗号化およびデータの暗号化を解除せずに別のテーブルに 1 つのテーブルに格納されているデータをコピーできます。 この手順は次のとおりです。

- ターゲット テーブルの暗号化構成が、ソース テーブルの構成と同じであることを確認します。 具体的には、両方のテーブルが、同じ列の暗号化を必要し、同じ暗号化の種類と同じ暗号化キーを使用して列を暗号化する必要があります。 任意のターゲット列が、対応するソース列とは異なる暗号化されている場合、コピー操作の後に、対象のテーブル内のデータの暗号化を解除することができなきます。 データは破損します。
- Always Encrypted が有効なせずに、ソース テーブルと対象テーブルに両方のデータベース接続を構成します。
- AllowEncryptedValueModifications オプションを設定します。 詳細については、次を参照してください。 [JDBC ドライバーで一括コピーを使用して](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)です。

> [!NOTE]
> このオプションは、データが実際に暗号化されている場合、または同じの暗号化を使用して正しく暗号化されている場合、Microsoft JDBC Driver for SQL Server がチェックされませんが、データベースが破損する可能性があります、AllowEncryptedValueModifications を指定するときに注意を使用します。型、アルゴリズム、および対象列としてキー。

## <a name="see-also"></a>参照
[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
