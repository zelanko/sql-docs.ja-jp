---
title: Azure SQL Database での Transparent Data Encryption | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3551cf4db3ab1b84f04ba13dea414943fbb2ef44
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049782"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Azure SQL Database での Transparent Data Encryption
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] 透過的なデータ暗号化 (プレビュー) では、アプリケーションに変更することがなく、データベース、関連付けられたバックアップ、および静止したトランザクション ログ ファイルのリアルタイムの暗号化と解読を実行することによって、悪意のあるアクティビティの脅威から保護を支援します。  
  
 TDE では、データベース暗号化キーという対称キーを使用してデータベース全体のストレージを暗号化します。 [!INCLUDE[ssSDS](../includes/sssds-md.md)] では、データベース暗号化キーは、組み込みのサーバー証明書によって保護されます。 組み込みのサーバー証明書は、各 [!INCLUDE[ssSDS](../includes/sssds-md.md)] サーバーに対して一意です。 データベースが GeoDR リレーションシップの状態にある場合、データベースは各サーバーで異なるキーによって保護されます。 2 つのデータベースが同じサーバーに接続している場合は、同じ組み込みの証明書を共有します。 [!INCLUDE[msCoName](../includes/msconame-md.md)] は、少なくとも 90 日ごとにこれらの証明書を自動的に回転します。 TDE の一般的な説明については、「 [透過的なデータ暗号化 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。  
  
 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] は、Azure Key Vault と TDE との統合をサポートしていません。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、Key Vault の非対称キーを使用できます。 詳細については、[例 a: Transparent Data Encryption Key Vault からの非対称キーを使用して](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA)を参照してください。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([一部の地域でプレビュー](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))。|  
  
> [!IMPORTANT]  
>  現在、これはプレビュー機能です。 その実装に同意し、承認[!INCLUDE[ssSDS](../includes/sssds-md.md)]を私のデータベースの transparent data encryption がライセンス契約 (エンタープライズ契約、Microsoft Azure 契約、またはマイクロソフト オンライン サブスクリプションでは、プレビューの条項契約書にも適用されるあらゆる[の追加使用条件の Microsoft Azure プレビュー](http://azure.microsoft.com/support/legal/preview-supplemental-terms/)します。  
  
 TDE の状態のプレビューが地理的リージョンのサブセットであっても適用されますのバージョン ファミリ V12[!INCLUDE[ssSDS](../includes/sssds-md.md)]だとして一般に可用性の状態として発表されます。 用に TDE を[!INCLUDE[ssSDS](../includes/sssds-md.md)]までの実稼働データベースで使用するためのものではありません[!INCLUDE[msCoName](../includes/msconame-md.md)]一般に、TDE がプレビューから昇格を発表 詳細については[!INCLUDE[ssSDS](../includes/sssds-md.md)]V12 を参照してください[新機能については Azure SQL Database](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)します。  
  
##  <a name="Permissions"></a> Permissions  
 プレビュー版にサインアップして Azure ポータル経由で、REST API または PowerShell を使用して TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] を使用して TDE を構成するには、以下が必要です。  
  
-   TDE のプレビュー版に既にサインアップしている必要があります。  
  
-   必要があります、データベース暗号化キーを作成する、[!INCLUDE[ssSDS](../includes/sssds-md.md)]管理者またはのメンバーである必要があります、 **dbmanager**マスターの役割がデータベースにあり、**コントロール**データベースに対する権限。  
  
-   ALTER DATABASE ステートメントを SET オプション付きで実行するには、 **dbmanager** ロールのメンバーシップだけが必要です。  
  
##  <a name="Preview"></a> データベースで TDE との有効化の TDE のプレビューにサインアップ  
  
1.  Azure ポータルにアクセスする[ https://portal.azure.com ](https://portal.azure.com)と、Azure 管理者または共同作成者アカウントでサインインします。  
  
2.  左側のバナーで、 **[参照]**、 **[SQL データベース]** の順にクリックします。  
  
3.  左側のウィンドウで選択した **SQL データベース** で、ご使用のユーザー データベースをクリックします。  
  
4.  データベース ブレードで、 **[すべての設定]** をクリックします。  
  
5.  **[設定]** ブレードで、 **[透過的なデータ暗号化 (プレビュー)]** 部分をクリックして **[透過的なデータ暗号化 (プレビュー版)]** ブレードを開きます。 TDE のプレビュー版にまだサインアップしていない場合は、サインアップが完了するまでデータ暗号化設定は無効になります。  
  
6.  **[プレビュー版の使用条件]** をクリックします。  
  
7.  プレビューの条項を読み、条項に同意する場合は、選択、**透過的なデータ encryptionPreview 用語**チェック ボックスをオンにし **[ok]** ページの下部付近で。 返す、**データ encryptionPREVIEW**ブレードで、場所、**データの暗号化** ボタンを有効にするようになりました。  
  
8.  **[データの暗号化 (プレビュー版)]** ブレードで **[データの暗号化]** ボタンを **[オン]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。 **[暗号化の状態]** には、透過的なデータ暗号化のおおよその進行状況が表示されます。  
  
     ![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")  
  
     また、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化の進行状況を監視することもできます。 クエリ、`encryption_state`の列、 [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)ビュー。  
  
##  <a name="Encrypt"></a> Transact-SQL を使用して [!INCLUDE[ssSDS](../includes/sssds-md.md)] で TDE を有効にする  
 次の手順は、既にプレビュー版にサインアップしていることを前提としています。  
  
###  <a name="TsqlProcedure"></a>  
  
1.  管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。  
  
2.  データベース暗号化キーを作成してデータベースを暗号化するには、次のステートメントを実行します。  
  
    ```  
    -- Create the database encryption key that will be used for TDE.  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;  
  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  暗号化の進行状況を監視する[!INCLUDE[ssSDS](../includes/sssds-md.md)]を持つデータベース ユーザー、 **VIEW DATABASE STATE**アクセス許可を問い合わせることができます、`encryption_state`の列、 [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)表示します。  
  
## <a name="enabling-tde-on-sql-database-by-using-powershell"></a>PowerShell を使用して SQL Database で TDE を有効にする  
 Azure PowerShell を使用すると、次のコマンドを実行して TDE を有効または無効にすることができます。 コマンドを実行するには、事前にアカウントを PS ウィンドウに接続する必要があります。 次の手順は、既にプレビュー版にサインアップしていることを前提としています。 PowerShell の詳細については、「 [Azure PowerShell をインストールおよび構成する方法](http://azure.microsoft.com/documentation/articles/powershell-install-configure/)」を参照してください。  
  
1.  TDE を有効にするには、TDE の状態表示に戻り、暗号化のアクティビティを表示します。  
  
    ```  
    PS C:\> Switch-AzureMode -Name AzureResourceManager  
  
    PS C:\> Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    ```  
  
2.  TDE を無効にするには、  
  
    ```  
    PS C:\> Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    PS C:\> Switch-AzureMode -Name AzureServiceManagement  
    ```  
  
##  <a name="Decrypt"></a> TDE で保護されたデータベースの暗号化を解除する: [!INCLUDE[ssSDS](../includes/sssds-md.md)]  
  
#### <a name="to-disable-tde-by-using-the-azure-portal"></a>Azure ポータルを使用して TDE を無効にするには  
  
1.  Azure ポータルにアクセスする[ https://portal.azure.com ](https://portal.azure.com)と、Azure 管理者または共同作成者アカウントでサインインします。  
  
2.  左側のバナーで、 **[参照]**、 **[SQL データベース]** の順にクリックします。  
  
3.  左側のウィンドウで選択した **SQL データベース** で、ご使用のユーザー データベースをクリックします。  
  
4.  データベース ブレードで、 **[すべての設定]** をクリックします。  
  
5.  **[設定]** ブレードで、 **[透過的なデータ暗号化 (プレビュー)]** 部分をクリックして **[透過的なデータ暗号化 (プレビュー版)]** ブレードを開きます。  
  
6.  **[透過的なデータの暗号化 (プレビュー版)]** ブレードで、 **[データの暗号化]** ボタンを **[オフ]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。 **[暗号化の状態]** には、透過的なデータの暗号化解除のおおよその進行状況が表示されます。  
  
     また、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化解除の進行状況を監視することもできます。 クエリ、`encryption_state`の列、 [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)ビュー。  
  
#### <a name="to-disable-tde-by-using-transact-sql"></a>Transact SQL を使用して TDE を無効にするには  
  
1.  管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。  
  
2.  データベースの暗号化を解除するには、次のステートメントを実行します。  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  暗号化の進行状況を監視する[!INCLUDE[ssSDS](../includes/sssds-md.md)]を持つデータベース ユーザー、 **VIEW DATABASE STATE**アクセス許可を問い合わせることができます、`encryption_state`の列、 [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)表示します。  
  
##  <a name="Working"></a> 保護されたデータベースの TDE の使用 [!INCLUDE[ssSDS](../includes/sssds-md.md)]  
 Azure 内での操作用にデータベースの暗号化を解除する必要はありません。 ソース データベースまたはプライマリ データベースの TDE の設定は、ターゲットに透過的に継承されます。 これには次の操作が含まれます。  
  
-   geo リストア  
  
-   セルフ サービスによる特定の時点での復元  
  
-   削除されたデータベースの復元  
  
-   アクティブな Geo_Replication  
  
-   データベースのコピーの作成  
  
##  <a name="Moving"></a> 使用して TDE で保護されたデータベースを移動します。Bacpac ファイル  
 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] ポータルまたは [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインポートおよびエクスポート] ウィザードでデータベースのエクスポート機能を使用して TDE で保護されたデータベースをエクスポートする場合、データベースのコンテンツは暗号化されません。 コンテンツは、暗号化されていない .bacpac ファイルに格納されます。  .bacpac ファイルは必ず適切に保護し、新しいデータベースのインポートが完了したら TDE を有効にしてください。  
  
## <a name="related-sql-server-topic"></a>関連する SQL Server のトピック  
 [EKM を使用して TDE を有効にする](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="see-also"></a>参照  
 [透過的なデータ暗号化 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
