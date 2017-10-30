---
title: "SQL Server の起動をインポートおよびエクスポート ウィザード |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 4fd91a36594a8d0d50e3f4eb8490497d6fe0e172
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="start-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードを起動する

 > SQL Server の以前のバージョンに関連するコンテンツでは、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](https://msdn.microsoft.com/en-US/library/ms140052(SQL.120).aspx)です。

開始、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からデータをインポートし、任意のサポートされているデータ ソースにデータをエクスポートするには、インポートおよびエクスポート ウィザードでは、このトピックで説明した方法のいずれか。

> [!IMPORTANT]
> このトピックでは、ウィザードの **起動** 方法のみを説明します。 他のものを探しの場合は、次を参照してください。[関連のタスクおよびコンテンツ](#related)です。

ウィザードを起動することができます。
-   サポートされているデータ ソースとの間でインポートまたはエクスポートを実行するには、 [スタート メニュー](#startStart)」を参照してください。
-   サポートされているデータ ソースとの間でインポートまたはエクスポートを実行するには、 [コマンド プロンプト](#startCmd)」を参照してください。 
-   SQL Server との間でインポートまたはエクスポートするには、 [SQL Server Management Studio (SSMS)](#startSSMS)」を参照してください。
-   SQL Server との間でインポートまたはエクスポートするには、 [SQL Server Data Tools (SSDT) がインストールされている Visual Studio](#startVS)」を参照してください。

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>前提条件、お使いのコンピューターにインストールされているウィザードとは
ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「 [SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。

> [!NOTE]
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するのには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのインストールのみです。

## <a name="startStart"></a> スタート メニュー  
### <a name="start-the-sql-server-import-and-export-wizard-from-the-start-menu"></a>[スタート] メニューから、SQL Server インポートおよびエクスポート ウィザードを起動します。
1.  **開始**] メニューの [検索し、展開**Microsoft SQL Server 2016**です。
3.  以下のいずれかのオプションをクリックします。
  
    -   **SQL Server 2016 データのインポートおよびエクスポート (64 ビット)**
          
    -   **SQL Server 2016 データのインポートおよびエクスポート (32 ビット)**  
  
    データ ソースに 32 ビットのデータ プロバイダーが必要であることがわかっていない限り、64 ビット バージョンのウィザードを実行してください。
 
    ![ウィザードの起動 (スタート)](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="startCmd"></a> Command prompt
### <a name="start-the-sql-server-import-and-export-wizard-from-the-command-prompt"></a>コマンド プロンプトから SQL Server インポートおよびエクスポート ウィザードを起動します。  
コマンド プロンプト ウィンドウで、次のいずれかの場所から **DTSWizard.exe** を実行します。  
  
-   64 ビット バージョンの場合、**C:\Program Files\Microsoft SQL Server\130\DTS\Binn** を選択します。  
  
-   32 ビット バージョンの場合、**C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn** を選択します。  
  
データ ソースに 32 ビットのデータ プロバイダーが必要であることがわかっていない限り、64 ビット バージョンのウィザードを実行してください。

![ウィザードの起動 (cmd)](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="startSSMS"></a> SQL Server Management Studio (SSMS)
### <a name="start-the-sql-server-import-and-export-wizard-from-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) からの SQL Server インポートおよびエクスポート ウィザードを開始します。    
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。
    
2.  **[データベース]**を展開します。
3.  データベースを右クリックします。
4.  **[タスク]**にカーソルを合わせます。
5.  以下のいずれかのオプションをクリックします。
  
    -   **データのインポート**
      
    -   **データのエクスポート**  

    ![ウィザードの起動 (SSMS)](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

SQL Server をインストールしていない場合、あるいは SQL Server をインストールしているが、SQL Server Management Studio をインストールしていない場合、「[SQL Server Management Studio (SSMS) のダウンロード](../../ssms/download-sql-server-management-studio-ssms.md)」を参照してください。
  
## <a name="startVS"></a>Visual Studio
### <a name="start-the-sql-server-import-and-export-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a>Visual Studio と SQL Server Data Tools (SSDT) からの SQL Server インポートおよびエクスポート ウィザードを開始します。 
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]がインストールされている Visual Studio で、Integration Services プロジェクトを開いている状態で、次のいずれかを実行します。 
  
-   **[プロジェクト]** メニューの **[SSIS インポートおよびエクスポート ウィザード]**をクリックします。 

    ![ウィザードの起動 (プロジェクト)](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \- または -
    
-   ソリューション エクスプローラーで、 **[SSIS パッケージ]** フォルダーを右クリックし、 **[SSIS インポートおよびエクスポート ウィザード]**をクリックします。

    ![ウィザードの起動 (パッケージ)](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Visual Studio がインストールされていない場合、あるいは Visual Studio がインストールされているが、SQL Server Data Tools がインストールされていない場合、「[SQL Server Data Tools (SSDT) のダウンロード](../../ssdt/download-sql-server-data-tools-ssdt.md)」を参照してください。

## <a name="get-the-wizard"></a>ウィザードを取得します。
ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「 [SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。

## <a name="get-help-while-the-wizard-is-running"></a>ウィザードの実行中にヘルプを得る
> [!TIP]
> ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。   

 ## <a name="whats-next"></a>次の操作  
 ウィザードを起動すると、最初のページは **[SQL Server インポートおよびエクスポート ウィザードへようこそ]**になります。 このページでいかなる操作も必要はありません。 詳細については、「 [SQL Server インポートおよびエクスポート ウィザードへようこそ](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)」を参照してください。  
  
## <a name="related"></a>関連のタスクとコンテンツ  
 その他の基本的な作業のとおりです。
-   **ウィザードのしくみの簡単な例を参照してください。**

    -   **スクリーン ショットを参照する場合は。** 1 つのページ - この単純なエンド ツー エンドの例を見て[インポートおよびエクスポート ウィザードのこの簡単な例の概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)です。

    -   **ビデオを視聴する場合は。** ウィザードを示し、明確に説明された YouTube かつ簡単にデータを Excel にエクスポートする方法の 4 分のビデオ[、SQL Server インポートおよびエクスポート ウィザードを Excel にエクスポートするを使用して](https://go.microsoft.com/fwlink/?linkid=829049)です。

-   **ウィザードのしくみについて説明します。**

    -   **ウィザードの詳細についてを説明します。** ウィザードの概要をお探しの場合は、「 [SQL Server でサポートされるインポートとエクスポートのデータ ソース](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。

    -   **ウィザードの手順について説明します。** ウィザードの手順についての情報を探している場合は、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードの手順を](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md)です。 ウィザードの各ページ用のドキュメントの別のページもあります。

    -   **データ ソースおよび変換先に接続する方法を説明します。** データに接続する方法についての情報を探している場合は、ここに一覧から、ページを選択[、SQL Server インポートおよびエクスポート ウィザードでデータ ソースへの接続](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md)です。 いくつかの一般的に使用されるデータ ソースごとにドキュメントの別のページがあります。



