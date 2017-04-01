---
title: "Data Streaming Destination | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 640e6a19-49ae-4ee8-ac07-008370158f0e
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Data Streaming Destination
  **Data Streaming Destination** は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Destination コンポーネントであり、**OLE DB Provider for SSIS** で SSIS パッケージの出力を表形式の結果セットとして利用することを可能にします。 OLE DB Provider for SSIS を利用するリンク サーバーを作成し、そのリンク サーバーで SQL クエリを実行し、SSIS パッケージが返したデータを表示できます。  
  
 下の例のクエリは、SSIS カタログの Power BI フォルダーに SSISPackagePublishing プロジェクトの Package.dtsx パッケージからの出力を返します。 このクエリは [Default Linked Server for Integration Services] という名前のリンク サーバーを利用し、このリンク サーバーは新しい OLE DB Provider for SSIS を利用します。 クエリには、SSIS カタログのフォルダー名、プロジェクト名、パッケージ名が含まれています。 OLE DB Provider for SSIS はクエリに指定されたパッケージを実行し、表形式の結果セットを返します。  
  
```  
SELECT * FROM OPENQUERY([Default Linked Server for Integration Services], N'Folder=Power BI;Project=SSISPackagePublishing;Package=Package.dtsx')  
  
```  
  
## データ フィード パブリッシング コンポーネント  
 データ フィード パブリッシング コンポーネントには、コンポーネントとして、OLE DB Provider for SSIS、Data Streaming Destination、SSIS パッケージ パブリッシュ ウィザードが含まれています。 このウィザードでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース インスタンスで SSIS パッケージを SQL ビューとして公開できます。 このウィザードでは、OLE DB Provider for SSIS を利用するリンク サーバーとリンク サーバーでクエリを表示する SQL ビューを作成できます。 ビューを実行し、表形式のデータ セットとなっている SSIS パッケージからの結果にクエリを実行します。  
  
 SSISOLEDB プロバイダーがインストールされていることを確認するには、SQL Server Management Studio で、 **[サーバー オブジェクト]**、 **[リンク サーバー]**、 **[プロバイダー]**の順に展開し、 **SSISOLEDB** プロバイダーが表示されていることを確認します。 **[SSISOLEDB]** をダブルクリックし、有効になっていなければ、**[InProcess 許可]** を有効にして **[OK]** をクリックします。  
  
## SQL ビューとして SSIS パッケージを公開する  
 以下では、SQL ビューとして SSIS パッケージを公開する手順について説明します。  
  
1.  SSIS パッケージを **Data Streaming Destination** コンポーネントで作成し、SSIS カタログにパッケージを配置します。  
  
2.  C:\Program Files\Microsoft SQL Server\130\DTS\Binn から ISDataFeedPublishingWizard.exe を実行するか、[スタート] メニューからデータ フィード パブリッシング ウィザードを実行し、**SSIS パッケージ パブリッシュ ウィザード**を実行します。  
  
     このウィザードにより、OLE DB Provider for SSIS (SSISOLEDB) を利用するリンク サーバーが作成され、リンク サーバーのクエリを構成する SQL ビューが作成されます。 このクエリには、SSIS カタログのフォルダー名、プロジェクト名、パッケージ名が含まれています。  
  
3.  SQL Server Management Studio で SQL ビューを実行し、SSIS パッケージからの結果を確認します。 このビューにより、作成したリンク サーバーを経由して OLE DB Provider for SSIS にクエリが送信されます。 OLE DB Provider for SSIS はクエリに指定されたパッケージを実行し、表形式の結果セットを返します。  
  
> [!IMPORTANT]  
>  詳細な手順については、「[チュートリアル: SSIS パッケージを SQL ビューとして公開する](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md)」を参照してください。  
  
## Power BI Admin Center を利用し、SSIS パッケージからの出力データを OData フィードとして公開する  
 Power BI Admin Center を利用することで、IT 管理者はオンプレミス データ ソースからのデータを OData フィードとしてユーザーに公開できます。 Power BI Admin Center は既定で SQL Server データ ソースの登録のみを許可します。 ただし、**Data Streaming Destination** と **Microsoft OLE DB Provider for SQL Server Integration Services (SSISOLEDB)** を利用し、ポータルで SSIS パッケージをデータ ソースとして登録し、SSIS パッケージからの結果データを OData フィードとしてユーザーに公開できます。  
  
 Admin Center では、SQL Server データベースでビューを公開できます。 結果として、SSIS Package Publish ウイザード を利用し、SSIS パッケージを SQL ビューとして公開できます。 その後、Power BI Admin Center で OData フィードに含めるビューを選択できます。 データ スチュワードは、Excel 用の Power Query アドインを利用し、SSIS パッケージからのフィードを利用できます。  
  
 詳しいチュートリアルが必要な場合、「 [Publish SSIS Packages as OData Feed Sources (OData フィード ソースとして SSIS パッケージを公開する)](http://go.microsoft.com/fwlink/?LinkID=317367)」を参照してください。  
  
## このセクションの内容  
  
-   [チュートリアル: SSIS パッケージを SQL ビューとして公開する](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md)  
  
-   [Data Streaming Destination を構成する](../../integration-services/data-flow/configure-data-streaming-destination.md)  
  
## 参照  
 [Publish SSIS Packages as OData Feed Sources (OData フィード ソースとして SSIS パッケージを公開する)](http://go.microsoft.com/fwlink/?LinkID=317367)  
  
  