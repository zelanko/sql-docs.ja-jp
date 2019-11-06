---
title: セキュリティで保護されたエンクレーブが設定された Always Encrypted を構成する | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 27f78de54735559365f771aaee3669b8f08856c7
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72902989"
---
# <a name="configure-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted を構成する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[セキュリティで保護されたエンクレーブが設定された Always Encrypted](always-encrypted-enclaves.md) は、既存の [Always Encrypted ](always-encrypted-database-engine.md) 機能を拡張して、データを機密性に保ちながら機密データに対してより高度な機能を有効にすることができます。

セキュリティで保護されたエンクレーブが設定された Always Encrypted を設定するには、次のワークフローを使用します。

1. ホスト ガーディアン サービス (HGS) 構成証明を構成します。
2. SQL Server コンピューターに [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] をインストールします。
3. クライアント/開発用コンピューターにツールをインストールします。
4. SQL Server インスタンスでエンクレーブの種類を構成します。
5. エンクレーブ対応キーをプロビジョニングします。
6. 機密データを含む列を暗号化します。

> [!NOTE]
> テスト環境を設定し、SSMS でセキュリティで保護されたエンクレーブが設定された Always Encrypted の機能を試す方法の手順を説明したチュートリアルについては、「[Tutorial: Getting started with Always Encrypted with secure enclaves using SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)」 (チュートリアル: SSMS を使用するセキュリティで保護されたエンクレーブが設定された Always Encrypted の概要) を参照してください。

## <a name="configure-your-environment"></a>環境を構成する

Always Encrypted にセキュリティで保護されたエンクレーブを使用するには、Windows Server 2019 プレビュー、SQL Server Management Studio (SSMS) 18.0、.NET Framework などのいくつかのコンポーネントが環境に必要です。 以下のセクションでは、必要なコンポーネントを入手するための詳細を説明し、リンクを示します。

### <a name="sql-server-computer-requirements"></a>SQL Server コンピューターの要件

SQL Server を実行しているコンピューターには、次のオペレーティング システムと SQL Server バージョンが必要です。

*SQL Server*:

- [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] 以降

*Windows*:

- Windows 10 Enterprise バージョン 1809
- Windows Server DataCenter (半期チャネル) バージョン 1809
- Windows Server 2019 DataCenter

> [!IMPORTANT]
> SQL Server コンピューターは、HGS によって構成証明された、保護されたホストとして構成する必要があります。 TPM 構成証明は、運用環境用の推奨されるエンクレーブの構成証明方法であり、SQL Server は仮想マシンではなく物理マシン上で実行する必要があります。 仮想マシンは、運用前環境にのみ適しています。

### <a name="hgs-computer-requirements"></a>HGS コンピューターの要件

テスト中とプロトタイプ作成中は、1 台の HGS コンピューターで十分です。 運用環境では、3 台のコンピューターによる Windows フェールオーバー クラスターをお勧めします。

Windows ホスト ガーディアン サービス (HGS) は、SQL Server と同じコンピューター上ではなく、別の HGS コンピューターにインストールする必要があります。 HGS コンピューターの要件と設定の詳細については、「[Setting up the Host Guardian Service for Always Encrypted in SQL Server (SQL Server で Always Encrypted 用ホスト ガーディアン サービスを設定する)](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server)」を参照してください。


### <a name="determine-your-attestation-service-url"></a>構成証明サービスの URL を決定する

構成証明サービスの URL を決定するには、ツールとアプリケーションを構成する必要があります。

1. 管理者として SQL Server コンピューターにサインインします。
2. PowerShell を管理者として実行します。
3. [Get-HGSClientConfiguration](https://docs.microsoft.com/powershell/module/hgsclient/get-hgsclientconfiguration) を実行します。
4. AttestationServerURL プロパティを書き留めて保存します。 これは `https://x.x.x.x/Attestation` のようになります。

### <a name="install-tools"></a>ツールをインストールする

クライアント/開発用コンピューターに次のツールをインストールします。

1. [.NET Framework 4.7.2](https://www.microsoft.com/net/download/dotnet-framework-runtime)。
2. [SSMS 18.0 以降](../../../ssms/download-sql-server-management-studio-ssms.md)。
3. [SQL Server PowerShell モジュール](../../../powershell/download-sql-server-ps-module.md) バージョン 21.1 以降。
4. [Visual Studio (2017 以降を推奨)](https://visualstudio.microsoft.com/downloads/)。
5. [Developer Pack for .NET Framework 4.7.2](https://www.microsoft.com/net/download/visual-studio-sdks)。
6. [Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider NuGet パッケージ](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) バージョン 2.2.0 以降。
7. [Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders NuGet パッケージ](https://www.nuget.org/packages?q=Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders)。

セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用してアプリケーションを開発するには、Visual Studio プロジェクトで NuGet パッケージを使います。 最初のパッケージは、Azure Key Vault に列マスター キーを格納する場合にのみ必要です。 詳細については、[開発用アプリケーション](#develop-applications-issuing-rich-queries-in-visual-studio)に関するページを参照してください。

### <a name="configure-a-secure-enclave"></a>セキュリティで保護されたエンクレーブを構成する

クライアント/開発用コンピューター上で次の手順を実行します。

1. SSMS を開き、Active Directory (AD) 管理者として SQL Server インスタンスに接続します。
2. セキュリティで保護されたエンクレーブが設定された Always Encrypted がインスタンスでサポートされていることを確認するには、次のクエリを実行します。

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```

    クエリによって、次のような行が返されます。  

    | NAME                           | value | value_in_use |
    | ------------------------------ | ----- | -------------|
    | 列暗号化エンクレーブの型 | 0     | 0            |

3. セキュリティで保護されたエンクレーブの型を VBS エンクレーブに構成します。

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1;
   RECONFIGURE;
   ```

4. SQL Server インスタンスを再起動して、前の変更を反映します。 SSMS でインスタンスを再起動するには、オブジェクト エクスプローラー上でそのインスタンスを右クリックし、[再起動] を選択します。 インスタンスの再起動後に、再接続します。

5. 次のクエリを実行して、セキュア エンクレーブが読み込まれていることを確認します。

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```   

    クエリによって、次のような行が返されます。  

    | NAME                           | value | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | 列暗号化エンクレーブの型 | 1     | 1              |

6. 暗号化された列に対して高度な計算を有効にするには、次のクエリを実行します。

   ```sql
   DBCC traceon(127,-1);
   ```

    > [!NOTE]
    > [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] では、高度な計算が既定で無効になります。 これらは、SQL Server インスタンスを再起動するたびに、上記のステートメントを使用して有効にする必要があります。

## <a name="provision-enclave-enabled-keys"></a>エンクレーブ対応キーをプロビジョニングする

エンクレーブ対応キーを導入しても、[Always Encrypted のキー プロビジョニングとキー管理ワークフロー](overview-of-key-management-for-always-encrypted.md)は基本的に変わりません。 違うのは、列マスター キーのプロビジョニング ワークフローだけです。 キーをエンクレーブ対応とマークすることができます。既定では、列マスター キーはエンクレーブ対応ではありません。 新しい列マスター キーを (SSMS または PowerShell を使用して) エンクレーブ対応に設定すると、次のようになります。

- データベース内の列マスター キー メタデータの `ENCLAVE_COMPUTATIONS` プロパティが設定されます。
- 列マスター キーのプロパティ値 (`ENCLAVE_COMPUTATIONS` の設定を含む) がデジタル署名されます。 ツールによって、実際の列マスター キーを使用して生成された署名がメタデータに追加されます。 署名により、`ENCLAVE_COMPUTATIONS` の設定での悪意のある改ざんが防止されます。 SQL クライアント ドライバーは、エンクレーブの使用を許可する前に署名を検証します。 これにより、セキュリティ管理者は、エンクレーブ内でどの列データを計算できるかを制御できます。

列マスター キーの `ENCLAVE_COMPUTATIONS` プロパティは不変です。 キーがプロビジョニングされた後は変更できません。 ただし、`ENCLAVE_COMPUTATIONS` プロパティの値が元のキーとは異なる新しいキーで、列マスター キーを置き換えることができます。 列マスター キーを置き換えるには、[列マスター キーを交換します](#make-columns-enclave-enabled-by-rotating-their-column-master-key)。 `ENCLAVE_COMPUTATIONS` プロパティの詳細については、「[CREATE COLUMN MASTER KEY](../../../t-sql/statements/create-column-master-key-transact-sql.md)」を参照してください。

エンクレーブ対応列暗号化キーをプロビジョニングするには、列暗号化キーを暗号化する列マスター キーがエンクレーブ対応であることを確認する必要があります。

現在、エンクレーブ対応キーのプロビジョニングには、次の制限が適用されています。

- エンクレーブ対応の列マスター キーは、[Windows 証明書ストア](/windows/desktop/seccrypto/managing-certificates-with-certificate-stores)または [Azure Key Vault](/azure/key-vault/key-vault-whatis/) に格納する必要があります。 他の種類のキー ストア (たとえば、ハードウェア セキュリティ モジュールやカスタム キー ストア) にエンクレーブ対応列マスター キーを格納することは、現在はサポートされていません。

### <a name="provision-enclave-enabled-keys-using-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) を使用してエンクレーブ対応キーをプロビジョニングする

次の手順では、エンクレーブ対応キーを作成します (SSMS 18.0 以降が必要です)。

1. SSMS を使用してデータベースに接続します。
2. **[オブジェクト エクスプローラー]** で、データベースを展開し、 **[セキュリティ]**  >  **[Always Encrypted キー]** に移動します。
3. エンクレーブ対応の列マスター キーをプロビジョニングします。

    1. **[Always Encrypted キー]** を右クリックし、 **[新しい列マスター キー...]** を選択します。
    2. 列マスター キー名を選択します。
    3. **[Windows 証明書ストア -現在のユーザー] または [Windows 証明書ストア - ローカル コンピューター]** か、 **[Azure Key Vault]** を選択します。
    4. **[エンクレーブ計算を許可する]** を選択します。
    5. [Azure Key Vault] を選択した場合は、Azure にサインインし、キー コンテナーを選択します。 Always Encrypted のキー コンテナーを作成する方法について詳しくは、「[Manage your key vaults from Azure portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/)」(Azure portal からキー コンテナーを管理する) を参照してください。
    6. 既にキーが存在する場合はそれを選択します。または、フォームの指示に従って新しいキーを作成します。
    7. **[OK]** をクリックします。

        ![エンクレーブ計算を許可する](./media/always-encrypted-enclaves/allow-enclave-computations.png)

4. 新しいエンクレーブ対応の列暗号化キーを作成します。

    1. **[Always Encrypted キー]** を右クリックし、 **[新しい列の暗号化キー]** を選択します。
    2. 新しい列暗号化キーの名前を入力します。
    3. **[列マスター キー]** ドロップダウンで、前の手順で作成した列マスター キーを選択します。
    4. **[OK]** をクリックします。

### <a name="provision-enclave-enabled-keys-using-powershell"></a>PowerShell を使用してエンクレーブ対応キーをプロビジョニングする

以下のセクションでは、エンクレーブ対応キーをプロビジョニングするための PowerShell スクリプトの例を示します。 セキュリティで保護されたエンクレーブが設定された Always Encrypted に固有の (新しい) 手順が強調表示されます。 PowerShell を使用したプロビジョニング キーの (セキュリティで保護されたエンクレーブが設定された Always Encrypted に固有ではない) 詳細については、「[PowerShell を使用して Always Encrypted キーの構成](configure-always-encrypted-keys-using-powershell.md)」を参照してください。

#### <a name="provisioning-enclave-enabled-keys---windows-certificate-store"></a>エンクレーブ対応キーのプロビジョニング - Windows 証明書ストア

クライアント/開発用コンピューターで Windows PowerShell ISE を開き、次のスクリプトを実行します。

重要なのは、[**New-SqlCertificateStoreColumnMasterKeySettings**](https://docs.microsoft.com/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings) コマンドレットで `-AllowEnclaveComputations` パラメーターを使用することです。

```powershell
# Create a column master key in Windows Certificate Store.
$cert = New-SelfSignedCertificate -Subject "\<Subject Name\>" -CertStoreLocation Cert:CurrentUser\\My -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Provide the server/db name. Modify the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Create a SqlColumnMasterKeySettings object for your column master key
# using the -AllowEnclaveComputations parameter.
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert.Thumbprint -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```

#### <a name="provisioning-enclave-enabled-keys---azure-key-vault"></a>エンクレーブ対応キーのプロビジョニング - Azure Key Vault

クライアント/開発用コンピューターで Windows PowerShell ISE を開き、次のスクリプトを実行します。

**ステップ 1:Azure Key Vault に列マスター キーをプロビジョニングする**

これは、Azure portal を使用して行うこともできます。 詳細は、「[Manage your key vaults from Azure portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/)」(Azure portal からキー コンテナーを管理する) を参照してください。


```powershell
Import-Module Az
Connect-AzAccount

# User values
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"

# Set the context to the specified subscription.
$azureCtx = Set-AzContext -SubscriptionId $SubscriptionId

# Create a new resource group - skip, if your desired group already exists.
New-AzResourceGroup -Name $resourceGroup -Location $azureLocation

# Create a new key vault - skip if your vault already exists.
New-AzKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation

# Grant yourself permissions needed to create and use the column master key.
Set-AzKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, list, update, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account

# Create a column master key in Azure Key Vault.
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination "Software"
```

**ステップ 2:データベースに列マスター キーのメタデータを作成し、列暗号化キーを作成し、データベースに列暗号化キーのメタデータを作成します。**


```powershell
# Import the SqlServer module.
Import-Module "SqlServer" -Version

# Connect to your database. Provide the server and db name. If needed, modify the connection string.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Authenticate to Azure before calling New-SqlAzureKeyVaultColumnMasterKeySettings,
# because -AllowEnclaveComputations causes a call to Azure Key Vault
# to generate the signature of the column master key.
Add-SqlAzureAuthenticationContext -Interactive

# Create a SqlColumnMasterKeySettings object for your column master key.
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyURL $akvKey.ID -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```

## <a name="identify-enclave-enabled-keys-and-columns"></a>エンクレーブ対応のキーと列を特定する

データベースに構成されている列マスター キーを一覧表示するには、[sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md) カタログ ビュー (SSMS など) のクエリを実行します。 新しい **allow_enclave_computations** 列では、列マスター キーがエンクレーブ対応かどうかが示されます。

```sql
SELECT name, allow_enclave_computations
FROM sys.column_master_keys;
```

エンクレーブ対応列暗号化キーで暗号化された列暗号化キーは、エンクレーブ対応です。 エンクレーブ対応列暗号化キーを返すため、次のクエリでは [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md)、[sys.column_encryption_key_values](../../system-catalog-views/sys-column-encryption-key-values-transact-sql.md)、[sys.column_encryption_keys](../../system-catalog-views/sys-column-encryption-keys-transact-sql.md) が結合されています。

```sql
SELECT cek.name AS [cek_name]
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
FROM sys.column_master_keys cmk
JOIN sys.column_encryption_key_values cekv
   ON cmk.column_master_key_id = cekv.column_master_key_id
JOIN sys.column_encryption_keys cek
   ON cekv.column_encryption_key_id = cek.column_encryption_key_id;
```

エンクレーブ対応キーで暗号化された列は、エンクレーブ対応です。 エンクレーブ対応の列を特定するには、次のクエリを使用します。

```sql
SELECT c.name AS column_name
, cek.name AS cek_name
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
from sys.columns c
JOIN sys.column_encryption_keys cek 
ON c.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_encryption_key_values cekv 
ON cekv.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_master_keys cmk 
ON cmk.column_master_key_id = cekv.column_master_key_id;
```

## <a name="manage-collations"></a>照合順序を管理する

Always Encrypted では、照合順序が制限されます。 決定論的な暗号化を使用して暗号化された文字列型の列に対しては、BIN2 以外の照合順序を使用できません。 この制限は、エンクレーブ対応文字列型の列にも適用されます。

ランダム化された暗号化およびエンクレーブ対応列暗号化キーを使用して暗号化された文字列型の列の場合、BIN2 以外の照合順序を使用することができます。 ただし、このような列に対して有効な唯一の新機能はインプレース暗号化です。 高度な計算 (パターン マッチング、比較操作) を有効にするには、暗号化された列で BIN2 照合順序が必要です。

以下の表は、暗号化の種類と照合順序の並べ替え順序に応じてエンクレーブ対応文字列型の列の機能をまとめたものです。

| **照合順序の並べ替え順序** | **決定論的な暗号化** | **ランダム化された暗号化**                 |
| ------------------------ | ---------------------------- | ----------------------------------------- |
| **BIN2 以外**             | サポートされていません                | インプレース暗号化                       |
| **BIN2**                 | 等価比較          | インプレース暗号化と高度なコンピューター |

### <a name="determining-and-changing-collations"></a>照合順序の決定と変更

SQL Server では、サーバー、データベース、または列レベルで照合順序を設定できます。 現在の照合順序を決定し、サーバー、データベース、または列レベルで照合順序を変更する方法の一般的な手順については、「[照合順序と Unicode のサポート](../../collations/collation-and-unicode-support.md)」を参照してください。

### <a name="special-considerations-for-non-unicode-string-columns"></a>UNICODE 以外の文字列型の列に関する特殊な考慮事項

(Always Encrypted に関連していない) SQL クライアント ドライバーの制限によって課せられる以下の追加の制限は、UNICODE (ASCII) 以外の文字列に適用されます。 UNICODE 以外 (char、varchar) の文字列型の列に関するデータベースの照合順序を上書きする場合は、列の照合順序がデータベースの照合順序と同じコード ページを使用していることを確認する必要があります。
すべての照合順序とそのコード ページ識別子を一覧表示するには、次のクエリを使用します。

```sql
SELECT [Name]
   , [Description]
   , [CodePage] = COLLATIONPROPERTY([Name], 'CodePage')
FROM ::fn_helpcollations();
```

たとえば、`Chinese_Traditional_Stroke_Order_100_CI_AI_WS` と `Chinese_Traditional_Stroke_Order_100_BIN2` は同じコード ページ (950) ですが、`Chinese_Traditional_Stroke_Order_100_CI_AI_WS` と `Latin1_General_100_BIN2` はコード ページが異なります (それぞれ 950 と 1252)。 前述の制限は、UNICODE (`nchar`、`nvarchar`) 文字列型の列には適用されません。 作成する新しい暗号化された列に対して UNICODE データ型を設定するか、既存の列を暗号化する前に型を UNICODE 型に変更することを検討します。

## <a name="create-a-new-table-with-enclave-enabled-columns"></a>エンクレーブ対応列を使用して新しいテーブルを作成する

[CREATE TABLE (Transact-SQL)](../../../t-sql/statements/create-table-transact-sql.md) ステートメントを使用して、暗号化された列を含む新しいテーブルを作成できます。 セキュリティで保護されたエンクレーブが設定された Always Encrypted では、このステートメントの構文は変更されません。

1. SSMS を使用して、データベースに接続し、クエリ ウィンドウを開きます。

     > [!NOTE]
     > このタスクの接続文字列で Always Encrypted を有効にする必要はありません。

2. クエリ ウィンドウで、`CREATE TABLE` ステートメントを発行して新しいテーブルを作成し、暗号化する各列の[列定義](../../../t-sql/statements/alter-table-column-definition-transact-sql.md)で `ENCRYPTED WITH` 句を指定します。 列をエンクレーブ対応にするには、エンクレーブ対応列暗号化キーを指定する必要があります。 また、データベースの既定の照合順序が BIN2 の照合順序でない場合は、文字列型の列に対して BIN2 の照合順序を指定する必要があります。 詳細については、「照合設定の設定」セクションを参照してください。

### <a name="example-of-creating-a-new-table-with-enclave-enabled-columns"></a>エンクレーブ対応列を使用して新しいテーブルを作成する例

以下のステートメントは、2 つの暗号化された列 SSN と Salary がある新しいテーブルを作成します。 CEK1 がエンクレーブ対応列暗号化キーであると仮定すると、列がランダム化された暗号化を使用している場合、SQL Server エンジンは両方の列に対してインプレース暗号化と高度な計算をサポートします。 このステートメントは、UNICODE SSN 列に Latin1\_General\_BIN2 照合順序を設定します。これは、既定のデータベース照合順序が BIN2 Latin1 以外の照合順序であると仮定した場合に必要です。

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [money] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY];
GO
```

## <a name="add-a-new-enclave-enabled-column-to-an-existing-table"></a>新しいエンクレーブ対応列を既存のテーブルに追加する

[ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) / ADD ステートメントを使用して、既存のテーブルに新しい暗号化列を追加することができます。 セキュリティで保護されたエンクレーブが設定された Always Encrypted では、このステートメントの構文は変更されません。

1. SSMS を使用して、データベースに接続し、クエリ ウィンドウを開きます。

   このタスクの接続文字列で Always Encrypted を有効にする必要はありません。

2. クエリ ウィンドウで、[列定義](../../../t-sql/statements/alter-table-column-definition-transact-sql.md)に ENCRYPTED WITH 句を指定し、エンクレーブ対応列暗号化キーを使用して、ADD 句を指定した ALTER TABLE ステートメントを発行します。 また、新しい列が文字列型の列であり、データベースの既定の照合順序が BIN2 の照合順序でない場合は、BIN2 の照合順序を指定する必要があります。 詳細については、「照合設定の設定」セクションを参照してください。

### <a name="example-of-adding-a-new-enclave-enabled-column-to-an-existing-table"></a>新しいエンクレーブ対応列を既存のテーブルに追加する例

CEK1 がエンクレーブ対応列暗号化キーであると仮定すると、以下のステートメントでは、BirthDate という新しい暗号化された列が追加されます。これは、高度なクエリとインプレース暗号化の両方をサポートしています (列にランダム化された暗号化が使用されているため)。

```sql
ALTER TABLE [dbo].[Employees]
ADD [BirthDate] [Date] ENCRYPTED WITH (
COLUMN_ENCRYPTION_KEY = [CEK1],
ENCRYPTION_TYPE = Randomized,
ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL;
```


## <a name="prepare-an-ssms-query-window-with-always-encrypted-enabled"></a>Always Encrypted を有効にして SSMS クエリ ウィンドウを準備する

必要な接続パラメーターを追加してエンクレーブ計算を有効にするには:

1. SSMS を開きます。
2. [サーバーに接続] ダイアログでサーバー名とデータベース名を指定したら、 **[オプション]** をクリックします。 **[Always Encrypted]** タブに移動し、 **[Always Encrypted を有効にする]** を選択し、エンクレーブ構成証明 URL を指定します。
    
    ![列の暗号化の設定](./media/always-encrypted-enclaves/column-encryption-setting.png)

3. [接続] をクリックします。
4. 新しいクエリ ウィンドウを開きます。

また、既にクエリ ウィンドウを開いている場合、次の手順でデータベース接続を更新して Always Encrypted を有効にします。

1. 既存のクエリ ウィンドウの任意の場所を右クリックします。
2. [接続] \> [接続の変更] の順に選択します。
3. **[オプション]** をクリックします。 **[Always Encrypted]** タブに移動し、 **[Always Encrypted を有効にする]** を選択し、エンクレーブ構成証明 URL を指定します。
4. [接続] をクリックします。

## <a name="work-with-encrypted-columns"></a>暗号化された列を使用する

### <a name="encrypt-an-existing-plaintext-column-in-place"></a>既存のプレーンテキスト列をインプレースで暗号化する

エンクレーブ対応列暗号化キーを使用する場合は、[ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) / ALTER COLUMN ステートメントを使用して、既存のプレーンテキスト列をインプレースで暗号化することができます。

エンクレーブ対応ではないキーを使用して列を暗号化するには、SSMS の Always Encrypted ウィザードや SqlServer PowerShell モジュールの Set-SqlColumnEncryption コマンドレットなどのクライアント側ツールを使用する必要があります。 詳細については、次の情報を参照してください。

- [Always Encrypted ウィザード](always-encrypted-wizard.md)
- [PowerShell を使用した列の暗号化の構成](configure-column-encryption-using-powershell.md)


#### <a name="prerequisites-for-encrypting-an-existing-plaintext-column-in-place"></a>既存のプレーンテキスト列をインプレースで暗号化するための前提条件

- 既存の列が暗号化されていない。
- エンクレーブ対応キーをプロビジョニング済みである
- 列マスター キーにアクセスできる。

#### <a name="steps-for-encrypting-existing-plaintext-column-in-place"></a>既存のプレーンテキスト列をインプレースで暗号化するための手順

1. Always Encrypted を有効にして SSMS クエリ ウィンドウを準備し、データベース接続でエンクレーブ計算を有効にします。 詳細については、「[Always Encrypted を有効にして SSMS クエリ ウィンドウを準備する](#prepare-an-ssms-query-window-with-always-encrypted-enabled)」を参照してください。
2. クエリ ウィンドウで、ENCRYPTED WITH 句にエンクレーブ対応列暗号化キーを指定して、ALTER COLUMN 句を指定した ALTER TABLE ステートメントを発行します。 列が文字列型の列 (char、varchar、nchar、nvarchar など) の場合は、照合順序を BIN2 の照合順序に変更する必要があります。 詳細については、「照合設定の設定」セクションを参照してください。
    
    > [!NOTE]
    > 列マスター キーが Azure Key Vault に格納されている場合は、Azure にサインインするように求められることがあります。

3. テーブルにアクセスするすべてのバッチおよびストアド プロシージャのプラン キャッシュをクリアして、パラメーター暗号化情報を更新します。 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > 影響を受けたクエリのプランをキャッシュから削除しないと、暗号化後のクエリの最初の実行が失敗する可能性があります。

    > [!NOTE]
    > `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE` または `DBCC FREEPROCCACHE` を使用してプランのキャッシュをクリアするときは、クエリのパフォーマンスが一時的に低下する可能性があるため、慎重に行ってください。 キャッシュのクリアによる悪影響を最小限に抑えるため、影響を受けるクエリのプランのみを選択して削除することができます。

4.  [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) を呼び出し、[sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) に保存されていて、列の暗号化によって無効にされた可能性のある各モジュール (ストアド プロシージャ、関数、ビュー、トリガー) のパラメーターのメタデータを更新します。

#### <a name="example-of-encrypting-existing-plaintext-column-in-place"></a>既存のプレーンテキスト列をインプレースで暗号化する例

以下の例の前提:

- CEK1 は、エンクレーブ対応列暗号化キーです。

- SSN 列はプレーンテキストであり、現在は Latin1 で BIN2 以外の照合順序を使用しています (たとえば Latin1\_General\_CI\_AI\_KS\_WS)。

このステートメントは、ランダム化された暗号化とエンクレーブ対応列暗号化キーを使用して SSN 列を暗号化します。 また、既定のデータベースの照合順序は、(同じコード ページ内の) 対応する BIN2 の照合順序で上書きされます。

この操作はオンラインで実行されます (ONLINE = ON)。 また、**ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE** を呼び出すと、テーブル スキーマの変更に影響を受けるクエリのプランが再作成されることに注意してください。

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

### <a name="make-an-existing-encrypted-column-enclave-enabled"></a>既存の暗号化された列をエンクレーブ対応にする

エンクレーブ対応ではない既存の列に対してエンクレーブ機能を有効にするには、いくつかの方法があります。 どの方法を選択するかは、いくつかの要因によって決まります。

- **スコープ/粒度:** エンクレーブ機能を有効にする対象が特定の列マスター キーで保護されている列の一部かすべての列か。
- **データ サイズ:** エンクレーブ対応にする列を含むテーブルのサイズ。
- 列の暗号化の種類も変更するか。 高度な計算 (パターン マッチング、比較操作) をサポートしているのは、ランダム化された暗号化のみである点に注意してください。 決定論的な暗号化を使用して列が暗号化されている場合は、ランダム化された暗号化を使用して再暗号化して、エンクレーブの全機能のロックも解除する必要があります。

既存の列のエンクレーブを有効にするには、次の 3 つの方法があります。

#### <a name="option-1-rotate-the-column-master-key-to-replace-it-with-an-enclave-enabled-column-master-key"></a>オプション 1:列マスター キーを交換して、エンクレーブ対応列暗号化キーに置き換えます。
  
- 長所:
  - データを再暗号化する必要がないため、通常は最も速い方法です。 これは、大量のデータを含む列で、すべての列を指定し、高度な計算を有効にする必要があり、既に決定論的な暗号化を使用しているため、再暗号化する必要がない場合にお勧めの方法です。
  - 元の列マスター キーに関連付けられているすべての列暗号化キーとすべての暗号化された列をエンクレーブ対応にするため、多数の列のエンクレーブ機能を有効にすることができます。
  
- 短所:
  - 暗号化の種類を決定論的からランダム化に変更することができないため、決定論的に暗号化された列に対するインプレース暗号化のロックを解除しても、高度な計算が有効になりません。
  - 特定の列マスター キーに関連付けられた列の一部を選択して変換することができません。
  - キー管理のオーバーヘッドが生じます。新しい列マスター キーを作成し、影響を受けた列のクエリを実行するアプリケーションで使用できるようにする必要があります。  

#### <a name="option-2-this-approach-involves-two-steps-1-rotating-the-column-master-key-as-in-option-1-and-2-re-encrypting-a-subset-of-deterministically-encrypted-columns-using-randomized-encryption-to-enable-rich-computations-for-those-columns"></a>オプション 2:この方法には 2 つの手順があります。1) (オプション 1 と同様に) 列マスター キーを交換します。2) ランダム化された暗号化を使用して決定論的に暗号化された列の一部を再暗号化して、それらの列の高度な計算を有効にします。
  
- 長所:
  - インプレースでデータを再暗号化するため、大量のデータを含む決定論的に暗号化された列の高度なクエリを有効にする場合にお勧めの方法です。 手順 1 では、決定論的な暗号化を使用して列のインプレース暗号化が解除されるため、手順 2 はインプレースで実行できます。
  - 多数の列に対してエンクレーブ機能を有効にすることができます。
  
- 短所:
  - 特定の列マスター キーに関連付けられた列の一部を選択して変換することができません。
  - キー管理のオーバーヘッドが生じます。新しい列マスター キーを作成し、影響を受けた列のクエリを実行するアプリケーションで使用できるようにする必要があります。

#### <a name="option-3-re-encrypting-selected-columns-with-a-new-enclave-enabled-column-encryption-key-and-randomized-encryption-if-needed-on-the-client-side"></a>オプション 3:(必要な場合) クライアント側で新しいエンクレーブ対応列暗号化キーとランダム化された暗号化を使用して、選択した列を再暗号化します。
  
- 長所 - この方法の場合:
  - 1 列または少数の一部の列に対して選択的にエンクレーブ機能を有効にすることができます。
  - 1 つの手順で決定論的に暗号化された列に対して高度な計算を有効にすることができます。
  - 新しい列マスター キーを作成する必要がないため、アプリケーションへの影響は小さくなります。
  
- 短所:
  - 再暗号化のために列を含むテーブルのコンテンツ全体をデータベースの外部に移動する必要があるため、小さなテーブルの場合にのみお勧めします。

詳細については、以下のセクションを参照してください。
  - [列マスター キーを交換して列をエンクレーブ対応にする](#make-columns-enclave-enabled-by-rotating-their-column-master-key)
  - [インプレースで列を再暗号化する](#re-encrypt-columns-in-place)
  - [クライアント側で列を再暗号化する](#re-encrypt-columns-on-the-client-side)

### <a name="make-columns-enclave-enabled-by-rotating-their-column-master-key"></a>列マスター キーを交換して列をエンクレーブ対応にする

列マスター キーの交換は、既存の列マスター キーを新しい列マスター キーに置き換える処理です。 新しい列マスター キーを使用して、古い列マスター キーに関連付けられた列暗号化キーを再暗号化する処理が含まれます。 このワークフローは、コンプライアンスまたはセキュリティ上の理由 (既存の列マスター キーが侵害された場合) による列マスター キーの置き換えをサポートするために、初期リリースの Always Encrypted から存在しています。

エンクレーブを使用する Always Encrypted によって、列マスター キーの交換ワークフローの新しい目的が追加されます。 古い列マスター キーがエンクレーブ対応ではなく、新しい列マスター キーがエンクレーブ対応であると仮定すると、交換プロセスで、列マスター キーに関連付けられたすべての列暗号化キーが効率的にエンクレーブ対応になります。 列マスター キーの交換にはデータの再暗号化が含まれないため、既存の列についてエンクレーブ機能を有効にする場合にお勧めの推奨プロセスです。

列マスター キーを交換しても、影響を受ける列の暗号化の種類は変更されません。 そのため、決定論的に暗号化された列のインプレース暗号化のロックのみを解除することができます。 決定論的な暗号化を使用して列の高度な計算のロックを解除するには、列マスター キーを交換した後で、(インプレースで) 再暗号化する必要があります。

また、高度な計算のロックを解除するために、必要に応じてランダム化された暗号化を使用して文字列型の列の照合順序を BIN2 の照合順序に変更する必要があります。 詳細については、「照合設定の設定」セクションを参照してください。

関係するキーがエンクレーブ対応かどうかにかかわらず、列マスター キーの交換プロセスは同じです。 列マスター キーの交換方法の詳細については、以下の記事を参照してください。

- [SSMS を使用して列マスター キーを交換する](configure-always-encrypted-using-sql-server-management-studio.md)
- [PowerShell を使用して列マスター キーを交換する](rotate-always-encrypted-keys-using-powershell.md)

参考までに、列マスター キーを交換するサンプル PowerShell スクリプトを以下に示します。

#### <a name="prerequisites-of-rotating-the-column-master-key-for-enclave-enabled-columns"></a>エンクレーブ対応列の列マスター キーを交換する場合の前提条件

- 新しいエンクレーブ対応の列マスター キーをプロビジョニング済みである。
- 古い列マスター キーと新しい列マスター キーの両方にアクセスできる。
- すべて文字列型の列が古い列マスター キーで保護され、BIN2 の照合順序を使用している

> [!NOTE]
> 列マスター キーを交換した後に文字列の照合順序を変更することもできます。

#### <a name="steps-for-rotating-the-column-master-key-for-enclave-enabled-columns"></a>エンクレーブ対応列の列マスター キーを交換する手順

次のスクリプトを Windows PowerShell ISE に貼り付け、\<プレース ホルダー\>を実際の値に置き換えます。

```powershell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Modify server/db name or/and the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " +
$databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Set the names of the old/current column master key and the new/target enclave-enabled column master key. (Change the names, if needed).
$oldCmkName = "<old column master key name>"
$newCmkName = "<new column master key name>"

# Authenticate to Azure. Needed only of either column master key is stored in Azure Key Vault.
Add-SqlAzureAuthenticationContext -Interactive

# Initiate the rotation from the current column master key to the new column master key.
Invoke-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName $oldCmkName
-TargetColumnMasterKeyName $newCmkName -InputObject $database

# Complete the rotation of the old column master key.
Complete-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName
$oldCmkName -InputObject $database

# Remove the old column master key metadata.
Remove-SqlColumnMasterKey -Name $oldCmkName -InputObject $database
```


### <a name="re-encrypt-columns-in-place"></a>インプレースで列を再暗号化する

列をエンクレーブ対応にした後、以下の操作をインプレースで実行できます (エンクレーブ内では、データベースからデータを移動する必要はありません)。

- 定期的なキーの交換を必須にするなどのコンプライアンス規則に従う場合や、セキュリティ上の理由 (列暗号化キーが侵害された場合など) で、列暗号化キーを交換して新しいキーで置き換えます。
- たとえば、決定論的な暗号化からランダム化された暗号化などの暗号化の種類を変更して、列の高度な計算のロックを解除します。

#### <a name="prerequisites-for-re-encrypting-columns-in-place"></a>インプレースで列を再暗号化する場合の前提条件

- 列は、エンクレーブ対応列暗号化キーを使用して暗号化されている。
- 新しいエンクレーブ対応列暗号化キーがプロビジョニング済みである (現在のエンクレーブ対応列暗号化キーを置き換えて列を保護することが目標の場合)。
- 列マスター キーにアクセスできる。

#### <a name="steps-for-re-encrypting-columns-in-place"></a>インプレースで列を再暗号化する手順

1. Always Encrypted を有効にして SSMS クエリ ウィンドウを準備し、データベース接続でエンクレーブ計算を有効にします。 詳細については、「[Always Encrypted を有効にして SSMS クエリ ウィンドウを準備する](#prepare-an-ssms-query-window-with-always-encrypted-enabled)」を参照してください。

2. クエリ ウィンドウで、ENCRYPTED WITH 句に以下を指定して、ALTER COLUMN 句を指定した [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) ステートメントを発行します。
    
    1. 現在のキーを交換している場合は、新しいエンクレーブ対応列暗号化キーの名前。 列の暗号化キーを変更しない場合は、現在のキーの名前を指定する必要があります。
    
    2. 変更する場合は、新しい暗号化の種類。 暗号化の種類を変更しない場合は、現在の暗号化の種類を指定する必要があります。
        
       再暗号化する列で、既定のデータベースの照合順序と異なる照合順序 (BIN2) が使用されている場合は、COLLATE 句を含めて列の定義に現在の照合順序を指定する必要があります (照合順序を同じに保つため)。
        
       > [!NOTE]
       > 列マスター キーが Azure Key Vault に格納されている場合は、Azure にサインインするように求められることがあります。

3. テーブルにアクセスするすべてのバッチおよびストアド プロシージャのプラン キャッシュをクリアして、パラメーター暗号化情報を更新します。 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > 影響を受けたクエリのプランをキャッシュから削除しないと、暗号化後のクエリの最初の実行が失敗する可能性があります。

    > [!NOTE]
    > ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE または DBCC FREEPROCCACHE を使用してプランのキャッシュをクリアするときは、クエリのパフォーマンスが一時的に低下する可能性があるため、慎重に行ってください。 キャッシュのクリアによる悪影響を最小限に抑えるため、影響を受けるクエリのプランのみを選択して削除することができます。

4.  [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) を呼び出し、[sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) に保存されていて、列の再暗号化によって無効にされた可能性のある各モジュール (ストアド プロシージャ、関数、ビュー、トリガー) のパラメーターのメタデータを更新します。

#### <a name="examples-of-re-encrypting-columns-in-place"></a>インプレースで列を再暗号化する例

CEK1 という名前のエンクレーブ対応列暗号化キー、および決定論的な暗号化を使用して SSN 列が暗号化されており、列レベルで設定されている現在の照合順序が Latin1\_General\_BIN2 であると仮定すると、以下のステートメントで、ランダム化された暗号化されたキーと同じキーを持つ列が再暗号化されます。

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

CEK1 という名前のエンクレーブ対応列暗号化キーを使用して SSN 列が暗号化されており、既定のデータベース照合順序は BIN2 の照合順序である (さらに列レベルでは設定されていない) と仮定すると、以下のステートメントで、CEK2 という新しいエンクレーブ対応キーを使用して列が再暗号化されます (暗号化の種類は変更されません)。

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION\_TYPE = Deterministic
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

CEK1 という名前のエンクレーブ対応列暗号化キーを使用して SSN 列が暗号化されており、既定のデータベース照合順序は BIN2 の照合順序である (さらに列レベルでは設定されていない) と仮定すると、以下のステートメントで、新しいエンクレーブ対応キーとランダム化された暗号化を使用して列が再暗号化されます。 さらに、この操作はオンライン モードで行われます。

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL 
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

### <a name="re-encrypt-columns-on-the-client-side"></a>クライアント側で列を再暗号化する

列を再暗号化 (および暗号化または復号化) する従来の方法では、Always Encrypted ウィザードや PowerShell などのクライアント側ツールが使用されます。 (再暗号化対象の) 列を含むテーブルが小さく、新しいエンクレーブ対応キーを使用して列を再暗号化して暗号化の種類を (決定論的からランダム化に) 変更することが目的の場合を除き、通常、この方法の使用は勧められません。

ランダム化された暗号化を使用する列を再暗号化する場合、高度な計算のロックを解除するために、場合によっては照合順序を BIN2 の照合順序に (再暗号化の前または後に) 変更する必要があります。 詳細については、「照合設定の設定」セクションを参照してください。

詳細については、次の情報を参照してください。

  - SSMS を使用して列暗号化キーを交換する: <https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-wizard>
  - PowerShell を使用して列暗号化キーを交換する: <https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-column-encryption-using-powershell>

### <a name="decrypt-a-column-in-place"></a>列をインプレースで復号化する

エンクレーブ対応列暗号化キーを使用して列が暗号化されている場合は、ALTER TABLE ステートメントを使用してインプレースで復号化する (プレーンテキスト列に変換する) ことができます。 さらに、この操作はオンライン モードで行われます。

#### <a name="prerequisites-for-decrypting-a-column-in-place"></a>列をインプレースで復号化するための前提条件

- 列は、エンクレーブ対応列暗号化キーを使用して暗号化されている。
- 列マスター キーにアクセスできる。

#### <a name="steps-for-decrypting-a-column-in-place"></a>列をインプレースで復号化する手順

1. Always Encrypted を有効にして SSMS クエリ ウィンドウを準備し、データベース接続でエンクレーブ計算を有効にします。 詳細については、「[Always Encrypted を有効にして SSMS クエリ ウィンドウを準備する](#prepare-an-ssms-query-window-with-always-encrypted-enabled)」を参照してください。

2. クエリ ウィンドウで、ENCRYPTED WITH 句を**指定せずに**、ALTER COLUMN 句で目的の列構成を指定した [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) ステートメントを発行します。
    
    > [!NOTE]
    > 列マスター キーが Azure Key Vault に格納されている場合は、Azure にサインインするように求められることがあります。

3. テーブルにアクセスするすべてのバッチおよびストアド プロシージャのプラン キャッシュをクリアして、パラメーター暗号化情報を更新します。 

    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```

    > [!NOTE]
    > 影響を受けたクエリのプランをキャッシュから削除しないと、暗号化後のクエリの最初の実行が失敗する可能性があります。

    > [!NOTE]
    > ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE または DBCC FREEPROCCACHE を使用してプランのキャッシュをクリアするときは、クエリのパフォーマンスが一時的に低下する可能性があるため、慎重に行ってください。 キャッシュのクリアによる悪影響を最小限に抑えるため、影響を受けるクエリのプランのみを選択して削除することができます。

4. [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) を呼び出し、[sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) に保存されていて、列の復号化によって無効にされた可能性のある各モジュール (ストアド プロシージャ、関数、ビュー、トリガー) のパラメーターのメタデータを更新します。

#### <a name="example-for-decrypting-a-column-in-place"></a>列をインプレースで復号化する例

SSN 列が暗号化され、現在の照合順序が列レベルで Latin1\_General\_BIN2 に設定されていると仮定すると、次のステートメントで列が復号化されます (照合順序は変更されません。または、同じステートメントで BIN2 以外の照合順序などに照合順序を変更することもできます)。

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

## <a name="issue-rich-queries-against-encrypted-columns-using-ssms"></a>SSMS を使用して暗号化された列に対して高度なクエリを発行する

エンクレーブ対応列に対して高度なクエリを試す最も簡単な方法は、Always Encrypted のパラメーター化を有効にした SSMS クエリ ウィンドウを使用するものです。 この SSMS の便利な機能の詳細については、以下を参照してください。

- [Always Encrypted のパラメーター化 - 暗号化された列の挿入、更新、フィルター処理に SSMS を使用する](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)
- [暗号化された列のクエリ](configure-always-encrypted-using-sql-server-management-studio.md#querying-encrypted-columns)

### <a name="prerequisites-for-issuing-rich-queries-against-encrypted-columns-using-ssms"></a>SSMS を使用して暗号化された列に対して高度なクエリを発行するための前提条件

- クエリ対象の列がエンクレーブ対応である。
- 1 つまたは複数の列マスター キーにアクセスできる。

### <a name="steps-for-issuing-rich-queries-against-encrypted-columns-using-ssms"></a>SSMS を使用して暗号化された列に対して高度なクエリを発行する手順

1. Always Encrypted を有効にして SSMS クエリ ウィンドウを準備し、データベース接続でエンクレーブ計算を有効にします。 詳細については、「[Always Encrypted を有効にして SSMS クエリ ウィンドウを準備する](#prepare-an-ssms-query-window-with-always-encrypted-enabled)」を参照してください。

2. Always Encrypted のパラメーター化を有効にします。

    1. SSMS のメイン メニューから **[クエリ]** を選択します。
    2. **[クエリ オプション...]** を選択します。
    3. **[実行]**  >  **[詳細]** の順に移動します。
    4. [Always Encrypted のパラメーター化を有効にする]をオンまたはオフにします。
    5. [OK] をクリックします。

3. 暗号化された列に対して高度な計算を使用するクエリを作成して実行します。 クエリ内で、暗号化された列をターゲットとする各値について Transact-SQL 変数を宣言する必要があります。 変数では、インラインの初期化を使用する必要があります (SET ステートメントでは設定できません)。

    > [!NOTE]
    > 列マスター キーが Azure Key Vault に格納されている場合は、Azure にサインインするように求められることがあります。

### <a name="example-of-rich-queries-against-encrypted-columns"></a>暗号化された列に対する高度なクエリの例

この例では、次のステートメントを使用して作成されたテーブルがデータベースに含まれているとします。

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [money] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY];
GO
```

CEK1 は、エンクレーブ対応列暗号化キーです。

そのテーブルに対する、パラメーター化のガイドラインに準拠したクエリの例を次に示します。

```sql
DECLARE @SSNPattern [char](11) = '%1111%'
DECLARE @MinSalary [money] = 1000
SELECT *
FROM [dbo].[Employees]
WHERE SSN LIKE @SSNPattern
    AND [Salary] >= @MinSalary;
GO;
```

## <a name="create-and-use-indexes-on-enclave-enabled-columns-using-randomized-encryption"></a>ランダム化された暗号化を使用してエンクレーブ対応の列でインデックスを作成して使用する

ランダム化された暗号化を使用するエンクレーブ対応の列でのインデックスには暗号化されたインデックスのキー値が格納されますが、値はプレーンテキストに基づいて格納されるため、SQL Server エンジンでは、次のようなインデックスの作成または更新に関連するすべての操作に対して、エンクレーブを使用する必要があります。

- インデックスの作成または再構築。
- (インデックス付け/暗号化された列が含まれる) テーブルの行の挿入、更新、または削除。インデックスのインデックス キーの挿入または削除がトリガーされます。
- インデックスの整合性のチェックが含まれる DBCC コマンドの実行。たとえば、[DBCC CHECKDB (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) や [DBCC CHECKTABLE (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)。
- SQL Server でインデックスへの変更を元に戻す必要がある場合の、データベースの復旧 (たとえば、SQL Server が失敗して再起動した後) (詳細については、以下を参照してください)。

上記のすべての操作では、インデックス キーを復号化できるように、エンクレーブがインデックス付き列の列暗号化キーを持っている必要があります。 一般に、エンクレーブでは、2 つの方法のいずれかで列暗号化キーを取得できます。
- クライアント アプリケーションから直接。
- 列暗号化キーのキャッシュから。

### <a name="invoke-indexing-operations-with-column-encryption-keys-provided-directly-by-the-client"></a>クライアントによって直接提供された列暗号化キーでインデックス付け操作を呼び出す

このインデックス付け操作呼び出し方法が動作するためには、インデックスに対する操作をトリガーするクエリを発行するアプリケーションで、次のことが必要です。

- データベース接続で Always Encrypted とエンクレーブ計算の両方が有効になっているデータベースに接続します。
- アプリケーションは、インデックス付き列の列暗号化キーを保護している列マスター キーにアクセスできる必要があります。

SQL Server エンジンで、アプリケーションのクエリが解析されて、クエリを実行するためには暗号化された列のインデックスを更新する必要があることがわかった場合、セキュリティで保護されたチャネル経由でエンクレーブに必要な CEK を提供するよう、クライアント ドライバーに対して指示されます。 これは、インデックス付け操作が含まれないクエリの処理の場合に、列暗号化キーをエンクレーブに提供するために使用されるのとまったく同じメカニズムであることに注意してください。

この方法は、接続で Always Encrypted とエンクレーブ計算が有効になっているデータベースに既に接続していて、クエリ処理にエンクレーブを使用しているアプリケーションに対し、暗号化された列でのインデックスの存在を透過的にするのに便利です。 列にインデックスを作成した後、アプリ内のドライバーでは、インデックス付け操作のためにエンクレーブに列暗号化キーが透過的に提供されます。 インデックスを作成すると、アプリケーションでエンクレーブに列暗号化キーを送信する必要があるクエリの数が増える場合があることに注意してください。

この方法の詳しい使用手順については、「[チュートリアル: ランダム化された暗号化を使用してエンクレーブ対応の列でインデックスを作成して使用する](../tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md)」をご覧ください。

### <a name="invoke-indexing-operations-using-cached-column-encryption-keys"></a>キャッシュされた列暗号化キーを使用してインデックス付け操作を呼び出す

クライアント アプリケーションからエンクレーブに列暗号化キーが送信されると (エンクレーブ計算を必要とするクエリの処理のため)、エンクレーブでは (エンクレーブ内に存在し、外部からアクセスできない) 内部キャッシュに列暗号化キーがキャッシュされます。

(同じユーザーまたは異なるユーザーによって使用される) 同じクライアント アプリケーションまたは別のクライアント アプリケーションで、必要な列暗号化を直接提供せずに、インデックスに対する操作がトリガーされると、エンクレーブではキャッシュ内の列暗号化キーが検索されます。 その結果、クライアント アプリケーションでキーを提供しなくても、インデックスに対する操作は成功します。

このインデックス付け操作呼び出し方法が動作するためには、アプリケーションで接続の Always Encrypted を有効にしないでデータベースに接続する必要があり、エンクレーブの内部キャッシュで必要な列暗号化キーを使用できる必要があります。

この操作呼び出し方法は、インデックスに関連しない他の操作については列暗号化キーが必要ないクエリに対してのみサポートされます。 たとえば、暗号化列を含むテーブルに INSERT ステートメントを使用して行を挿入するアプリケーションでは、暗号化列にインデックスがあるかどうかに関係なく、接続文字列で Always Encrypted を有効にしてデータベースに接続する必要があり、キーにアクセスできる必要があります。

この方法は次の場合に便利です。

- ランダム化された暗号化を使用するエンクレーブ対応の列でのインデックスの存在を、プレーンテキストのキーとデータにアクセスできないアプリケーションとユーザーに対して透過的にする。 これにより、暗号化列でインデックスを作成しても、既存のクエリが壊れないことが保証されます。つまり、キーにアクセスできる必要がない暗号化列が含まれるテーブルに対するクエリをアプリケーションで発行している場合、DBA がインデックスを作成した後も、アプリケーションはキーにアクセスできない状態で引き続き実行できます。 たとえば、DBA が暗号化列でインデックスを作成する前に、前の例で使用した **Employees** テーブルに対して次のクエリを実行するアプリケーションについて考えます。 

   ```sql
   DELETE FROM [dbo].[Employees] WHERE [EmployeeID] = 1;
   GO
   ```

   Always Encrypted とエンクレーブ計算が有効になっていない接続でアプリケーションがクエリを送信した場合、暗号化列に対して計算がトリガーされないので、クエリは成功します。 DBA が暗号化列でインデックスを作成した後は、クエリにより、エンクレーブで列暗号化キーが必要なインデックスからのインデックス キーの削除がトリガーされます。 しかし、データ所有者がエンクレーブに対して列暗号化キーを提供している限り、アプリケーションでは同じ接続を通してこのクエリを引き続き実行できます。

- インデックスを管理するときの役割の分離を実現します。それにより、DBA は、機密データにアクセスできなくても、暗号化列のインデックスを作成および変更できます。 

この方法の詳しい使用手順については、「[チュートリアル: ランダム化された暗号化を使用してエンクレーブ対応の列でインデックスを作成して使用する](../tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md)」をご覧ください。

## <a name="develop-applications-issuing-rich-queries-in-visual-studio"></a>Visual Studio で高度なクエリを発行するアプリケーションを開発する

### <a name="set-up-your-visual-studio-project"></a>Visual Studio プロジェクトを設定する

.NET Framework アプリケーションでセキュリティで保護されたエンクレーブが設定された Always Encrypted を使用するには、.NET Framework 4.7.2 をターゲットにしてアプリケーションを構築し、[Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders) と統合する必要があります。 さらに、列マスター キーを Azure Key Vault に格納する場合は、アプリケーションを [Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) バージョン 2.2.0 以降と統合する必要があります。 

1. Visual Studio を開きます。
2. 新しい Visual C\# プロジェクトを作成するか、既存のプロジェクトを開きます。
3. プロジェクトは必ず .NET Framework 4.7.2 以降をターゲットにします。 ソリューション エクスプローラーでプロジェクトを右クリックし、[プロパティ] を選択し、[ターゲット フレームワーク] を [.NET Framework 4.7.2] に設定します。

4. **[ツール]** (メイン メニュー) > **[NuGet パッケージ マネージャー]**  >  **[パッケージ マネージャー コンソール]** に移動して、次の NuGet パッケージをインストールします。 パッケージ マネージャー コンソールで次のコードを実行します。

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders -IncludePrerelease
   ```

5. Azure Key Vault を使用して列マスター キーを格納する場合は、 **[ツール]** (メイン メニュー) > **[NuGet パッケージ マネージャー]**  >  **[パッケージ マネージャー コンソール]** に移動して、次の NuGet パッケージをインストールします。 パッケージ マネージャー コンソールで次のコードを実行します。

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -IncludePrerelease -Version 2.2.0
   Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
   ```

6. プロジェクトを選択して [インストール] をクリックします。
7. プロジェクト から構成ファイルを開きます (たとえば、App.config、Web.config)。
8. \<configuration\> セクションを見つけて、\<configsections\> セクションを追加または更新します。

   A. \<configuration\> セクションに \<configSections\> セクションが含まれて**いない**場合、\<configuration\> のすぐ下に次のコンテンツを追加します。
   
      ```xml
      <configSections>
         <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
      </configSections>
      ```
   B. \<configruation\> セクションに既に \<configSections\> セクションが含まれている場合、\<configSections\> 内に次の行を追加します。

   ```xml
   <section name="SqlColumnEncryptionEnclaveProviders"  type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data,  Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
   ```

9. configuration セクション内の \<configSections\> の下に次のセクションを追加します。これは構成証明と VBS エンクレーブとの対話に使用されるエンクレーブ プロバイダーに固有のものです。

   ```xml
   <SqlColumnEncryptionEnclaveProviders>
       <providers>
           <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.VirtualizationBasedSecurityEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
       </providers>
   </SqlColumnEncryptionEnclaveProviders>
   ```

単純なコンソール アプリケーションの app.config ファイルの完全な例を次に示します。
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
  </configSections>
  <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.2" />
    </startup>

  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="VBS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider, Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders>
</configuration>
```
### <a name="develop-and-test-your-app"></a>アプリを開発してテストする

Always Encrypted とエンクレーブ計算を使用するには、アプリケーションで接続文字列に次の 2 つのキーワードを指定してデータベースに接続する必要があります: `Column Encryption Setting = Enabled; Enclave Attestation Url=https://x.x.x.x/Attestation` (この xxxx には ip、ドメインなどを指定できます)。

さらに、アプリケーションは、Always Encrypted を使用するアプリケーションに適用される一般的なガイドラインに従う必要があります。たとえば、アプリケーションは、アプリケーション クエリで参照されるデータベース列に関連付けられた列マスター キーにアクセスできる必要があります。

Always Encrypted を使用した .NET Framework アプリケーションの開発の詳細については、以下の記事を参照してください。

- [Always Encrypted と .NET Framework Data Provider を使用して開発する](develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Always Encrypted:SQL Database で機密データを保護し、暗号キーを Azure Key Vault に格納する](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

#### <a name="example-of-simple-application"></a>簡単なアプリケーションの例

以下のコードは、次のスキーマを持つテーブルに対して LIKE クエリを発行する C\# コンソール アプリの単純な例です。

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [money] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY];
GO
```

CEK1 は、エンクレーブ対応列暗号化キーであると想定されています。

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.SqlClient;
using System.Data;
namespace ConsoleApp1
{
   class Program
   {
      static void Main(string\[\] args)
   {

   string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = https://10.193.16.185/Attestation/attestationservice.svc/signingCertificates; Integrated Security = true";

using (SqlConnection connection = new SqlConnection(connectionString))
{
   connection.Open();
   
   SqlCommand cmd = connection.CreateCommand();
   cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";
   
   SqlParameter paramSSNPattern = cmd.CreateParameter();
   
   paramSSNPattern.ParameterName = @"@SSNPattern";
   paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
   paramSSNPattern.Direction = ParameterDirection.Input;
   paramSSNPattern.Value = "%1111";
   paramSSNPattern.Size = 11;
   
   cmd.Parameters.Add(paramSSNPattern);
   
   SqlParameter MinSalary = cmd.CreateParameter();
   
   MinSalary.ParameterName = @"@MinSalary";
   MinSalary.DbType = DbType.Currency;
   MinSalary.Direction = ParameterDirection.Input;
   MinSalary.Value = 900;
   
   cmd.Parameters.Add(MinSalary);
   cmd.ExecuteNonQuery();
   
   SqlDataReader reader = cmd.ExecuteReader();
   while (reader.Read())
   
   {
     Console.WriteLine(reader);
     Console.WriteLine(reader\[0\] + ", " + reader\[1\] + ", " + reader\[2\] + ", " + reader\[3\]);
   }

   Console.ReadKey();

   }
  }
 }
}
```
