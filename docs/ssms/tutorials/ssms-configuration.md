---
Title: 'Tutorial: SQL Server Management Studio components and configuration'
description: SQL Server Management Studio 環境のコンポーネントと基本的な構成オプションについて説明するチュートリアルです。
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/16/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: 173123f180047c35ce93a64928770f55525f651b
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662686"
---
# <a name="tutorial-sql-server-management-studio-components-and-configuration"></a>チュートリアル:SQL Server Management Studio のコンポーネントと構成
このチュートリアルでは、SQL Server Management Studio (SSMS) 内のさまざまなウィンドウ コンポーネントと、ワークスペースに関する基本的な構成オプションについて説明します。 この記事では、次の方法を学習します。 

> [!div class="checklist"]
> * SSMS 環境を構成するさまざまなコンポーネントを確認する
> * 環境レイアウトを変更する/リセットして既定に戻す
> * クエリ エディターを最大化する
> * フォントを変更する 
> * 起動オプションを構成する 
> * 構成をリセットして既定に戻す 

## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio が必要です。  

- [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。

## <a name="sql-server-management-studio-components"></a>SQL Server Management Studio のコンポーネント
このセクションでは、ワークスペースで利用できるさまざまなウィンドウ コンポーネントとその使用方法について説明します。 

- ウィンドウを閉じるには、タイトル バーの右隅にある **[X]** を選択します。 
- ウィンドウをもう一度開くには、**[表示]** メニューでウィンドウを選択します。 

    ![[表示] メニュー](media/ssms-configuration/viewmenu.png)

- **オブジェクト エクスプローラー** (F8):オブジェクト エクスプローラーには、サーバー上のすべてのデータベース オブジェクトがツリー形式で表示されます。 このビューには、SQL Server Database Engine、SQL Server Analysis Services、SQL Server Reporting Services、SQL Server Integration Services のデータベースが含まれています。 オブジェクト エクスプローラーには、それに接続されているすべてのサーバーの情報が含まれています。 
    
    ![オブジェクト エクスプローラー](media/ssms-configuration/objectexplorer.png)
- **クエリ ウィンドウ** (Ctrl + N):**[新しいクエリ]** を選択したら、このウィンドウに Transact-SQL (T-SQL) クエリを入力します。 クエリの結果もここに表示されます。
    
    ![[新しいクエリ] ウィンドウ](media/ssms-configuration/newquery.png)

- **プロパティ** (F4):クエリ ウィンドウが開くと、[プロパティ] ビューが表示されます。 このビューには、クエリの基本的なプロパティが表示されます。 たとえば、クエリの開始時刻、返された行数、接続の詳細などが表示されます。  

    ![Properties](media/ssms-configuration/properties.png)

- **テンプレート ブラウザー** (Ctrl + Alt + T):テンプレート ブラウザーには、さまざまな既成 T-SQL テンプレートが含まれています。 これらのテンプレートを使うと、データベースの作成やバックアップなど、さまざまな機能を実行できます。 

    ![テンプレート ブラウザー](media/ssms-configuration/templates.png)

- **オブジェクト エクスプローラーの詳細** (F7):このビューは、オブジェクト エクスプローラーのビューより詳しくなっています。 オブジェクト エクスプローラーの詳細を使用し、複数のオブジェクトを同時に操作できます。 たとえば、このウィンドウで、複数のデータベースを選択し、その後、全部同時に削除するか、スクリプト化できます。 

    ![[オブジェクト エクスプローラーの詳細]](media/ssms-configuration/objectexplorerdetails.PNG) 
 
    

## <a name="change-the-environment-layout"></a>環境レイアウトの変更 
このセクションでは、さまざまなウィンドウを移動する方法など、環境レイアウトの変更方法について説明します。 

- ウィンドウを移動するには、タイトルを押しながらウィンドウをドラッグします。 
- ウィンドウを固定したり、固定解除したりするには、タイトル バーの画鋲アイコンを選択します。
    
    ![オブジェクトをピン留めする](media/ssms-configuration/pushpin.png)

- 各ウィンドウ コンポーネントにはドロップダウン メニューがあります。これを利用し、さまざまな方法でウィンドウを操作できます。 

    ![ウィンドウのオプション](media/ssms-configuration/windowoptions.png)

- 複数のクエリ ウィンドウが開いているとき、垂直方向または水平方向にタブ化して、一度に複数のクエリ ウィンドウを表示できます。 ウィンドウをタブ化して表示するには、クエリのタイトルを右クリックし、タブ オプションを選択します。 
 
    ![クエリのタブ オプション](media/ssms-configuration/querytabbedoptions.png)

    - これは水平タブ グループです。

      ![水平タブ グループの例](media/ssms-configuration/horizontaltab.png)     
    
    - これは垂直タブ グループです。

      ![垂直タブ グループの例](media/ssms-configuration/verticaltabgroup.png)
        
    - タブをマージするには、クエリのタイトルを右クリックし、**[前のタブ グループへ移動]** または **[次のタブ グループへ移動]** を選択します。
    
      ![クエリ タブをマージする](media/ssms-configuration/mergetabgroups.png)

- 既定の環境レイアウトに戻すには、**[ウィンドウ]** メニューで **[ウィンドウ レイアウトのリセット]** を選択します。
 
    ![元のウィンドウ レイアウトに戻す](media/ssms-configuration/resetwindowlayout.png)
    
## <a name="maximize-query-editor"></a>クエリ エディターを最大化する
クエリ エディターを最大化して全画面表示モードにすることができます。

1. クエリ エディター ウィンドウの任意の場所をクリックします。
2. Shift + Alt + Enter キーを押し、全画面モードと通常モードを切り替えます。 

このショートカット キーは、どのドキュメント ウィンドウでも使用できます。 



## <a name="change-basic-settings"></a>基本設定を変更する
このセクションでは、**[ツール]** メニューから SSMS の基本設定を一部変更する方法について説明します。

  ![[ツール] メニュー](media/ssms-configuration/tools.png)


- 強調表示されているツール バーを変更するには、**[ツール]** > **[カスタマイズ]** の順に選択します。

    ![ツール バーのカスタマイズ](media/ssms-configuration/toolbar.png)

### <a name="change-the-font"></a>フォントを変更する
- フォントを変更するには、**[ツール]** > **[オプション]** > **[フォントおよび色]** の順に選択します。

     ![フォントと色を変更する](media/ssms-configuration/fontsandcolors.png)

### <a name="change-startup-options"></a>スタートアップ オプションの変更
- SSMS を初めて開いたときのワークスペースの外観は、スタートアップ オプションによって決まります。 スタートアップ オプションを変更するには、**[ツール]** > **[オプション]** > **[スタートアップ]** の順に選択します。
 
    ![スタートアップ オプションの変更](media/ssms-configuration/startup.png)

### <a name="reset-settings-to-the-default"></a>設定をリセットして既定値に戻す
- メニューからすべての設定をインポートまたはエクスポートできます。 設定をインポートまたはエクスポートするには、あるいは既定の設定に戻すには、**[ツール]** > **[設定のインポートとエクスポート]** の順に選択します。 

    ![設定のインポートとエクスポート](media/ssms-configuration/settings.png)



## <a name="next-steps"></a>次の手順
次の記事では、SQL Server エラー ログや SQL インスタンス名の検索方法など、SSMS を使用するためのいくつかのヒントとテクニックについて説明します。 

> [!div class="nextstepaction"]
> [SSMS を使用するためのヒントとテクニック](ssms-tricks.md)
 
 




