---
title: ADO.NET 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.adonetconnection.f1
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bee4d3ea71aaeacf682a6e90fad91786fa7a0c9c
ms.sourcegitcommit: e92ce0f59345fe61c0dd3bfe495ef4b1de469d4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2019
ms.locfileid: "66221172"
---
# <a name="adonet-connection-manager"></a>ADO.NET 接続マネージャー

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用すると、パッケージは .NET プロバイダーを使用してデータ ソースにアクセスできます。 この接続マネージャーは通常、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]などのデータ ソースへのアクセスに使用されます。また、C# などの言語を使用してマネージド コードに記述されたカスタム タスク内で、OLE DB や XML を介して公開されているデータ ソースにもアクセスできます。  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーをパッケージに追加すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、 **ADO.NET**に設定されます。 **ConnectionManagerType** の値には、接続マネージャーが使用する .NET プロバイダーの名前を含めることができます。  
  
## <a name="adonet-connection-manager-troubleshooting"></a>ADO.NET 接続マネージャーのトラブルシューティング  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択する必要があります。 詳細については、「 [パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーに読み込まれると、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日付データ型のデータは次の表に示す結果を生成します。  
  
|SQL Server データ型|結果|  
|--------------------------|------------|  
|**time**、 **datetimeoffset**|パッケージがパラメーター化 SQL コマンドを使用していない場合、パッケージは失敗します。 パラメーター化 SQL コマンドを使用するには、パッケージで SQL 実行タスクを使用します。 詳細については、「 [SQL 実行タスク](../../integration-services/control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](https://msdn.microsoft.com/library/a3ca65e8-65cf-4272-9a81-765a706b8663)」を参照してください。|  
|**datetime2**|[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーは、ミリ秒の値を切り捨てます。|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の詳細とそれを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型にマッピングする方法については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」と「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="adonet-connection-manager-configuration"></a>ADO.NET 接続マネージャーの構成  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーは、次の方法で構成できます。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
-   選択した .NET プロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。  
  
-   プロパイダによっては、接続先のデータ ソースの名前を指定します。  
  
-   選択したプロバイダーに適したセキュリティ資格情報を指定します。  
  
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーの多くの構成オプションは、接続マネージャーが使用する .NET プロバイダーによって異なります。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[ADO.NET の接続マネージャーの構成]](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="configure-adonet-connection-manager"></a>[ADO.NET の接続マネージャーの構成]
  **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスでは、SqlClient プロバイダーなど、.NET Framework データ プロバイダーを使用してアクセスできるデータ ソースへの接続を追加できます。 接続マネージャーでは、既存の接続を使用することも、新しく接続を作成することもできます。  
  
 ADO.NET 接続マネージャーの詳細については、「 [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md)」を参照してください。  
  
### <a name="options"></a>オプション  
 **[データ接続]**  
 一覧から既存の ADO.NET データ接続を選択します。  
  
 **[データ接続のプロパティ]**  
 選択した ADO.NET データ接続のプロパティとその値を表示します。  
  
 **[新規作成]**  
 **[接続マネージャー]** ダイアログ ボックスを使用して、ADO.NET データ接続を作成します。  
  
 **削除**  
 接続を選択し、 **[削除]** ボタンを使用して削除します。  
  
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

最後に、ADO.NET 接続マネージャーに対する**マネージド ID 認証を構成**します。 これを行うには 2 つのオプションがあります。
    
1. 設計時に構成します。 SSIS デザイナーで、ADO.NET 接続マネージャーを右クリックし、 **[プロパティ]** をクリックして **[プロパティ] ウィンドウ**を開きます。 プロパティ **ConnectUsingManagedIdentity** を **True** に更新します。
    > [!NOTE]
    >  現在、SSIS パッケージを SSIS デザイナーまたは [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server で実行しているときは、接続マネージャーのプロパティ **ConnectUsingManagedIdentity** が有効になりません (マネージド ID 認証が機能しないことを示します)。
    
1. 実行時に構成します。 パッケージを [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) または [Azure Data Factory の SSIS パッケージの実行アクティビティ](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)で実行するときは、ADO.NET 接続マネージャーでプロパティ **ConnectUsingManagedIdentity** を **True** に更新します。
    > [!NOTE]
    >  Azure-SSIS 統合ランタイムでは、データベース接続を確立するためにマネージド ID 認証を使用すると、ADO.NET 接続マネージャーで事前構成済みの他のすべての認証方法 (統合認証、パスワードなど) は**オーバーライド**されます。

> [!NOTE]
>  既存のパッケージでマネージド ID 認証を構成するには、[最新の SSIS デザイナー](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)で SSIS プロジェクトを少なくとも 1 回リビルドし、その SSIS プロジェクトを Azure-SSIS 統合ランタイムに再デプロイして、新しい接続マネージャーのプロパティ**ConnectUsingManagedIdentity** が SSIS プロジェクト内のすべての ADO.NET 接続マネージャーに自動的に追加されるようにしてください。

## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
