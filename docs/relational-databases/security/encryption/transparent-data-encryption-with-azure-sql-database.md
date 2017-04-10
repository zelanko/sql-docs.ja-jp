---
title: "Azure SQL Database での Transparent Data Encryption | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
  - "MSDN content"
  - "MSDN - SQL DB"
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-database"
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TDE, SQL Database"
  - "暗号化 (SQL Database), TDE"
  - "Transparent Data Encryption, SQL Database"
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Azure SQL Database での Transparent Data Encryption
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx_md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] の Transparent Data Encryption は、データベース、関連するバックアップ、静止したトランザクション ログ ファイルのリアルタイム暗号化および暗号化解除を実行して、悪意のあるアクティビティの脅威から保護するのに役立ちます。アプリケーションに変更を加える必要はありません。  
  
 TDE では、データベース暗号化キーという対称キーを使用してデータベース全体のストレージを暗号化します。 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] では、データベース暗号化キーは、組み込みのサーバー証明書によって保護されます。 組み込みのサーバー証明書は、各 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] サーバーに対して一意です。 データベースが GeoDR リレーションシップの状態にある場合、データベースは各サーバーで異なるキーによって保護されます。 2 つのデータベースが同じサーバーに接続している場合は、同じ組み込みの証明書を共有します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] は、少なくとも 90 日ごとにこれらの証明書を自動的に回転します。 TDE の一般的な説明については、「[Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)」を参照してください。  
  
 [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] は、Azure Key Vault と TDE との統合をサポートしていません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、Key Vault の非対称キーを使用できます。 詳細については、「[Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。  
  
##  <a name="Permissions"></a> 権限  
 Azure ポータル経由で、REST API または PowerShell を使用して TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。  
  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して TDE を構成するには、以下が必要です。  
  
-   ALTER DATABASE ステートメントを SET オプション付きで実行するには、 **dbmanager** ロールのメンバーシップが必要です。  
  
##  <a name="Preview"></a> ポータルを使用してデータベースで TDE を有効にする  
  
1.  Azure ポータル[https://portal.azure.com](https://portal.azure.com)にアクセスして、Azure の管理者または共同作成者のアカウントでサインインします。  
  
2.  左側のバナーで、 **[参照]**、 **[SQL データベース]**の順にクリックします。  
  
3.  左側のウィンドウで選択した **SQL データベース** で、ご使用のユーザー データベースをクリックします。  
  
4.  データベース ブレードで、 **[すべての設定]**をクリックします。  
  
5.  **[設定]** ブレードで、 **[透過的なデータ暗号化]** 部分をクリックして **[透過的なデータ暗号化]** ブレードを開きます。  
  
6.  **[データの暗号化]** ブレードで **[データの暗号化]** ボタンを **[オン]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。 **[暗号化の状態]** には、透過的なデータ暗号化のおおよその進行状況が表示されます。  
  
     ![SQL Database TDE Start Encryption](../../../relational-databases/security/encryption/media/sqldb-tde-encrypt.png "SQL Database TDE Start Encryption")  
  
     また、 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化の進行状況を監視することもできます。 [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) ビューの **encryption_state** 列のクエリを実行します。  
  
##  <a name="Encrypt"></a> Transact-SQL を使用して [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] で TDE を有効にする  
 TDE を有効にする手順は次のとおりです。  
  
###  <a name="TsqlProcedure"></a>  
  
1.  管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。  
  
2.  データベースを暗号化する、次のステートメントを実行します。  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] で暗号化の進行状況を監視するには、**VIEW DATABASE STATE** 権限を持つデータベース ユーザーが [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) ビューの **encryption_state** 列のクエリを実行します。  
  
##  <a name="EncryptPS"></a> PowerShell を使用して [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] で TDE を有効または無効にする  
 Azure PowerShell を使用すると、次のコマンドを実行して TDE を有効または無効にすることができます。 コマンドを実行するには、事前にアカウントを PS ウィンドウに接続する必要があります。 次の例をカスタマイズして、 `ServerName`、 `ResourceGroupName`、 `DatabaseName` の各パラメーターに実際の値を使用してください。 PowerShell の詳細については、「 [Azure PowerShell をインストールおよび構成する方法](http://azure.microsoft.com/documentation/articles/powershell-install-configure/)」を参照してください。  
  
> [!NOTE]  
>  続行するには、Azure PowerShell のバージョン 1.0 をインストールして構成する必要があります。 バージョン 0.9.8 も使用できるものの、推奨されていません。 `PS C:\> Switch-AzureMode -Name AzureResourceManager` コマンドを使用して、AzureResourceManager コマンドレットに切り替える必要があります。  
  
###  <a name="PSlProcedure"></a>  
  
1.  TDE を有効にするには、TDE の状態表示に戻り、暗号化のアクティビティを表示します。  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
    ```  
  
     バージョン 0.9.8 を使用している場合は、Set-AzureSqlDatabaseTransparentDataEncryption、Get-AzureSqlDatabaseTransparentDataEncryption、Get-AzureSqlDatabaseTransparentDataEncryptionActivity の各コマンドを使用します。  
  
2.  TDE を無効にするには、  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    ```  
  
     バージョン 0.9.8 を使用している場合は、Set-AzureSqlDatabaseTransparentDataEncryption コマンドを使用します。  
  
##  <a name="Decrypt"></a> TDE で保護されたデータベースの暗号化を解除する: [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
  
#### Azure ポータルを使用して TDE を無効にするには  
  
1.  Azure ポータル[https://portal.azure.com](https://portal.azure.com)にアクセスして、Azure の管理者または共同作成者のアカウントでサインインします。  
  
2.  左側のバナーで、 **[参照]**、 **[SQL データベース]**の順にクリックします。  
  
3.  左側のウィンドウで選択した **SQL データベース** で、ご使用のユーザー データベースをクリックします。  
  
4.  データベース ブレードで、 **[すべての設定]**をクリックします。  
  
5.  **[設定]** ブレードで、 **[透過的なデータ暗号化]** 部分をクリックして **[透過的なデータ暗号化]** ブレードを開きます。  
  
6.  **[透過的なデータの暗号化]** ブレードで、**[データの暗号化]** ボタンを **[オフ]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。 **[暗号化の状態]** には、透過的なデータの暗号化解除のおおよその進行状況が表示されます。  
  
     また、 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化解除の進行状況を監視することもできます。 [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) ビューの **encryption_state** 列のクエリを実行します。  
  
#### Transact SQL を使用して TDE を無効にするには  
  
1.  管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。  
  
2.  データベースの暗号化を解除するには、次のステートメントを実行します。  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] で暗号化の進行状況を監視するには、**VIEW DATABASE STATE** 権限を持つデータベース ユーザーが [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) ビューの **encryption_state** 列のクエリを実行します。  
  
##  <a name="Working"></a> で TDE で保護されたデータベースを移動する [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
 Azure 内での操作用にデータベースの暗号化を解除する必要はありません。 ソース データベースまたはプライマリ データベースの TDE の設定は、ターゲットに透過的に継承されます。 これには次の操作が含まれます。  
  
-   geo リストア  
  
-   セルフ サービスによる特定の時点での復元  
  
-   削除されたデータベースの復元  
  
-   アクティブな Geo_Replication  
  
-   データベースのコピーの作成  
  
 [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] ポータルまたは [[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインポートおよびエクスポート] ウィザードでデータベースのエクスポート機能を使用して TDE で保護されたデータベースをエクスポートする場合、データベースのエクスポートされるコンテンツは暗号化されません。 このエクスポートされたコンテンツは、暗号化されていない .bacpac ファイルに保存されます。 .bacpac ファイルは必ず適切に保護し、新しいデータベースのインポートが完了したら TDE を有効にしてください。 
 
 たとえば、.bacpac ファイルをオンプレミスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からエクスポートする場合、新しいデータベースのインポートされるコンテンツは自動的に暗号化されません。 同様に、.bacpac を [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] からオンプレミスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にエクスポートする場合も、新しいデータベースは自動的に暗号化されません。  
 
 1 つの例外は、[!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] からエクスポートおよび Azure SQL Database にエクスポートする場合です。新しいデータベースで TDE は有効になりますが、.bacpac ファイル自体は暗号化されません。
  
## 関連する SQL Server のトピック  
 [EKM の使用による TDE の有効化](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## 参照  
 [透過的なデータ暗号化 &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql.md)  
  
  