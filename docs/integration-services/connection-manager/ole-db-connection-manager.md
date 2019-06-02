---
title: OLE DB 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.oledbconnection.f1
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c455e449ff59296848c7e3f15d07aaee80d415c7
ms.sourcegitcommit: e92ce0f59345fe61c0dd3bfe495ef4b1de469d4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2019
ms.locfileid: "66221157"
---
# <a name="ole-db-connection-manager"></a>OLE DB 接続マネージャー

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  OLE DB 接続マネージャーを使用すると、パッケージは OLE DB プロバイダーを使用してデータ ソースに接続できます。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する OLE DB 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用できます。    
    
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB プロバイダーでは、マルチサブネット フェールオーバー クラスタリングの新しい接続文字列キーワード (MultiSubnetFailover=True) はサポートされません。 詳細については、 [SQL Server リリース ノート](https://go.microsoft.com/fwlink/?LinkId=247824) および www.mattmasson.com のブログ記事「 [AlwaysOn マルチサブネット フェールオーバーと SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)」を参照してください。    
> 
> [!NOTE]
>  データ ソースが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 または [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007 である場合、Excel または Access の以前のバージョンとは異なるデータ プロバイダーが必要になります。 詳細については、「 [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) 」および「 [Access データベースに接続する](../../integration-services/connection-manager/connect-to-an-access-database.md)」を参照してください。    
    
 いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] タスクとデータ フロー コンポーネントは、OLE DB 接続マネージャーを使用します。 たとえば、OLE DB ソースと OLE DB 変換先は、この接続マネージャーを使用してデータの抽出と読み込みを行います。また、SQL 実行タスクは、この接続マネージャーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、クエリを実行できます。    
    
 OLE DB 接続マネージャーは、C++ などの言語を使用するアンマネージ コードで記述されたカスタム タスク内で、OLE DB データ ソースにアクセスするためにも使用されます。    
    
 OLE DB 接続マネージャーをパッケージに追加すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に OLE DB 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの **Connections** コレクションに追加します。    
    
 接続マネージャーの **ConnectionManagerType** プロパティは、 **OLEDB**に設定されます。    
    
 OLE DB 接続マネージャーは、次の方法で構成できます。    
    
-   選択したプロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。    
    
-   プロパイダによっては、接続先のデータ ソースの名前を指定します。    
    
-   選択したプロバイダーに適したセキュリティ資格情報を指定します。    
    
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。    
    
## <a name="logging"></a>ログ記録    
 OLE DB 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、OLE DB 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。 OLE DB 接続マネージャーによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択する必要があります。 詳細については、「 [パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>OLEDB 接続マネージャーの構成    
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [OLE DB 接続マネージャーの構成](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)」を参照してください。 プログラムによって接続マネージャーを構成する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** クラスのドキュメントを参照してください。    
    
## <a name="related-content"></a>関連コンテンツ    
    
-   social.technet.microsoft.com の Wiki の記事「 [SSIS から Oracle への接続](https://go.microsoft.com/fwlink/?LinkId=220670) 」    
    
-   carlprothman.net の [OLE DB プロバイダー用接続文字列](https://go.microsoft.com/fwlink/?LinkId=220744)に関する技術記事    
    
## <a name="configure-ole-db-connection-manager"></a>[OLE DB 接続マネージャーの構成]
  **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用すると、データ ソースへの接続を追加できます。新しい接続を設定するか、既存の接続のコピーを使用できます。  
  
> [!NOTE]  
>  データ ソースが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 である場合、Excel の以前のバージョンとは異なる接続マネージャーが必要になります。 詳細については、「 [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)」を参照してください。  
>   
>  データ ソースが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007 である場合、Access の以前のバージョンとは異なる OLE DB プロバイダーが必要になります。 詳細については、「 [Access データベースに接続する](../../integration-services/connection-manager/connect-to-an-access-database.md)」を参照してください。  
  
 OLE DB 接続マネージャーの詳細については、「 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
### <a name="options"></a>オプション  
 **[データ接続]**  
 一覧から既存の OLE DB データ接続を選択します。  
  
 **[データ接続のプロパティ]**  
 選択した OLE DB データ接続のプロパティとその値を表示します。  
  
 **[新規作成]**  
 **[接続マネージャー]** ダイアログ ボックスを使用して、OLE DB データ接続を作成します。  
  
 **削除**  
 データ接続を選択して **[削除]** ボタンをクリックすると、接続が削除されます。  
  
### <a name="managed-identities-for-azure-resources-authentication"></a>Azure リソース認証用のマネージド ID
[Azure Data Factory 内の Azure-SSIS 統合ランタイム](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime)上で SSIS パッケージを実行しているときは、お使いのデータ ファクトリに関連付けられている[マネージド ID](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity) を Azure SQL Database (または Managed Instance) 認証に使用できます。 この ID を使用して指定したファクトリからデータベースにアクセスし、データベースに、またはデータベースからデータをコピーできます。

Azure SQL Database にマネージド ID 認証を使用するには、以下の手順でデータベースを構成します。

1. **Azure AD でグループを作成します。** マネージド ID をそのグループのメンバーにします。
    
   1. [Azure portal でデータ ファクトリのマネージド ID を確認します](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)。 お使いのデータ ファクトリの **[プロパティ]** に移動します。 **マネージド ID のオブジェクト ID** をコピーします。
    
   1. [Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) モジュールをインストールします。 `Connect-AzureAD` コマンドを使用してサインインします。 次のコマンドを実行してグループを作成し、メンバーとしてマネージド ID を追加します。
      ```powershell
      $Group = New-AzureADGroup -DisplayName "<your group name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "NotSet"
      Add-AzureAdGroupMember -ObjectId $Group.ObjectId -RefObjectId "<your data factory managed identity object ID>"
      ```
    
1. まだ行っていない場合は、Azure portal で Azure SQL サーバーの **[Azure Active Directory 管理者をプロビジョニング](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server)** します。 Azure AD 管理者は、Azure AD ユーザーでも Azure AD グループでもかまいません。 マネージド ID を持つグループに管理者ロールを付与する場合は、ステップ 3 と 4 をスキップします。 管理者は、データベースへのフル アクセスを持ちます。

1. Azure AD グループに対する **[包含データベース ユーザーを作成](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities)** します。 少なくとも ALTER ANY USER アクセス許可を持つ Azure AD ID で、SSMS のようなツールを使用してデータをコピーするデータベースに接続します。 次の T-SQL を実行します。 
    
    ```sql
    CREATE USER [your AAD group name] FROM EXTERNAL PROVIDER;
    ```

1. SQL ユーザーなどに対して通常行っているように、**Azure AD グループに必要なアクセス許可を付与**します。 たとえば、次のコードを実行します。

    ```sql
    ALTER ROLE [role name] ADD MEMBER [your AAD group name];
    ```

Azure SQL Database Managed Instance にマネージド ID 認証を使用するには、以下の手順でデータベースを構成します。
    
1. まだ行っていない場合は、Azure portal でお使いのマネージド インスタンスの **[Azure Active Directory 管理者をプロビジョニング](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance)** します。 Azure AD 管理者は、Azure AD ユーザーでも Azure AD グループでもかまいません。 マネージド ID を持つグループに管理者ロールを付与する場合は、ステップ 2 から 5 をスキップします。 管理者は、データベースへのフル アクセスを持ちます。

1. **[Azure portal でデータ ファクトリのマネージド ID を確認します](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** 。 お使いのデータ ファクトリの **[プロパティ]** に移動します。 (**マネージド ID オブジェクト ID** ではなく) **マネージド ID アプリケーション ID** をコピーします。

1. **データ ファクトリのマネージド ID をバイナリ型に変換します**。 SQL/Active Directory 管理者アカウントで、SSMS などのツールを使用して、マネージド インスタンスの **master** データベースに接続します。 **master** データベースに対して次の T-SQL を実行し、マネージド ID アプリケーション ID をバイナリとして取得します。
    
    ```sql
    DECLARE @applicationId uniqueidentifier = '{your managed identity application ID}'
    select CAST(@applicationId AS varbinary)
    ```

1. Azure SQL Database Managed Instance で**ユーザーとしてデータ ファクトリ マネージド ID を追加**します。 **master** データベースに対して、次の T-SQL を実行します。
    
    ```sql
    CREATE LOGIN [{a name for the managed identity}] FROM EXTERNAL PROVIDER with SID = {your managed identity application ID as binary}, TYPE = E
    ```

1. **データ ファクトリ マネージド ID に必要なアクセス許可を付与**します。 データのコピー元またはコピー先のデータベースに対して、次の T-SQL を実行します。

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE db_owner ADD MEMBER [{the managed identity name}]
    ```

次に、OLE DB 接続マネージャーに対して **OLE DB プロバイダーを構成**します。 これを行うには 2 つのオプションがあります。
    
1. 設計時に構成します。 SSIS デザイナーで、OLE DB 接続マネージャーをダブルクリックして、 **[接続マネージャー]** ウィンドウを開きます。 **[プロバイダー]** ドロップダウン リストで、[ **[Microsoft OLE DB Driver for SQL Server]** ](https://go.microsoft.com/fwlink/?linkid=871294) を選択します。
    > [!NOTE]
    >  ドロップダウン リストの他のプロバイダーでは、マネージド ID 認証がサポートされていない場合があります。
    
1. 実行時に構成します。 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) または [Azure Data Factory の SSIS パッケージの実行アクティビティ](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)を使用してパッケージを実行するときに、OLE DB 接続マネージャーに対する接続マネージャー プロパティ **ConnectionString** を見つけて、接続プロパティ **Provider** を **MSOLEDBSQL** (つまり、Microsoft OLE DB Driver for SQL Server) に更新します。
    ```vb
    Data Source=serverName;Initial Catalog=databaseName;Provider=MSOLEDBSQL;...
    ```

最後に、OLE DB 接続マネージャーに対する**マネージド ID 認証を構成**します。 これを行うには 2 つのオプションがあります。
    
1. 設計時に構成します。 SSIS デザイナーで、OLE DB 接続マネージャーを右クリックし、 **[プロパティ]** をクリックして **[プロパティ] ウィンドウ**を開きます。 プロパティ **ConnectUsingManagedIdentity** を **True** に更新します。
    > [!NOTE]
    >  現在、SSIS パッケージを SSIS デザイナーまたは [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server で実行しているときは、接続マネージャーのプロパティ **ConnectUsingManagedIdentity** が有効になりません (マネージド ID 認証が機能しないことを示します)。

1. 実行時に構成します。 パッケージを SSMS または SQL パッケージの実行アクティビティで実行するときは、OLE DB 接続マネージャーでプロパティ **ConnectUsingManagedIdentity** を **True** に更新します。
    > [!NOTE]
    >  Azure-SSIS 統合ランタイムでは、データベース接続を確立するためにマネージド ID 認証を使用すると、OLE DB 接続マネージャーで事前構成済みの他のすべての認証方法 (統合セキュリティ、パスワードなど) は**オーバーライド**されます。

> [!NOTE]
>  既存のパッケージでマネージド ID 認証を構成するには、[最新の SSIS デザイナー](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)で SSIS プロジェクトを少なくとも 1 回リビルドし、その SSIS プロジェクトを Azure-SSIS 統合ランタイムに再デプロイして、新しい接続マネージャーのプロパティ**ConnectUsingManagedIdentity** が SSIS プロジェクト内のすべての OLE DB 接続マネージャーに自動的に追加されるようにしてください。

## <a name="see-also"></a>参照    
 [OLE DB ソース](../../integration-services/data-flow/ole-db-source.md)     
 [OLE DB 変換先](../../integration-services/data-flow/ole-db-destination.md)     
 [SQL 実行タスク](../../integration-services/control-flow/execute-sql-task.md)     
 [Integration Services &#40;SSIS&#41; の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
