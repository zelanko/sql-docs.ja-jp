---
title: "手順 2: パッケージ構成の有効化と構成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1a63c43606d2a27da3469c4cedb83654c79c1bf1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-5-2---enabling-and-configuring-package-configurations"></a>レッスン 5-2 - パッケージ構成の有効化と構成
ここでは、パッケージ構成ウィザードを使用することで、プロジェクトをパッケージ配置モデルに変換してパッケージ構成を有効にします。 ここでは、Foreach ループ コンテナーの **Directory** プロパティの構成設定が記述された XML 構成ファイルを生成します。 Directory プロパティの値は、実行時に更新できる新しいパッケージ レベル変数を使って指定します。 また、テスト時に使用する新しいサンプル データを作成します。  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a>Directory プロパティにマップする新しいパッケージ レベル変数を作成するには  
  
1.  **デザイナーで、** [制御フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブの背景をクリックします。 これにより、作成する変数のスコープがこのパッケージに限定されます。  
  
2.  [ [!INCLUDE[ssIS](../includes/ssis-md.md)] ] メニューの **[変数]**をクリックします。  
  
3.  **[変数]** ウィンドウで、[変数の追加] アイコンをクリックします。  
  
4.  **[名前]** ボックスに「 **varFolderName**」と入力します。  
  
    > [!IMPORTANT]  
    > 変数名では大文字と小文字が区別されます。  
  
5.  **[スコープ]** ボックスにパッケージの名前 (Lesson 5) が表示されていることを確認します。  
  
6.  **変数の** [データ型] `varFolderName` ボックスの値を **[String]**に設定します。  
  
7.  **[制御フロー]** タブに戻り、 **[Foreach File in Folder]** コンテナーをダブルクリックします。  
  
8.  **[Foreach ループ エディター]** の **[コレクション]**ページで、 **[Expressions]**をクリックし、参照ボタン ( **[...]**) をクリックします。  
  
9. **[プロパティ式エディター]**で、 **[プロパティ]** ボックスの一覧内をクリックして **[Directory]**をクリックします。  
  
10. **[式]** ボックスで、参照ボタン (**[...]**) をクリックします。  
  
11. **[式ビルダー]**で [変数] フォルダーを展開し、 **User::varFolderName** 変数を **[式]** ボックスへドラッグします。  
  
12. **[OK]** をクリックして **[式ビルダー]**を閉じます。  
  
13. **[OK]** をクリックして **[プロパティ式エディター]**を閉じます。  
  
14. **[OK]** をクリックし、 **[Foreach ループ エディター]**を閉じます。  
  
### <a name="to-enable-package-configurations"></a>パッケージ構成を有効にするには  
  
1.  **[プロジェクト]**メニューの **[パッケージ配置モデルに変換]**をクリックします。  
  
2.  警告のメッセージで **[OK]** をクリックし、変換が完了したら、 **[パッケージ配置モデルに変換]** ダイアログで **[OK]** をクリックします。  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、**[制御フロー]** タブの背景をクリックします。  
  
4.  **[SSIS]** メニューの **[パッケージ構成]**をクリックします。  
  
5.  **[パッケージ構成オーガナイザー]** ダイアログ ボックスで **[パッケージの構成を有効にする]**をクリックし、 **[追加]**をクリックします。  
  
6.  パッケージ構成ウィザードの初期画面で、**[次へ]** をクリックします。  
  
7.  **[構成の種類の選択]** ページで、 **[構成の種類]** が **[XML 構成ファイル]**に設定されていることを確認します。  
  
8.  **[構成の種類の選択]** ページで **[参照]**をクリックします。  
  
9. **[構成ファイルの場所の選択]** ダイアログ ボックスが開きます。既定の場所はプロジェクト フォルダーです。  
  
10. **[構成ファイルの場所の選択]** ダイアログ ボックスで、 **[ファイル名]** に「 **SSISTutorial**」と入力し、 **[保存]**をクリックします。  
  
11. **[構成の種類の選択]** ページで **[次へ]**をクリックします。  
  
12. **[エクスポートするプロパティの選択]** ページの **[オブジェクト]** ペインで、 **[変数]**、 **[varFolderName]**、 **[Properties]**の順に展開し、 **[Value]**チェック ボックスをオンにします。  
  
13. **[エクスポートするプロパティの選択]** ページで **[次へ]**をクリックします。  
  
14. **[ウィザードの完了]** ページで、作成した構成の構成名を入力します。たとえば、「 **SSIS Tutorial Directory configuration**」と入力します。 ここに入力した構成名が **[パッケージ構成オーガナイザー]** ダイアログ ボックスに表示されます。  
  
15. **[完了]**をクリックします。  
  
16. **[閉じる]**をクリックします。  
  
17. SSISTutorial.dtsConfig という名前の構成ファイルが作成されます。この構成ファイルには、変数の**value** に対応する構成設定が含まれています。また、この変数値により、列挙子の **Directory** プロパティが設定されます。  
  
    > [!NOTE]  
    > 通常、構成ファイルにはパッケージのプロパティに関する複雑な情報が含まれていますが、このチュートリアルでは、次の構成情報のみを使用します:  
    > <Configuration ConfiguredType="Property"  
    > Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType\="String">  
    >  <ConfiguredValue>\<\/ConfiguredValue>  
    > \<\/Configuration>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a>新しいサンプル データ フォルダーを作成して、データを取り込むには  
  
1.  Windows エクスプローラーで、ドライブのルート レベル (C:\\など) に新しいフォルダーを作成します。このフォルダーには「 **New Sample Data**」という名前を付けてください。  
  
2.  コンピューター上でサンプル ファイルを探し、フォルダーから 3 つのファイルをコピーします。  
  
3.  コピーしたファイルを **New Sample Data** フォルダーに貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 3 : Directory プロパティの構成値の変更](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
