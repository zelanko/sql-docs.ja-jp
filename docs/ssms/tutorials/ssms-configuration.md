---
Title: 'Tutorial: SQL Server Management Studio Components and Configuration'
description: SQL Server Management Studio 環境のコンポーネントと基本的な構成オプションについて説明するチュートリアルです。
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/16/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: b2c850ac32aebf78441234327ec33b6223dc447b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-sql-server-management-studio-components-and-configuration"></a>チュートリアル: SQL Server Management Studio のコンポーネントと構成
このチュートリアルでは、SQL Server Management Studio (SSMS) 内のさまざまなウィンドウ コンポーネントと、ワークスペースに関する基本的な構成オプションについて説明します。 この記事では、次の内容を学習します。 

> [!div class="checklist"]
> * SSMS 環境を構成するさまざまなコンポーネント
> * 環境レイアウトの変更と、既定値へのリセット
> * クエリ エディターの最大化
> * フォントの変更 
> * 起動オプションの構成 
> * 構成の既定値へのリセット 

## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio が必要です。  

- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。

## <a name="sql-server-management-studio-components"></a>SQL Server Management Studio のコンポーネント
このセクションでは、ワークスペースで使用できるさまざまなウィンドウ コンポーネントと、それぞれの目的について説明します。 

- ウィンドウのすべてのコンポーネントは、タイトル バーの隅にある [X] をクリックして閉じることができ、メイン メニューの **[表示]** ドロップダウンから再び開くことができます。 

    ![[表示] メニュー](media/ssms-configuration/viewmenu.png)

- **[オブジェクト エクスプローラー]** (F8): オブジェクト エクスプローラーには、サーバー上のすべてのデータベース オブジェクトがツリー形式で表示されます。 これには、SQL Server のデータベース エンジン、Analysis Services、Reporting Services、Integration Services のデータベースを含めることができます。 オブジェクト エクスプローラーには、接続しているすべてのサーバーの情報が登録されています。 
    
    ![オブジェクト エクスプローラー](media/ssms-configuration/objectexplorer.png)
- **[クエリ ウィンドウ]** (Ctrl + N): **[新しいクエリ]** をクリックした後、このウィンドウに Transact-SQL (T-SQL) のクエリを入力します。 クエリの結果もここに表示されます。
    
    ![[新しいクエリ] ウィンドウ](media/ssms-configuration/newquery.png)

- **[プロパティ]** (F4): **[クエリ ウィンドウ]** を開いてクエリの基本プロパティを表示すると、見ることができるようになります。 たとえば、クエリの開始時刻、返された行数、接続の詳細などが表示されます。  

    ![[プロパティ]](media/ssms-configuration/properties.png)

- **[テンプレート ブラウザー]** (Ctrl + Alt + T): 作成済みの T-SQL テンプレートをテンプレート ブラウザーで探すことができます。 これらのテンプレートを使うと、データベースの作成やバックアップなど、さまざまな機能を実行できます。 

    ![テンプレート ブラウザー](media/ssms-configuration/templates.png)

- **[オブジェクト エクスプローラーの詳細]** (F7): オブジェクト エクスプローラーの表示内容のより詳細なビューであり、一度に複数のオブジェクトを操作することができます。 たとえば、同時に複数のデータベースを選択して、それらを削除したり、スクリプト化したりできます。 

    ![[オブジェクト エクスプローラーの詳細]](media/ssms-configuration/objectexplorerdetails.PNG) 
 

    

## <a name="change-the-environmental-layout"></a>環境レイアウトを変更する 
ここでは、さまざまなウィンドウの移動など、環境レイアウトの操作について説明します。 

-  ウィンドウの各コンポーネントは、タイトルをクリックしたままドラッグすることで、ウィンドウ内を移動できます。 
- タイトル バーの画鋲アイコンを選択することで、ウィンドウの各コンポーネントをピン留めしたり、ピン留めを外したりできます。
    
    ![オブジェクトのピン留め](media/ssms-configuration/pushpin.png)

- ウィンドウの各コンポーネントのドロップダウン矢印では、さまざまな方法でウィンドウを操作できます。 

    ![ウィンドウのオプション](media/ssms-configuration/windowoptions.png)

- 複数のクエリ ウィンドウを開いた後は、垂直方向または水平方向にタブ化して、一度に複数のクエリ ウィンドウを表示することができます。 そのためには、クエリのタイトルを右クリックして、目的のタブ オプションを選択します。 
 
    ![クエリのタブ オプション](media/ssms-configuration/querytabbedoptions.png)

    - 次に示すのは、**水平タブ グループ**です。![水平タブ グループ](media/ssms-configuration/horizontaltab.png)     
    
    - 次に示すのは、**垂直タブ グループ**です。  
        ![垂直タブ グループ](media/ssms-configuration/verticaltabgroup.png)
        

    - タブを再びマージするには、もう一度クエリのタイトルを右クリックして、**[次のタブ グループへ移動]** または **[前のタブ グループへ移動]** を選択します。
    
        ![クエリ タブをマージする](media/ssms-configuration/mergetabgroups.png)

- 既定の環境レイアウトに戻すには、**[ウィンドウ]** > **[ウィンドウ レイアウトのリセット]** の順にクリックします。
 
    ![元のウィンドウ レイアウトに戻す](media/ssms-configuration/resetwindowlayout.png)
    
## <a name="maximize-query-editor"></a>クエリ エディターを最大化する
クエリ エディターを最大化して全画面表示モードにすることができます。

1. クエリ エディター ウィンドウの任意の場所をクリックします。
2. Shift + Alt + Enter キーを押して、全画面モードと通常モードを切り替えます。 

このショートカット キーは、どのドキュメント ウィンドウでも使用できます。 



## <a name="change-basic-settings"></a>基本設定を変更する
ここでは、SSMS のいくつかの基本設定を変更する方法について説明します。 これらのオプションは、**[ツール]** メニュー オプションにあります。

  ![[ツール] メニュー](media/ssms-configuration/tools.png)


- 強調表示されたツールバーは、**[ツール]** > **[カスタマイズ]** メニューで変更できます。

    ![ツール バーのカスタマイズ](media/ssms-configuration/toolbar.png)

### <a name="change-the-font"></a>フォントを変更する
- フォントは、**[ツール]** > **[オプション]** > **[フォントおよび色]** メニューから変更できます。

     ![フォントおよび色](media/ssms-configuration/fontsandcolors.png)

### <a name="change-the-startup-options"></a>起動オプションを変更する
- SSMS を初めて起動したときのワークスペースの外観は、スタートアップ オプションによって決まります。 これらは、**[ツール]** > **[オプション]** > **[スタートアップ]** メニューから構成できます。
 
    ![スタートアップ オプション](media/ssms-configuration/startup.png)

### <a name="reset-settings-to-default"></a>設定を既定値にリセットする
- これらの設定はすべて、**[ツール]** > **[設定のインポートとエクスポート]** メニューからエクスポートおよびインポートできます。 

    ![インポートとエクスポートの設定](media/ssms-configuration/settings.png)
    - ここではまた、すべての設定を既定値にリセットすることもできます。 


## <a name="next-steps"></a>次の手順
次の記事では、SQL Server エラー ログと SQL インスタンス名の検索など、SSMS を使用するためのいくつかのヒントとテクニックについて説明します。 

詳細については、次の記事に進んでください
> [!div class="nextstepaction"]
> [次のステップ ボタン](ssms-tricks.md)
 
 




