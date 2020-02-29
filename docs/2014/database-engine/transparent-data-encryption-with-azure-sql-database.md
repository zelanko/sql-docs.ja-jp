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
ms.openlocfilehash: 541d6d27dc5dbc31dad98840e7ed6654f48a8dfc
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175404"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Azure SQL Database での Transparent Data Encryption
  
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] の透過的なデータの暗号化 (プレビュー版) は、データベース、関連するバックアップ、および静止したトランザクション ログのリアルタイム暗号化および暗号化解除を実行して、悪意のあるアクティビティの脅威から保護するのに役立ちます。アプリケーションに変更を加える必要はありません。

 TDE は、データベース暗号化キーと呼ばれる対称キーを使用してデータベース全体のストレージを暗号化します。 
  [!INCLUDE[ssSDS](../includes/sssds-md.md)] では、データベース暗号化キーは、組み込みのサーバー証明書によって保護されます。 組み込みのサーバー証明書は、各 [!INCLUDE[ssSDS](../includes/sssds-md.md)] サーバーに対して一意です。 データベースが GeoDR リレーションシップに含まれる場合は、サーバーごとに異なるキーで保護されます。 2 つのデータベースが同じサーバーに接続している場合は、同じ組み込みの証明書を共有します。 
  [!INCLUDE[msCoName](../includes/msconame-md.md)] は、少なくとも 90 日ごとにこれらの証明書を自動的に回転します。 TDE の一般的な説明については、「 [透過的なデータ暗号化 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。

 
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] は、Azure Key Vault と TDE との統合をサポートしていません。 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、Key Vault の非対称キーを使用できます。 詳細については、「 [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA)」を参照してください。

||
|-|
|**適用対象**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([一部の地域ではプレビュー](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)版)。|

> [!IMPORTANT]
>  現在、これはプレビュー機能です。 
  [!INCLUDE[ssSDS](../includes/sssds-md.md)] の透過的なデータ暗号化をデータベースに実装すると、使用許諾契約書 (マイクロソフト エンタープライズ契約、Microsoft Azure 契約、マイクロソフト オンライン サブスクリプション契約など) に規定されたプレビューに関する条件、ならびに適用されるあらゆる [Microsoft Azure プレビューの追加使用条件](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)の対象となることを認め、それに同意したことになります。

 TDE のプレビューの状態は、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] のバージョン ファミリ V12 が現在一般提供の段階にあると発表されている地理的リージョンのサブセットにおいても適用されます。 TDE がプレビューから GA に昇格されたことを [!INCLUDE[ssSDS](../includes/sssds-md.md)] が発表するまで、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 用の TDE の実稼働データベースでの使用は想定されていません。 
  [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 の詳細については、「 [Azure SQL Database の新機能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)」をご覧ください。

##  <a name="Permissions"></a> Permissions
 プレビュー版にサインアップして Azure ポータル経由で、REST API または PowerShell を使用して TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。

 
  [!INCLUDE[tsql](../includes/tsql-md.md)] を使用して TDE を構成するには、以下が必要です。

-   TDE のプレビュー版に既にサインアップしている必要があります。

-   データベースの暗号化キーを作成するには、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 管理者であるか、またはマスター データベースの **dbmanager** ロールのメンバーでありかつデータベースに対する **CONTROL** 権限を持っている必要があります。

-   ALTER DATABASE ステートメントを SET オプション付きで実行するには、 **dbmanager** ロールのメンバーシップだけが必要です。

##  <a name="Preview"></a>TDE のプレビューにサインアップして、データベースで TDE を有効にする

1.  Azure Portal にアクセス[https://portal.azure.com](https://portal.azure.com)し、Azure 管理者または共同作成者アカウントでサインインします。

2.  左のバナーの [**参照**] をクリックしてから、[**SQL データベース**] をクリックします。

3.  左側のウィンドウの [**SQL データベース**] を選択して、ユーザー データベースをクリックします。

4.  データベースブレードで、[**すべての設定**] をクリックします。

5.  
  **[設定]** ブレードで、 **[透過的なデータ暗号化 (プレビュー)]** 部分をクリックして **[透過的なデータ暗号化 (プレビュー版)]** ブレードを開きます。 TDE のプレビュー版にまだサインアップしていない場合は、サインアップが完了するまでデータ暗号化設定は無効になります。

6.  
  **[プレビュー版の使用条件]** をクリックします。

7.  プレビューの使用条件を読み、条項に同意する場合は [ **Transparent Data encryptionPreview**の使用条件] チェックボックスをオンにして、ページの下部の近くにある [ **OK** ] をクリックします。 **Data encryptionPREVIEW**ブレードに戻ります。ここで、[**データの暗号化**] ボタンを有効にする必要があります。

8.  
  **[データの暗号化 (プレビュー版)]** ブレードで **[データの暗号化]** ボタンを **[オン]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。 **暗号化の状態**は、透過的なデータ暗号化の進行状況を概算します。

     ![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")

     また、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化の進行状況を監視することもできます。 Dm_database_encryption_keys ビュー `encryption_state`の列に[](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)対してクエリを実行します。

##  <a name="Encrypt"></a>Transact-sql を使用し[!INCLUDE[ssSDS](../includes/sssds-md.md)]てで tde を有効にする
 次の手順は、既にプレビュー版にサインアップしていることを前提としています。

###  <a name="TsqlProcedure"></a>

1.  管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。

2.  データベース暗号化キーを作成してデータベースを暗号化するには、次のステートメントを実行します。

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  での暗号化の進行状況を[!INCLUDE[ssSDS](../includes/sssds-md.md)]監視するために、 **view database STATE**権限を持つデータベース`encryption_state`ユーザーは、 [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)ビューの列に対してクエリを実行できます。

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a>PowerShell を使用して SQL Database で TDE を有効にする
 Azure PowerShell を使用すると、次のコマンドを実行して TDE を有効または無効にすることができます。 コマンドを実行するには、事前にアカウントを PS ウィンドウに接続する必要があります。 次の手順は、既にプレビュー版にサインアップしていることを前提としています。 PowerShell の詳細については、「 [Azure PowerShell をインストールおよび構成する方法](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)」を参照してください。

1.  TDE を有効にするには、TDE の状態表示に戻り、暗号化のアクティビティを表示します。

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  TDE を無効にするには、

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="Decrypt"></a>で TDE で保護されたデータベースの暗号化を解除する[!INCLUDE[ssSDS](../includes/sssds-md.md)]

#### <a name="to-disable-tde-by-using-the-azure-portal"></a>Azure ポータルを使用して TDE を無効にするには

1.  Azure Portal にアクセス[https://portal.azure.com](https://portal.azure.com)し、Azure 管理者または共同作成者アカウントでサインインします。

2.  左のバナーの [**参照**] をクリックしてから、[**SQL データベース**] をクリックします。

3.  左側のウィンドウの [**SQL データベース**] を選択して、ユーザー データベースをクリックします。

4.  データベースブレードで、[**すべての設定**] をクリックします。

5.  
  **[設定]** ブレードで、 **[透過的なデータ暗号化 (プレビュー)]** 部分をクリックして **[透過的なデータ暗号化 (プレビュー版)]** ブレードを開きます。

6.  
  **[透過的なデータの暗号化 (プレビュー版)]** ブレードで、 **[データの暗号化]** ボタンを **[オフ]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。 
  **[暗号化の状態]** には、透過的なデータの暗号化解除のおおよその進行状況が表示されます。

     また、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化解除の進行状況を監視することもできます。 Dm_database_encryption_keys ビュー `encryption_state`の列に[](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)対してクエリを実行します。

#### <a name="to-disable-tde-by-using-transact-sql"></a>Transact SQL を使用して TDE を無効にするには

1.  管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。

2.  データベースの暗号化を解除するには、次のステートメントを実行します。

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  での暗号化の進行状況を[!INCLUDE[ssSDS](../includes/sssds-md.md)]監視するために、 **view database STATE**権限を持つデータベース`encryption_state`ユーザーは、 [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)ビューの列に対してクエリを実行できます。

##  <a name="Working"></a>で TDE で保護されたデータベースを操作する[!INCLUDE[ssSDS](../includes/sssds-md.md)]
 Azure 内での操作用にデータベースの暗号化を解除する必要はありません。 ソース データベースまたはプライマリ データベースの TDE の設定は、ターゲットに透過的に継承されます。 これには次の操作が含まれます。

-   geo リストア

-   セルフ サービスによる特定の時点での復元

-   削除されたデータベースの復元

-   アクティブな Geo_Replication

-   データベースのコピーの作成

##  <a name="Moving"></a>を使用して、TDE で保護されたデータベースを移動します。Bacpac ファイル
 
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] ポータルまたは [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインポートおよびエクスポート] ウィザードでデータベースのエクスポート機能を使用して TDE で保護されたデータベースをエクスポートする場合、データベースのコンテンツは暗号化されません。 コンテンツは、暗号化されていない .bacpac ファイルに格納されます。  .bacpac ファイルは必ず適切に保護し、新しいデータベースのインポートが完了したら TDE を有効にしてください。

## <a name="related-sql-server-topic"></a>関連する SQL Server のトピック
 [EKM を使用して TDE を有効にする](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a>参照
 [Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [Create CREDENTIAL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [create 非対称 KEY &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) create [DATABASE Encryption KEY](/sql/t-sql/statements/create-database-encryption-key-transact-sql) &#40;transact-sql&#41;[alter database &#40;](/sql/t-sql/statements/alter-database-transact-sql) transact-sql&#41;alter database [SET Options](/sql/t-sql/statements/alter-database-transact-sql-set-options) (transact-sql &#40;) を作成&#41;
