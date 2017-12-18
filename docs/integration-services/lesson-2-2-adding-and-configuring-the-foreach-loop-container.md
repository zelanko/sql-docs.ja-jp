---
title: "手順 2: Foreach ループ コンテナーの追加と構成 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
caps.latest.revision: "36"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4c5183131893849feca62582a63a0d2c25963631
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="lesson-2-2---adding-and-configuring-the-foreach-loop-container"></a>レッスン 2-2 - Foreach ループ コンテナーの追加と構成
この実習では、フラット ファイルのフォルダー全体にループ機能を付加し、レッスン 1 で使用したデータ フロー変換と同じ変換を各フラット ファイルに適用します。 そのためには、Foreach ループ コンテナーを制御フローに追加して、構成します。  
  
Foreach ループ コンテナーを追加したら、フォルダー内の各フラット ファイルに接続できるようにする必要があります。 フォルダー内のファイルはすべて同じ形式なので、Foreach ループ コンテナーは、どのファイルに接続する場合でも同じフラット ファイル接続マネージャーを使用できます。 このループ コンテナーが使用するフラット ファイル接続マネージャーは、レッスン 1 で作成したフラット ファイル接続マネージャーと同じものです。  
  
レッスン 1 で作成したフラット ファイル接続マネージャーは、現在、1 つのフラット ファイルにのみ接続しています。 フォルダーの各フラット ファイルに 1 つずつ接続するには、Foreach ループ コンテナーとフラット ファイル接続マネージャーをそれぞれ次のように構成します。  
  
-   **ForEach ループ コンテナー:** このコンテナーの列挙値をユーザー定義のパッケージ変数にマップします。 ForEach ループ コンテナーは、このユーザー定義の変数を使用して、フラット ファイル接続マネージャーの **ConnectionString** プロパティを動的に変更しながら、フォルダー内の各フラット ファイルへ順番に接続します。  
  
-   **フラット ファイル接続マネージャー:** ユーザー定義変数を使用して、レッスン 1 で作成した接続マネージャーの **ConnectionString** プロパティに値を設定します。  
  
この実習の手順では、ForEach ループ コンテナーを作成し、ユーザー定義パッケージ変数を使用するように変更する方法、およびデータ フロー タスクをこのループに追加する方法を説明します。 次の実習では、ユーザー定義変数を使用するようにフラット ファイル接続マネージャーを変更します。  
  
上記のように変更した後でこのパッケージを実行すると、Foreach ループ コンテナーによって、Sample Data フォルダー内のすべてのファイルが反復的に処理されます。 条件と一致するファイルが検出されるたびに、ユーザー定義の変数にそのファイルの名前が取り込まれ、Sample Currency Data フラット ファイル接続マネージャーの **ConnectionString** プロパティにマップされます。さらに、そのファイルに対してデータ フローが実行されます。 つまり、Foreach ループの反復処理が実行されるたびに、データ フロー タスクではそれぞれ異なるフラット ファイルが使用されることになります。  
  
> [!NOTE]  
> [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では制御フローとデータ フローが分離されているので、制御フローにループを追加した場合でも、データ フローを修正する必要はありません。 したがって、レッスン 1 で作成したデータ フローは変更する必要がありません。  
  
### <a name="to-add-a-foreach-loop-container"></a>ForEach ループ コンテナーを追加するには  
  
1.  **SQL Server Data Tools**で **[制御フロー]** タブをクリックします。  
  
2.  **SSIS ツールボックス**で **[コンテナー]**を展開し、 **[ForEach ループ コンテナー]** を **[制御フロー]** タブのデザイン画面にドラッグします。  
  
3.  新しく追加した **[ForEach ループ コンテナー]** を右クリックし、 **[編集]**をクリックします。  
  
4.  **[Foreach ループ エディター]** ダイアログ ボックスの **[全般]** ページで、 **[Name]**に「 **Foreach File in Folder**」と入力します。 **[OK]**をクリックします。  
  
5.  [Foreach ループ コンテナー] を右クリックして **[プロパティ]**をクリックし、[プロパティ] ウィンドウで **LocaleID** プロパティが **[英語 (米国)]**に設定されていることを確認します。  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a>ForEach ループ コンテナーの列挙子を構成するには  
  
1.  [Foreach File in Folder] をダブルクリックして、 **[Foreach ループ エディター]**をもう一度開きます。  
  
2.  **[コレクション]**をクリックします。  
  
3.  **[コレクション]** ページで、 **[Foreach File 列挙子]**を選択します。  
  
4.  **[列挙子の構成]** で、 **[参照]**をクリックします。  
  
5.  **[フォルダーの参照]** ダイアログ ボックスで、Currency_*.txt ファイルが保存されている、コンピューター上のフォルダーに移動します。  
  
    このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。 サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。  
  
    1.  「 [Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=275027)をクリックします。 
  
    2.  **[ダウンロード]** タブをクリックします。  
  
    3.  [SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip](http://msftisprodsamples.codeplex.com/downloads/get/596031) ファイルのリンクをクリックします。  
  
6.  **[ファイル]** ボックスに「**Currency_\*.txt**」と入力します。  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a>ユーザー定義の変数に列挙子をマップするには  
  
1.  **[変数のマッピング]**をクリックします。  
  
2.  **[変数のマッピング]** ページで、**[変数]** 列の空いているセルをクリックし、**\<新しい変数…>** をクリックします。  
  
3.  **[変数の追加]** ダイアログ ボックスで、 **[名前]**ボックスに「 **varFileName**」と入力します。  
  
    > [!IMPORTANT]  
    > 変数名では大文字と小文字が区別されます。  
  
4.  **[OK]**をクリックします。  
  
5.  再び **[OK]** をクリックし、 **[Foreach ループ エディター]** ダイアログ ボックスを閉じます。  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a>データ フロー タスクをループに追加するには  
  
-   **[Extract Sample Currency Data]** データ フロー タスクを、名前を変更した Foreach ループ コンテナー **[Foreach File in Folder]**までドラッグします。  
  
## <a name="next-lesson-task"></a>次のレッスンの作業  
[手順 3: フラット ファイル接続マネージャーの変更](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a>参照  
[Foreach ループ コンテナーを構成する](http://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25)  
[パッケージで変数を使用する](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
  
