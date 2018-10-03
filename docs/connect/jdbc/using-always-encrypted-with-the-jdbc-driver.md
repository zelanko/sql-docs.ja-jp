---
title: JDBC ドライバーで Always Encrypted の使用 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ce122713ce5d57daa9a7313d8b6d184bd33b850
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842750"
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>JDBC ドライバーでの Always Encrypted の使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

このページを使用して Java アプリケーションの開発方法に関する情報を提供する[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と Microsoft JDBC Driver 6.0 (またはそれ以降) for SQL Server。

Always Encrypted を使用すると、クライアントは SQL Server または Azure SQL データベースにデータまたは暗号化キーを開示することなく、機密データを暗号化することができます。 Microsoft JDBC Driver 6.0 for SQL Server 以降など、Always Encrypted が有効のドライバーは、クライアント アプリケーション内の機密データを透過的に暗号化および暗号化解除することで、この動作を実行します。 ドライバーはクエリを自動的に決定します。 パラメーターは、Always Encrypted データベース列に対応と SQL Server または Azure SQL Database にそれらを送信する前に、これらのパラメーターの値を暗号化します。 同様に、ドライバーは、クエリ結果内の暗号化されたデータベース列から取得されたデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)と[API リファレンスを常に、JDBC ドライバーは暗号化](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)します。

## <a name="prerequisites"></a>Prerequisites
- 6.0 (またはそれ以降) ことを確認の Microsoft JDBC Driver for SQL Server が開発用コンピューターにインストールされています。 
- Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files (JCE 管轄ポリシーファイル (無制限強度)) をダウンロードしてインストールします。  インストール手順、および考えられるエクスポート/インポート問題に関する詳細について、zip ファイルに含まれる Readme を必ず読んでください。  

    - mssql-jdbc-X.X.X.jre7.jar または sqljdbc41.jar を使用している場合は、[Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 7 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html) からポリシー ファイルをダウンロードできます。

    - mssql-jdbc-X.X.X.jre8.jar または sqljdbc42.jar を使用している場合は、[Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 8 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) からポリシー ファイルをダウンロードできます。

    - 場合は mssql jdbc X.X.X.jre9.jar を使用して、ポリシー ファイル必要はありませんをダウンロードします。 Java 9 で管轄ポリシーでは、無制限強度の暗号化が既定値です。

## <a name="working-with-column-master-key-stores"></a>列マスター キー ストアを操作する
暗号化または暗号化された列のデータを復号化には、SQL Server は、列暗号化キーを保持します。 列暗号化キーは、データベースのメタデータに暗号化された形式で格納されています。 各列暗号化キーには、列暗号化キーの暗号化に使用された対応する列マスター キーが含まれます。 データベースのメタデータには、列マスター _ キーが含まれていません。 これらのキーは、クライアントでのみ保持されます。 ただし、データベースのメタデータをクライアントの列マスター_キーの格納場所に関する情報が含まれています。 たとえば、データベースのメタデータ可能性がありますとをキーストアの列マスター キーには、Windows 証明書ストアとの暗号化し、復号化に使用される特定の証明書は、Windows 証明書ストア内の特定のパスを保持します。 クライアントでは、Windows 証明書ストアにその証明書へのアクセスが含まれる場合は、証明書が取得できます。 証明書は、列暗号化キーを復号化に使用できます。 その暗号化キーを復号化またはその列の暗号化キーを使用して暗号化された列のデータの暗号化に使用できます。

Microsoft JDBC Driver for SQL Server と通信から派生したクラスのインスタンスでは、列のマスター _ キーのストア プロバイダーを使用してキーストア**SQLServerColumnEncryptionKeyStoreProvider**します。

### <a name="using-built-in-column-master-key-store-providers"></a>組み込み列マスター キー ストア プロバイダーを使用する
Microsoft JDBC Driver for SQL Server、次の組み込み列マスター キー ストア プロバイダーが付属します。 特定のプロバイダー名 (プロバイダーの検索に使用) に事前登録されているこれらのプロバイダーの一部と、一部は、追加の資格情報または明示的な登録が必要です。

| クラス                                                 | [説明]                                        | プロバイダー (検索) 名  | 事前登録されているか。 |
| :---------------------------------------------------- | :------------------------------------------------- | :---------------------- | :----------------- |
| **SQLServerColumnEncryptionAzureKeyVaultProvider**    | Azure Key Vault のキーストアのプロバイダー。 | AZURE_KEY_VAULT         | いいえ                 |
| **SQLServerColumnEncryptionCertificateStoreProvider** | Windows 証明書ストアのプロバイダー。      | MSSQL_CERTIFICATE_STORE | [ユーザー アカウント制御]                |
| **SQLServerColumnEncryptionJavaKeyStoreProvider**     | Java キーストアのプロバイダー                   | MSSQL_JAVA_KEYSTORE     | [ユーザー アカウント制御]                |

事前登録されたキーストア プロバイダーの場合は、これらのプロバイダーを使用し、次の項目に注意してくださいアプリケーションのコード変更を加える必要はありません。

- ユーザー (またはデータベース管理者) は、列マスター キーのメタデータで構成されているプロバイダー名が正しいこと、および列マスター キー パスが、特定のプロバイダーに対して有効なキー パス形式に準拠していることを確認する必要があります。 CREATE COLUMN MASTER KEY (Transact-SQL) ステートメントを発行する際に有効なプロバイダー名とキー パスを自動的に生成する、SQL Server Management Studio などのツールを使用してキーを構成することをお勧めします。
- アプリケーションがキー ストア内のキーにアクセスできることを確認します。 このタスクには、キーストアに応じてキーまたはキー ストアへのアクセスをアプリケーションに許可したり、その他のキー ストア固有の構成手順を行ったりするプロセスが含まれる場合があります。 たとえば、SQLServerColumnEncryptionJavaKeyStoreProvider を使用するため、場所と接続のプロパティでキーストアのパスワードを入力する必要があります。 

すべてのこれらのキーストア プロバイダーは、次のセクションで詳しく説明します。 Always Encrypted を使用する 1 つのキーストア プロバイダーを実装する必要があるだけです。

### <a name="using-azure-key-vault-provider"></a>Azure Key Vault プロバイダーを使用する
Azure Key Vault は、特にアプリケーションが Azure でホストされている場合、Always Encrypted の列マスター キーの格納と管理に便利なオプションです。 Microsoft JDBC Driver for SQL Server には、組み込みのプロバイダー、SQLServerColumnEncryptionAzureKeyVaultProvider、Azure Key Vault に格納されているキーを持つアプリケーションにはが含まれています。 このプロバイダーの名前は、AZURE_KEY_VAULT です。 Azure Key Vault ストア プロバイダーを使用するには、アプリケーション開発者は Azure Key Vault に資格情報コンテナーとキーを作成し、Azure Active Directory でアプリの登録を作成する必要があります。 登録済みのアプリケーションでは、付与、復号化、暗号化、キーのラップ解除、Wrap Key、および検証アクセス許可を取得で Always Encrypted で使用するために作成された、key vault に対して定義されているアクセス ポリシーをする必要があります。 Key vault を設定して、列マスター _ キーを作成する方法の詳細については、次を参照してください。 [Azure Key Vault-ステップ バイ ステップ](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/)と[Azure Key Vault で列マスター_キーの作成](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault)です。

それらを再作成する T-SQL スクリプトを独自の特定の例のようになります、Azure Key Vault を作成した場合、このページの例は、ベースの列マスター_キーと SQL Server Management Studio を使用して列暗号化キー、 **KEY_パス**と**ENCRYPTED_VALUE**:

```sql
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

```java
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** Azure Active Directory インスタンスでアプリの登録のアプリケーション ID です。 **clientkey では**キーのパスワードをそのアプリケーションを Azure Key Vault への API アクセスの提供に登録します。

アプリケーションでは、SQLServerColumnEncryptionAzureKeyVaultProvider のインスタンスが作成されたら、アプリケーションは SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドを使用してドライバーを使用したインスタンスを登録する必要があります。 既定の参照名、SQLServerColumnEncryptionAzureKeyVaultProvider.getName() API を呼び出すことによって取得できる AZURE_KEY_VAULT を使用して、インスタンスを登録することを強くお勧めします。 既定の名前を使用して使用すると、SQL Server Management Studio や PowerShell などのツールを使用して、プロビジョニングおよび Always Encrypted のキー (ツールは、列マスター キー メタデータ オブジェクトを生成する既定の名前を使用) を管理できます。 次の例では、Azure Key Vault プロバイダーの登録を示します。 SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドの詳細については、次を参照してください。 [API リファレンスを常に、JDBC ドライバーは暗号化](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)します。

```java
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Azure Key Vault のキーストア プロバイダーを使用する場合、アプリケーションに含める必要がありますが (GitHub) からのこれらのライブラリに依存している JDBC ドライバーの Azure Key Vault 実装。
>
>  [azure sdk for java](https://github.com/Azure/azure-sdk-for-java)
>
>  [azure active directory-ライブラリ-用の java ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> これらの依存関係を Maven プロジェクトに含める方法の例は、次を参照してください[ダウンロード ADAL4J と AKV の依存関係 Apache Maven で。](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>Windows 証明書ストアのプロバイダーを使用します。
SQLServerColumnEncryptionCertificateStoreProvider は、列マスター キーを Windows 証明書ストアに格納するために使用できます。 列マスター_キーと列の暗号化キーの定義をデータベースに作成するのにには、SQL Server Management Studio (SSMS) が Always Encrypted ウィザードまたはサポートされているその他のツールを使用します。 常に暗号化されたデータの列マスター_キーとして使用できる Windows 証明書ストアに自己署名証明書を生成する、同じウィザードを使用できます。 列マスター_キーと列暗号化キーの T-SQL 構文の詳細については、次を参照してください。 [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)と[列暗号化キーの作成](../../t-sql/statements/create-column-encryption-key-transact-sql.md)それぞれします。

SQLServerColumnEncryptionCertificateStoreProvider の名前は、MSSQL_CERTIFICATE_STORE でプロバイダー オブジェクトの getName() API によってクエリを実行できます。 ドライバーによって自動的に登録し、アプリケーションを変更せずにシームレスに使用されることができます。

それらを再作成する T-SQL スクリプトを独自の特定の例のようになりますWindows証明書ストアを作成した場合、このページの例は、ベースの列マスター_キーとSQLServerManagementStudioを使用して列暗号化キー、**KEY_PATH**と**ENCRYPTED_VALUE**:

```sql
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
> 他のキーストア プロバイダーは、この記事では、ドライバーでサポートされるすべてのプラットフォームで利用可能な JDBC ドライバーの SQLServerColumnEncryptionCertificateStoreProvider 実装は Windows オペレーティング システムでのみ使用できます。 ドライバー パッケージで使用できる sqljdbc_auth.dll の依存関係があります。 このプロバイダーを使用するには、JDBC ドライバーがインストールされているコンピューターの Windows システム パス上のディレクトリに sqljdbc_auth.dll ファイルをコピーします。 または、java.libary.path システム プロパティを設定して sqljdbc_auth.dll のディレクトリを指定することもできます。 32 ビットの Java 仮想マシン (JVM) を実行している場合は、オペレーティング システムのバージョンが x64 であっても、x86 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 64 ビットの JVM を x64 プロセッサ上で実行している場合は、x64 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 たとえば、32 ビットの JVM を使用していて、JDBC ドライバーが既定のディレクトリにインストールされている場合、Java アプリケーションの起動時に次の仮想マシン (VM) 引数を使用することで、DLL の場所を指定できます。`-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>Java キー ストア プロバイダーを使用します。
JDBC ドライバーには、Java キー ストアの組み込みキー ストア プロバイダー実装が含まれています。 場合、 **keyStoreAuthentication**接続文字列プロパティは、接続文字列に存在する、"JavaKeyStorePassword"に設定されていると、ドライバーは自動的にインスタンス化し、Java キー ストア プロバイダーを登録します。 Java キー ストア プロバイダーの名前は、MSSQL_JAVA_KEYSTORE です。 この名前は、SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API を使用して照会することもできます。 

クライアント アプリケーション、ドライバーは、Java キー ストアへの認証が必要な資格情報を指定できるようにする 3 つの接続文字列プロパティがあります。 ドライバーでは、これら 3 つの接続文字列プロパティの値に基づいてプロバイダーを初期化します。

**keyStoreAuthentication:** を使用する Java キー ストアを識別します。 Microsoft JDBC Driver for SQL Server 6.0 以降では、このプロパティを介してのみ Java キー ストアに認証できます。 Java キー ストアで、このプロパティの値がある必要があります`JavaKeyStorePassword`します。

**keyStoreLocation:** 列マスター _ キーを格納する Java キーストア ファイルへのパス。 パスには、キーストア ファイル名が含まれています。

**keyStoreSecret:** シークレット/パスワード、キーともキーストアを使用します。 Java キー ストアを使用するため、キーストアとキーのパスワード同じでなければなりません。

接続文字列にこれらの資格情報を提供する例を次に示します。

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

取得または SQLServerDataSource オブジェクトを使用してこれらの設定を設定することもできます。 詳細については、次を参照してください。 [API リファレンスを常に、JDBC ドライバーは暗号化](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)します。

JDBC ドライバーでは、これらの資格情報が接続のプロパティに存在する場合、SQLServerColumnEncryptionJavaKeyStoreProvider が自動的にインスタンス化します。

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Java キー ストアの列マスター _ キーを作成します。
JKS または PKCS12 キーストアの型を持つ、SQLServerColumnEncryptionJavaKeyStoreProvider を使用できます。 このプロバイダーで使用するキーを作成またはインポートするには、Java を使用して[keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html)ユーティリティ。 キーは、キーストア自体と同じパスワードをいる必要があります。 公開キーと keytool ユーティリティを使用して関連付けられた秘密キーを作成する方法の例を次に示します。

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

このコマンドは、公開キーを作成し、関連付けられた秘密キーと共に ' keystore.jks' キーストアに格納されている証明書の自己署名 X.509 でラップします。 キーストア内のこのエントリは、エイリアス 'AlwaysEncryptedKey' によって識別されます。

PKCS12 ストアの種類を使用する同じ例を次に示します。

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

キーストアの PKCS12 型の場合、keytool ユーティリティは、キーのパスワードを要求しないし、キーのパスワードを SQLServerColumnEncryptionJavaKeyStoreProvider は、キーストアとキーが同じである必要があります - keypass オプションを提供する必要があります。パスワードです。

.Pfx 形式で Windows の証明書ストアから証明書をエクスポートし、SQLServerColumnEncryptionJavaKeyStoreProvider と一緒に使用こともできます。 エクスポートした証明書は、JKS keystore の種類として Java キー ストアにインポートすることもできます。

Keytool エントリを作成した後は、キーストア プロバイダー名とキーのパスを必要とすると、データベースで列マスター_キーのメタデータを作成します。 列マスター_キーのメタデータを作成する方法の詳細については、次を参照してください。 [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)します。 SQLServerColumnEncryptionJavaKeyStoreProvider、キーのパスは、キーのエイリアスだけで、SQLServerColumnEncryptionJavaKeyStoreProvider の名は 'MSSQL_JAVA_KEYSTORE' です。 SQLServerColumnEncryptionJavaKeyStoreProvider クラスの getName() パブリック API を使用してこの名前をクエリすることもできます。 

列マスター_キーを作成するための T-SQL 構文です。

```sql
CREATE COLUMN MASTER KEY [<CMK_name>]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'<key_alias>'
)
```

'AlwaysEncryptedKey' 上記で作成した、列マスター _ キーの定義になります。

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```

> [!NOTE]
> 組み込みの SQL Server management Studio の機能は、Java のキー ストアの列マスター _ キーの定義を作成できません。 T-SQL コマンドをプログラムで使用する必要があります。

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Java キー ストアの列暗号化キーを作成します。
Java キー ストアに列マスター _ キーを使用して暗号化キーの列を作成する、SQL Server Management Studio またはその他のツールを使用できません。 クライアント アプリケーションでは、SQLServerColumnEncryptionJavaKeyStoreProvider クラスを使用してプログラムで列暗号化キーを作成する必要があります。 詳細については、次を参照してください。[列マスター キー ストア プロバイダーを使用して、プログラムによるキーのプロビジョニングの](#using-column-master-key-store-providers-for-programmatic-key-provisioning)します。

### <a name="implementing-a-custom-column-master-key-store-provider"></a>カスタム列マスター キー ストア プロバイダーを実装する
既存のプロバイダーでサポートされていないキー ストアに列マスター キーを格納する場合は、SQLServerColumnEncryptionKeyStoreProvider クラスを拡張し、SQLServerConnection.registerColumnEncryptionKeyStoreProviders() メソッドを使用してプロバイダーを登録して、カスタム プロバイダーを実装できます。

```java
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

```java
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(storeProvider.getName(), storeProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>プログラムによるキーのプロビジョニングに列マスター キー ストア プロバイダーを使用する
Microsoft JDBC Driver for SQL Server は、暗号化された列にアクセスする際に、列暗号化キーを暗号化解除するための適切な列マスター キー ストア プロバイダーを透過的に検索して呼び出します。 一般的に、通常のアプリケーション コードは列マスター キー ストア プロバイダーを直接呼び出しません。 ただしのインスタンスを作成、プロビジョニングや Always Encrypted キーの管理をプログラムでのプロバイダーに連絡する可能性があります。 暗号化された列暗号化キーを生成し、例として、一部の列マスター_キーの回転、列暗号化キーを復号化には、この手順を実行することがあります。 詳細については、「 [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Always Encrypted のキー管理の概要)」を参照してください。

カスタム キー ストア プロバイダーを使用する場合、独自のキー管理ツールの実装が必要になることがあります。 Windows 証明書ストアまたは Azure Key Vault に格納されているキーを使用する場合は、キーのプロビジョニングを管理する SQL Server Management Studio や PowerShell などの既存のツールを使用できます。 Java キー ストアに格納されたキーを使用する場合は、キーをプログラムでプロビジョニングする必要があります。 Java キー ストアに格納されているキーを使用してキーの暗号化に SQLServerColumnEncryptionJavaKeyStoreProvider クラスを使用して次の例を示しています。

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
 */
public class AlwaysEncrypted {
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
     * Name of the encryption algorithm used to encrypt the value of the column encryption key. The algorithm for the system providers must be
     * RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";

        try (Connection connection = DriverManager.getConnection(connectionUrl);
                Statement statement = connection.createStatement();) {

            // Instantiate the Java Key Store provider.
            SQLServerColumnEncryptionKeyStoreProvider storeProvider = new SQLServerColumnEncryptionJavaKeyStoreProvider(keyStoreLocation,
                    keyStoreSecret);

            byte[] encryptedCEK = getEncryptedCEK(storeProvider);

            /**
             * Create column encryption key For more details on the syntax, see:
             * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql Encrypted column encryption key first needs
             * to be converted into varbinary_literal from bytes, for which byteArrayToHex() is used.
             */
            String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY "
                    + columnEncryptionKey
                    + " WITH VALUES ( "
                    + " COLUMN_MASTER_KEY = "
                    + columnMasterKeyName
                    + " , ALGORITHM =  '"
                    + algorithm
                    + "' , ENCRYPTED_VALUE =  0x"
                    + byteArrayToHex(encryptedCEK)
                    + " ) ";
            statement.executeUpdate(createCEKSQL);
            System.out.println("Column encryption key created with name : " + columnEncryptionKey);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException {
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(keyAlias, algorithm, plainCEK);

        return encryptedCEK;
    }

    public static String byteArrayToHex(byte[] a) {
        StringBuilder sb = new StringBuilder(a.length * 2);
        for (byte b : a)
            sb.append(String.format("%02x", b).toUpperCase());
        return sb.toString();
    }
}
```

## <a name="enabling-always-encrypted-for-application-queries"></a>アプリケーション クエリで Always Encrypted を有効にする
パラメーターの暗号化と、暗号化された列をターゲットとするクエリ結果の暗号化解除を有効にする最も簡単な方法としては、**columnEncryptionSetting** 接続文字列キーワードの値を **Enabled** に設定します。

次の接続文字列は、JDBC ドライバーで Always Encrypted を有効にする例を示します。

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
```

次のコードでは、SQLServerDataSource オブジェクトを使用して同等の例を示します。

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(<port>);
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Always Encrypted は、個々のクエリに対しても有効にすることができます。 詳細については、次を参照してください。 [Always Encrypted のパフォーマンスに与える影響を制御する](#controlling-the-performance-impact-of-always-encrypted)します。 暗号化または暗号化解除を正常に行うには、Always Encrypted を有効にするだけでは不十分です。 次のことを確認する必要もあります。
- アプリケーションが、データベース内の Always Encrypted キーに関するメタデータへのアクセスに必要な *VIEW ANY COLUMN MASTER KEY DEFINITION* および *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* データベース権限を持っている。 詳細については、[「Always Encrypted (データベース エンジン)」のページで権限に関するセクション](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions)を参照してください。
- アプリケーションが、列暗号化キーを保護する列マスター キーにアクセスでき、クエリされたデータベース列を暗号化する。 Java キー ストア プロバイダーを使用するには、接続文字列に追加の資格情報を提供する必要があります。 詳細については、次を参照してください。[を使用する Java キー ストア プロバイダー](#using-java-key-store-provider)します。

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>java.sql.Time の値をサーバーに送信する方法の構成
java.sql.Time 値のサーバーへの送信方法を構成するために、**sendTimeAsDatetime** 接続プロパティを使用します。 時刻の値は false に設定すると、SQL Server 時の型として送信されます。 値が datetime 型として送信された時刻を true に設定するとします。 Time 列が暗号化されている場合、**で sendTimeAsDatetime**暗号化された列は、時間から datetime への変換をサポートしないプロパティが false に設定する必要があります。 このプロパティは、暗号化された列を使用する場合は、false に設定する必要がありますので、既定値は true にも注意してください。 それ以外の場合、ドライバーは、例外をスローします。 プログラムでこのプロパティの値を構成する 2 つのメソッドを SQLServerConnection クラスは、ドライバーのバージョン 6.0 以降、あります。
 
* public void setSendTimeAsDatetime (ブール sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

このプロパティの詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](configuring-how-java-sql-time-values-are-sent-to-the-server.md)します。

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>文字列の値がサーバーに送信する方法を構成します。
**SendStringParametersAsUnicode**文字列の値を SQL Server に送信する方法を構成する接続プロパティを使用します。 true に設定されている場合、サーバーには Unicode 形式で文字列パラメーターが送信されます。 文字列パラメーターを false に設定は、ASCII または Unicode ではなく、MBCS などの Unicode 以外の形式で送信されます。 場合、 このプロパティの既定値は、true です。 Always Encrypted が有効になっているし、char/varchar/varchar(max) 列が暗号化されて、値の**sendStringParametersAsUnicode**を false に設定する必要があります。 このプロパティ設定されている場合は true、ドライバーは例外をスローを Unicode 文字を持つ暗号化された char/varchar/varchar(max) 列からデータを復号化するときにします。 このプロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)します。
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>暗号化された列のデータを取得および変更する
アプリケーション クエリに対して Always Encrypted を有効すると、取得または暗号化されたデータベース列のデータを変更する標準の JDBC Api を使用できます。 アプリケーションが必要なデータベース アクセス許可を持つ列マスター_キーにアクセスできる場合、ドライバーは暗号化された列をターゲットし、は、暗号化された列から取得されるデータを復号化するすべてのクエリ パラメーターを暗号化します。

Always Encrypted が有効でない場合、暗号化された列をターゲットとするパラメーターを含むクエリは失敗します。 暗号化された列をターゲットとするパラメーターがクエリにない場合、クエリでは、暗号化された列からデータを取得できます。 ただし、ドライバーは、暗号化された列から取得された値を暗号化解除しようとせず、アプリケーションは、暗号化されたバイナリ データを (バイト配列として) 受け取ります。

次の表は、Always Encrypted が有効かどうかに応じたクエリの動作をまとめたものです。

| クエリの特性                                                                           | Always Encrypted が有効になっており、アプリケーションがキーとキー メタデータにアクセスできる                                                                                                                        | Always Encrypted が有効になっており、アプリケーションがキーまたはキー メタデータにアクセスできない | Always Encrypted が無効になっている                                                                                        |
| :--------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------ |
| 暗号化された列をターゲットとするパラメーターを含むクエリ。                                           | パラメーター値は透過的に暗号化されます。                                                                                                                                                           | [エラー]                                                                             | [エラー]                                                                                                               |
| 暗号化された列をターゲットとするパラメーターを含まず、暗号化された列からデータを取得するクエリ。 | 暗号化された列の結果は透過的に暗号化解除されます。 アプリケーションは、暗号化された列用に構成された SQL Server 型に対応する、JDBC データ型のプレーンテキスト値を受け取ります。 | [エラー]                                                                             | 暗号化された列の結果は暗号化解除されません。 アプリケーションは、暗号化された値をバイト配列 (byte[]) として受け取ります。 |

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>挿入して、暗号化されたデータの例を取得します。

次の例は、暗号化された列のデータを取得および変更する方法を示しています。 例には、次のスキーマおよび SSN と BirthDate の暗号化された列を使用して、対象テーブルがあるとします。 という名前の列マスター _ キーを構成した場合は"MyCMK"と列の暗号化キーという名前の"MyCEK"(上記のキーストア プロバイダー セクションで説明) と、このスクリプトを使用してテーブルを作成することができます。

```sql
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

それぞれの Java コード例の記載場所にキーストアに固有のコードを挿入する必要があります。

Azure Key Vault のキーストア プロバイダーを使用する: 場合

```java
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Windows 証明書ストアのキーストア プロバイダーを使用する: 場合

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Java キー ストアのキーストア プロバイダーを使用する: 場合

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>データの挿入の例

この例では、Patients テーブルに列を挿入します。 次の項目に注意してください。

- このサンプル コードの暗号化に固有のものは何もありません。 Microsoft JDBC Driver for SQL Server は自動的に検出し、暗号化された列をターゲットとするパラメーターを暗号化します。 この動作により、アプリケーションに対して暗号化が透過的に実行されます。
- 暗号化された列を含め、データベース列に挿入された値は、SQLServerPreparedStatement を使用して、パラメーターとして渡されます。 暗号化されていない列に値を送信する場合、パラメーターの使用は省略可能です (ただし、SQL インジェクションを防ぐのに役立つので、強くお勧めします) が、暗号化された列をターゲットとする値に対しては必須です。 暗号化された列に挿入された値は、クエリ ステートメントに埋め込まれているリテラルとして渡された、ドライバーがターゲットの暗号化された列の値を決定できませんし、値が暗号化されることはありませんので、クエリは失敗します。 その結果、サーバーはこれらの値を、暗号化された列と互換性がないと見なして拒否します。
- Microsoft JDBC Driver for SQL Server は、暗号化された列から取得されたデータを透過的に暗号化解除するので、プログラムで印刷される値はすべてプレーンテキストになります。
- WHERE 句、WHERE 句が必要で、ドライバーでは、データベースに送信する前に暗号化透過的にするために、パラメーターとして渡される使用される値を使用して検索を行っています。 場合、 次の例では、SSN はパラメーターとして渡されますが、LastName が暗号化されていないと、LastName はリテラルとして渡されます。
- SSN 列をターゲットとするパラメーターに使用される setter メソッドは、setString()、char/varchar SQL Server データ型にマップされます。 このパラメーターに対して使用されている setter メソッドが setNString () だった場合、nchar/nvarchar にマップされ、クエリは失敗します。これは、暗号化された nchar/nvarchar 値から暗号化された char/varchar 値への変換が Always Encrypted でサポートされていないためです。

```java
// <Insert keystore-specific code here>
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement insertStatement = sourceConnection.prepareStatement("INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)")) {
    insertStatement.setString(1, "795-73-9838");
    insertStatement.setString(2, "Catherine");
    insertStatement.setString(3, "Abel");
    insertStatement.setDate(4, Date.valueOf("1996-09-10"));
    insertStatement.executeUpdate();
    System.out.println("1 record inserted.\n");
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-plaintext-data-example"></a>プレーンテキスト データの取得の例

次の例は、暗号化された値に基づいてデータをフィルター処理し、暗号化された列からプレーンテキスト データを取得する方法を示しています。 次の項目に注意してください。

- SSN 列に対してフィルター処理するために WHERE 句で使用される値は、Microsoft JDBC Driver for SQL Server がデータベースに送信する前に透過的に暗号化できるように、パラメーターとして渡す必要があります。
- Microsoft JDBC Driver for SQL Server は、SSN 列と BirthDate 列から取得されたデータを透過的に暗号化解除するので、プログラムで印刷される値はすべてプレーンテキストになります。

> [!NOTE]
> 決定論的暗号化を使用して列が暗号化される場合、クエリは列に対して等価比較を実行できます。 詳細については、[「Always Encrypted (データベース エンジン)」の「明確な暗号化またはランダム化された暗号化の選択」](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption)を参照してください。

```java
// <Insert keystore-specific code here>
try (Connection connection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection
                .prepareStatement("\"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;\"");) {
    selectStatement.setString(1, "795-73-9838");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-encrypted-data-example"></a>暗号化されたデータの取得の例

Always Encrypted が有効になっていない場合でも、暗号化された列をターゲットとするパラメーターをクエリが含んでいなければ、クエリでは、暗号化された列からデータを取得できます。

次の例は、暗号化された列から暗号化されたバイナリ データを取得する方法を示しています。 次の項目に注意してください。

- 接続文字列で Always Encrypted が有効になっていないので、クエリは、SSN と BirthDate の暗号化された値をバイト配列として返します (プログラムによって値が文字列に変換されます)。
- Always Encrypted が無効の状態で、暗号化された列からデータを取得するクエリは、暗号化された列をターゲットとするパラメーターがない場合に限り、パラメーターを含むことができます。 次のクエリは、データベースで暗号化されない LastName によってフィルター処理を行います。 クエリが SSN または BirthDate によってフィルター処理を行った場合、クエリは失敗します。

```java
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = sourceConnection
                .prepareStatement("SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;");) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>暗号化された列をクエリする際の一般的な問題を回避する

ここでは、暗号化された列を Java アプリケーションからクエリする際のエラーの一般的なカテゴリと、その対処方法に関するいくつかのガイドラインを示します。

### <a name="unsupported-data-type-conversion-errors"></a>サポートされていないデータ型の変換エラー

Always Encrypted では、暗号化されたデータ型に対するいくつかの変換がサポートされています。 サポートされている型の変換の詳細な一覧については、「[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。 データ型の変換エラーを回避するには、 次のことを確認してください。

- 暗号化された列を対象とするパラメーターの値を渡す場合は、適切な setter メソッドを使用します。 パラメーターの SQL Server データ型が正確に対象列の型と同じパラメーターの SQL Server データ型の列のターゲット型への変換はサポートされていることを確認します。 API のメソッドが特定の SQL Server データ型に対応するパラメーターを渡す SQLServerPreparedStatement や SQLServerCallableStatement、SQLServerResultSet クラスに追加されました。 たとえば、列が暗号化されていない場合、datetime2、datetime 型の列、パラメーターを渡す setTimestamp() メソッドを使用することができます。 列が暗号化されている場合は、データベース内の列の型を表す正確なメソッドを使用する必要があります。 たとえば、setTimestamp() を使用して、暗号化された datetime2 列に値を渡すし、暗号化された datetime 列に値を渡す setDateTime() を使用します。 参照してください[API リファレンスを常に、JDBC ドライバーは暗号化](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)新しい Api の完全な一覧についてはします。
- 10 進数と数値の SQL Server データ型の列をターゲットとするパラメーターの有効桁数と小数点以下桁数が、ターゲット列に対して構成された有効桁数と小数点と同じである。 API のメソッドが、有効桁数と小数点と共に decimal および numeric のデータ型を表すパラメーター/列のデータ値をそのまま使用する SQLServerPreparedStatement、SQLServerCallableStatement、SQLServerResultSet クラスに追加されました。 参照してください[API リファレンスを常に、JDBC ドライバーは暗号化 ](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) /オーバー ロードされた新しい Api の完全な一覧についてはします。  
- datetime2、datetimeoffset、または時刻の SQL Server データ型の列をターゲットとするパラメーターの秒の小数部桁数/いない対象列の値を変更するクエリでは、ターゲット列に対して秒の小数部桁数/より大きい. API のメソッドが、秒の小数部の有効桁数/スケールと共にこれらのデータ型を表すパラメーターのデータ値をそのまま使用する SQLServerPreparedStatement や SQLServerCallableStatement、SQLServerResultSet クラスに追加されました。 /オーバー ロードされた新しい Api の完全な一覧を参照してください。 [API リファレンスを常に、JDBC ドライバーは暗号化](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)します。

### <a name="errors-due-to-incorrect-connection-properties"></a>不適切な接続プロパティに起因するエラー

このセクションでは、常に暗号化されたデータを使用するには、正しく接続設定を構成する方法について説明します。 暗号化されたデータの種類、制限付きの変換をサポートするため、**で sendTimeAsDatetime**と**sendStringParametersAsUnicode**接続の設定は、暗号化された列を使用する場合、適切な構成を必要があります。 次のことを確認してください。

- [sendTimeAsDatetime](setting-the-connection-properties.md)時間列の暗号化されたデータを挿入するとき、接続の設定が false に設定します。 詳細については、次を参照してください。 [java.sql.Time の値がサーバーに送信する方法を構成する](configuring-how-java-sql-time-values-are-sent-to-the-server.md)します。
- [sendStringParametersAsUnicode](setting-the-connection-properties.md)接続設定に設定されて true (または既定値のままです) と、char/varchar/varchar(max) 列を暗号化するデータを挿入します。

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>暗号化された値の代わりにプレーンテキストを渡すことによるエラー

暗号化された列をターゲットとするすべての値は、アプリケーションの内部で暗号化される必要があります。 暗号化された列でプレーンテキスト値を挿入/変更したり、この値によってフィルター処理を行おうとしたりすると、次のようなエラーになります。

```java
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

このようなエラーを防ぐには、次のことを確認してください。

- Always Encrypted が、暗号化された列をターゲットとするアプリケーション クエリに対して有効になっている (接続文字列または特定のクエリで)。
- 準備されたステートメントを使用して、暗号化された列のデータを対象とするを送信するパラメーター。 次の例は、パラメーターとしてリテラルを渡す代わりに、暗号化された列 (SSN) でリテラル/定数によって不正なフィルター処理を行うクエリを示しています。 このクエリは失敗します。

```java
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>入力パラメーターで暗号化を強制します。

Always Encrypted を使用する場合、強制的に暗号化機能は、パラメーターの暗号化を適用します。 強制的な暗号化が使用され、パラメーターの暗号化が不要であることが SQL Server からドライバーに通知された場合、このパラメーターを使用するクエリは失敗します。 攻撃を受けた SQL Server がクライアントに不正な暗号化メタデータを提供すると、データ漏えいが引き起こされる可能性がありますが、このプロパティは、そのようなセキュリティ攻撃に対する保護を強化します。 SQLServerPreparedStatement や SQLServerCallableStatement クラスおよび更新プログラム セット * メソッド\*強制暗号化の設定を指定するブール型の引数を受け入れるように SQLServerResultSet クラスのメソッドはオーバー ロードします。 この引数の値が false の場合、ドライバーは、パラメーターで暗号化を強制しません。 強制的に暗号化が設定されている場合は true、クエリに変換先列が暗号化されていて、接続またはステートメントでは、Always Encrypted が有効パラメーターは送信のみです。 このプロパティを使用すると、こと、ドライバーが誤ってにデータを送信 SQL Server として、プレーン テキストを暗号化することを想定している場合ことを確認して、セキュリティの層を追加します。

暗号化設定を強制 SQLServerPreparedStatement、SQLServerCallableStatement のメソッドをオーバー ロードの詳細については、次を参照してください[API リファレンスを常に、JDBC ドライバーの暗号化。](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Always Encrypted のパフォーマンスの影響を制御する

Always Encrypted はクライアント側暗号化テクノロジであるため、ほとんどのパフォーマンス オーバーヘッドは、データベースではなくクライアント側で発生します。 暗号化および暗号化解除の操作のコストとは別に、クライアント側のパフォーマンス オーバーヘッドのその他の原因を次に示します。

- クエリ パラメーターのメタデータを取得するためのデータベースへの追加のラウンド トリップ。
- 列マスター キーにアクセスするための列マスター キー ストアの呼び出し。

このセクションでは、Microsoft JDBC Driver for SQL Server の組み込みのパフォーマンス最適化、および上記の 2 つの要因によるパフォーマンスへの影響を制御する方法について説明します。

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>クエリ パラメーターのメタデータを取得するためのラウンド トリップを制御する

既定では、接続に対して Always Encrypted が有効になっている場合、ドライバーは、各パラメーター化クエリに対して [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) を呼び出し、クエリ ステートメント (パラメーター値を除く) を SQL Server に渡します。 [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) はクエリ ステートメントを分析して、パラメーターを暗号化する必要があるかどうかを判断し、必要がある場合は、これらの各パラメーターに対して暗号化関連の情報を返します。この情報により、ドライバーはパラメーター値を暗号化できます。 この動作により、クライアント アプリケーションに対する高度な透明性が確保されます。 アプリケーションでは、ドライバーに暗号化された列をターゲットとする値を渡すパラメーターを使用する限り、アプリケーション (およびアプリケーション開発者) は、暗号化された列にアクセスするクエリを認識する必要ありません。

### <a name="setting-always-encrypted-at-the-query-level"></a>クエリ レベルで Always Encrypted を設定する

パラメーター化クエリに対して暗号化メタデータを取得することによるパフォーマンスへの影響を制御するには、Always Encrypted を接続に対して設定する代わりに、個々のクエリに対して有効にします。 これにより、暗号化された列をターゲットとするパラメーターを含むことがわかっているクエリに対してのみ、sys.sp_describe_parameter_encryption が呼び出されるように設定できます。 ただし、これにより、暗号化の透明度が損なわれることに注意してください。データベース列の暗号化プロパティを変更する場合は、スキーマの変更に合わせてアプリケーション コードの変更が必要になる可能性があります。

個々 のクエリの Always Encrypted の動作を制御するには列挙型であり、データの送信し、受信の読み取りと書き込みの際に指定する、SQLServerStatementColumnEncryptionSetting を渡すことによって、個々 のステートメント オブジェクトを構成する必要があります。その特定のステートメントに対して暗号化された列。 有用なガイドラインを次に示します。

- クライアント アプリケーションがデータベース接続を介して送信するほとんどのクエリが、暗号化された列にアクセスする場合は、次のガイドラインを使用してください。

    - **columnEncryptionSetting** 接続文字列キーワードを **Enabled** に設定します。
    - 暗号化された列にアクセスしない個々のクエリに対して、SQLServerStatementColumnEncryptionSetting.Disabled を設定します。 この設定により、sys.sp_describe_parameter_encryption の呼び出しと、結果セット内の値を暗号化解除しようとする試みの両方が無効になります。
    - 暗号化を必要とするパラメーターを含まないが、暗号化された列からデータを取得する個々のクエリに対して、SQLServerStatementColumnEncryptionSetting.ResultSet を設定します。 この設定により、sys.sp_describe_parameter_encryption の呼び出しと、パラメーター暗号化が無効になります。 クエリは、暗号化列の結果を暗号化解除できます。

- クライアント アプリケーションがデータベース接続を介して送信するほとんどのクエリが、暗号化された列にアクセスしない場合は、次のガイドラインを使用してください。

    - **columnEncryptionSetting** 接続文字列キーワードを **Disabled** に設定します。
    - 暗号化を必要とするパラメーターを含む個々のクエリに対して、SQLServerStatementColumnEncryptionSetting.Enabled を設定します。 この設定により、sys.sp_describe_parameter_encryption の呼び出しと、暗号化された列から取得されたクエリ結果の暗号化解除の両方が有効になります。
    - 暗号化を必要とするパラメーターを含まないが、暗号化された列からデータを取得するクエリに対して、SQLServerStatementColumnEncryptionSetting.ResultSet を設定します。 この設定により、sys.sp_describe_parameter_encryption の呼び出しと、パラメーター暗号化が無効になります。 クエリは、暗号化列の結果を暗号化解除できます。

SQLServerStatementColumnEncryptionSetting 設定は、暗号化をバイパスし、プレーン テキスト データへのアクセスに使用できません。 ステートメントで列の暗号化を構成する方法の詳細については、次を参照してください。 [API リファレンスを常に、JDBC ドライバーは暗号化](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)します。  

次の例では、データベース接続に対して Always Encrypted が無効になっています。 アプリケーションが発行するクエリに、暗号化されていない LastName 列をターゲットとするパラメーターが含まれています。 このクエリは、どちらも暗号化されている SSN 列と BirthDate 列からデータを取得します。 このような場合、暗号化メタデータを取得するために sys.sp_describe_parameter_encryption を呼び出す必要ありません。 ただし、アプリケーションが 2 つの暗号化された列からプレーンテキスト値を受け取ることができるよう、クエリ結果の暗号化解除を有効にする必要があります。 SQLServerStatementColumnEncryptionSetting.ResultSet 設定は、いることを確認に使用されます。

```java
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>;" 
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=<keyStoreLocation>" 
        + "keyStoreSecret=<keyStoreSecret>;";

String filterRecord = "SELECT FirstName, LastName, SSN, BirthDate FROM " + tableName + " WHERE LastName = ?";

try (SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection.prepareStatement(filterRecord, ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_READ_ONLY,
                connection.getHoldability(), SQLServerStatementColumnEncryptionSetting.ResultSetOnly);) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("First name: " + rs.getString("FirstName"));
        System.out.println("Last name: " + rs.getString("LastName"));
        System.out.println("SSN: " + rs.getString("SSN"));
        System.out.println("Date of Birth: " + rs.getDate("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="column-encryption-key-caching"></a>列暗号化キーのキャッシュ

列暗号化キーを暗号化解除するための列マスター キー ストアの呼び出し回数を減らすために、Microsoft JDBC Driver for SQL Server は、プレーンテキストの列暗号化キーをメモリにキャッシュします。 暗号化された列暗号化キー値をデータベース メタデータから受け取った後、ドライバーは、暗号化されたキー値に対応するプレーンテキストの列暗号化キーをまず見つけようとします。 ドライバーは、暗号化された列暗号化キー値がキャッシュ内に見つからない場合にのみ、列マスター キーを含むキー ストアを呼び出します。

SetColumnEncryptionKeyCacheTtl()、API を使用して、SQLServerConnection クラスのキャッシュでは、列暗号化キー エントリの有効期限の値を構成できます。 キャッシュ内の列暗号化キー エントリの既定の有効期限値には、2 つの時間です。 キャッシュを無効にするには、値 0 を使用します。 任意の有効期限の値を設定するには、次の API を使用します。

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

たとえば、10 分間の有効期限の値を設定する次のように使用します。

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

日、時間、分、または秒のみが、時間の単位としてサポートされます。  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>SQLServerBulkCopy を使用して暗号化されたデータのコピー

SQLServerBulkCopy を使用して、データの暗号化解除を行うことなく、既に暗号化されて 1 つのテーブルに格納されているデータを別のテーブルにコピーできます。 この手順は次のとおりです。

- ターゲット テーブルの暗号化構成が、ソース テーブルの構成と同じであることを確認します。 具体的には、両方のテーブルで同じ列が暗号化されており、同じ暗号化タイプおよび同じ暗号化キーを使用してこれらの列が暗号化されている必要があります。 いずれかのターゲット列が、対応するソース列と異なる方法で暗号化されている場合、コピー操作の後でターゲット テーブル内のデータを暗号化解除することはできません。 データは破損します。
- Always Encrypted を有効にせずに、ソース テーブルとターゲット テーブルへの両方のデータベース接続を構成します。
- AllowEncryptedValueModifications オプションを設定します。 詳細については、次を参照してください。 [JDBC ドライバーで一括コピーを使用して](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)します。

> [!NOTE]
> データベースが破損する可能性があるので、AllowEncryptedValueModifications を指定する際には注意が必要です。このオプションは、データが実際に暗号化されているかどうか、またはターゲット列と同じ暗号化のタイプ、アルゴリズム、およびキーを使用して正しく暗号化されているかどうかを、Microsoft JDBC Driver for SQL Server がチェックしないためです。

## <a name="see-also"></a>参照

[Always Encrypted (データベース エンジン)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
