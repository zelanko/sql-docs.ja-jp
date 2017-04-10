---
title: "SQL Server インポートおよびエクスポート ウィザードを起動する | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server インポートおよびエクスポート ウィザード"
  - "SQL Server インポートおよびエクスポート ウィザードの起動"
  - "インポートおよびエクスポート ウィザード"
  - "インポートおよびエクスポート ウィザードの起動"
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 112
---
# SQL Server インポートおよびエクスポート ウィザードを起動する
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインポート/エクスポート ウィザードは次のいずれかの方法で開始できます。
-   サポートされているデータ ソースとの間でインポートまたはエクスポートを実行するには、[スタート メニュー](#startStart)または[コマンド プロンプト](#startCmd)から。
-   SQL Server との間でインポートまたはエクスポートするには、[SQL Server Management Studio (SSMS)](#startSSMS) から。
-   SQL Server Integration Services プロジェクトを開いている場合、[SQL Server Data Tools (SSDT) がインストールされている Visual Studio](#startVS) から。

このトピックでは、ウィザードの**起動**方法のみを説明します。
-   ウィザードの概要をお探しの場合は、「[SQL Server でサポートされるインポートとエクスポートのデータ ソース](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。
-   ウィザードの手順に関する情報をお探しの場合、コンテンツ ナビゲーション メニューで必要なページを選択してください。 ウィザードのページごとに別のドキュメント ページがあります。 または、ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。

**ウィザードを取得します。** ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「[SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。  

## <a name="a-namestartstarta-start-the-wizard-from-the-start-menu"></a><a name="startStart"></a> [スタート] メニューからウィザードを起動する  
1.  **[スタート]** ボタンをクリックし、**[すべてのアプリ]** をクリックします。
2.  **Microsoft SQL Server 2016** を見つけ、展開します。
3.  以下のいずれかのオプションをクリックします。
  
    -   **SQL Server 2016 データのインポートおよびエクスポート (64 ビット)**
          
    -   **SQL Server 2016 データのインポートおよびエクスポート (32 ビット)**  
  
データ ソースに 32 ビットのデータ プロバイダーが必要であることがわかっていない限り、64 ビット バージョンのウィザードを実行してください。
 
![ウィザードの起動 (スタート)](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="a-namestartcmda-start-the-wizard-from-the-command-prompt"></a><a name="startCmd"></a> コマンド プロンプトからウィザードを起動する  
コマンド プロンプト ウィンドウで、次のいずれかの場所から **DTSWizard.exe** を実行します。  
  
-   64 ビット バージョンの場合、**C:\Program Files\Microsoft SQL Server\130\DTS\Binn** を選択します。  
  
-   32 ビット バージョンの場合、**C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn** を選択します。  
  
データ ソースに 32 ビットのデータ プロバイダーが必要であることがわかっていない限り、64 ビット バージョンのウィザードを実行してください。

![ウィザードの起動 (cmd)](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="a-namestartssmsa-start-the-wizard-from-sql-server-management-studio-ssms"></a><a name="startSSMS"></a> SQL Server Management Studio (SSMS) からウィザードを起動する  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。
2.  **[データベース]**を展開します。
3.  データベースを右クリックします。
4.  **[タスク]** にカーソルを合わせます。
5.  以下のいずれかのオプションをクリックします。
  
    -   **データのインポート**
      
    -   **データのエクスポート**  

![ウィザードの起動 (SSMS)](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

SQL Server をインストールしていない場合、あるいは SQL Server をインストールしているが、SQL Server Management Studio をインストールしていない場合、「[SQL Server Management Studio (SSMS) のダウンロード](https://msdn.microsoft.com/library/mt238290.aspx)」を参照してください。
    
## <a name="a-namestartvsa-start-the-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a><a name="startVS"></a> SQL Server Data Tools (SSDT) で Visual Studio からウィザードを起動する  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がインストールされている Visual Studio で、Integration Services プロジェクトを開いている状態で、次のいずれかを実行します。  
  
-   **[プロジェクト]** メニューの **[SSIS インポートおよびエクスポート ウィザード]** をクリックします。 

    ![ウィザードの起動 (プロジェクト)](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \- または -
    
-   ソリューション エクスプローラーで、**[SSIS パッケージ]** フォルダーを右クリックし、**[SSIS インポートおよびエクスポート ウィザード]** をクリックします。

    ![ウィザードの起動 (パッケージ)](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Visual Studio がインストールされていない場合、あるいは Visual Studio がインストールされているが、SQL Server Data Tools がインストールされていない場合、「[SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。 

## <a name="get-help-while-the-wizard-is-running"></a>ウィザードの実行中にヘルプを得る
> [!TIP] ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。   

 ## <a name="whats-next"></a>次の操作  
 ウィザードを起動すると、最初のページは **[SQL Server インポートおよびエクスポート ウィザードへようこそ]** になります。 このページでいかなる操作も必要はありません。 詳細については、「[SQL Server インポートおよびエクスポート ウィザードへようこそ](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)」を参照してください。  
  
  