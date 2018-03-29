---
Title: 'Tutorial: Using Templates in SQL Server Management Studio'
description: SSMS 内でのテンプレートの使用に関するチュートリアルです。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。
keywords: SQL Server, SSMS, SQL Server Management Studio, テンプレート
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: 05a9883ff436991e5ee830ce1561ecced0fa9b60
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="tutorial-using-templates-within-sql-server-management-studio"></a>チュートリアル: SQL Server Management Studio 内でテンプレートを使用する
このチュートリアルでは、SQL Server Management Studio (SSMS) 内で使用できる作成済みの Transact-SQL (T-SQL) テンプレートについて説明します。 この記事では、次の内容を学習します。
    - テンプレート ブラウザーを使用して T-SQL スクリプトを生成する
    - 既存のテンプレートを編集する 
    - ディスク上のテンプレートを探す
    - 新しいテンプレートを作成する
   

## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio と SQL Server へのアクセスが必要です。 

- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) をインストールする。

 

## <a name="using-the-template-browser"></a>テンプレート ブラウザーを使用する
このセクションでは、**テンプレート ブラウザー**の場所を探して使う方法を説明します。 

1. SQL Server Management Studio を起動します。
2. **[表示]** メニューの **[テンプレート ブラウザー]** を選択します (Ctrl + Alt + T)。 

    ![テンプレート ブラウザー](media/templates-ssms/templatebrowser.png)
    - **[テンプレート ブラウザー]** の下部には、最近使ったテンプレートも表示されます。

3. 目的のノードを展開し、テンプレートを右クリックして、[開く] を選択します。

    ![テンプレートを開く](media/templates-ssms/opentemplate.png)
    - テンプレートをダブルクリックしても同じ結果になります。

4. T-SQL が既に含まれる新しいクエリ ウィンドウが開きます。 
5. 必要に応じてテンプレートを変更し、クエリを **[実行]** します。
    
    ![DB テンプレートを作成する](media/templates-ssms/createdbtemplate.png)


## <a name="edit-an-existing-template"></a>既存のテンプレートを編集する
**[テンプレート ブラウザー]** では、既存のテンプレートを編集することもできます。  

1. **[テンプレート ブラウザー]** で目的のテンプレートを見つけます
2. テンプレートを右クリックし、**[編集]** を選択します

    ![テンプレートを編集する](media/templates-ssms/edittemplate.png)

3. 表示されるクエリ ウィンドウで必要な変更を行います。
4. **[ファイル]** > **[保存]** (Ctrl + S) の順に選択して、テンプレートを保存します。
5. クエリ ウィンドウを閉じます。
6. 保存したテンプレートを再び開くと、新しい編集で更新されています。
 

## <a name="locate-the-templates-on-disk"></a>ディスク上のテンプレートを探す
テンプレートを開くと、ディスク上でのその場所を確認できます。

1. **[テンプレート ブラウザー]** でテンプレートを選んで、**[編集]** を選択します。
2. **クエリのタイトル**を右クリックして、**[Open Containing Folder]\(含んでいるフォルダーを開く\)** を選択します。 エクスプローラーが開き、テンプレートが格納されているディスク上の場所が示されます。 

    ![ディスク上のテンプレート](media/templates-ssms/templatesondisk.png)
  

## <a name="create-a-new-template"></a>新しいテンプレートを作成する
**[テンプレート ブラウザー]** では、新しいテンプレートを作成することもできます。 以下の手順では、新しいフォルダーを作成し、そのフォルダー内に新しいテンプレートを作成する方法を示します。 ただし、この手順では、既存のフォルダーにカスタム テンプレートを作成することもできます。 

1. **[テンプレート ブラウザー]** を開きます
2. [SQL Server テンプレート] を右クリックし、**[新規]** > **[フォルダー]** の順に選択します 
3. このフォルダーの名前を「**カスタム テンプレート**」に設定します

    ![カスタム テンプレートの作成](media/templates-ssms/creatingcustomtemplate.png)

4. 新しく作成した**カスタム テンプレート** フォルダーを右クリックし、**[新規]** > **[テンプレート]** の順に選択して、テンプレートの名前を指定します。 
 
    ![カスタム テンプレートを作成する](media/templates-ssms/createnewtemplate.png)
   
5. 作成したテンプレートを右クリックして、**[編集]** を選択します。 **[新しいクエリ ウィンドウ]** が開きます。
6. 保存する T-SQL のテキストを入力します。 
7. **[ファイル]** メニューの **[保存]** を選択して、ファイルを保存します
8. 既存の **[クエリ ウィンドウ]** を閉じて、新しいカスタム テンプレートを開きます。 

    

## <a name="next-steps"></a>次の手順
次の記事では、SQL Server Management Studio を使う際の他のヒントとテクニックを示します。 

詳細については、次の記事に進んでください
> [!div class="nextstepaction"]
> [次のステップ ボタン](ssms-tricks.md))
