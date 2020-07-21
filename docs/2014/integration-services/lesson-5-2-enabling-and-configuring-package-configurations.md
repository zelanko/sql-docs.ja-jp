---
title: '手順 2: パッケージ構成の有効化と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da51560f2ccfb7bef849f1b191c43f19d35d36ed
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440389"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a>手順 2:パッケージ構成の有効化と構成
  ここでは、パッケージ構成ウィザードを使用することで、プロジェクトをパッケージ配置モデルに変換してパッケージ構成を有効にします。 ここでは、Foreach ループ コンテナーの `Directory` プロパティの構成設定が記述された XML 構成ファイルを生成します。 Directory プロパティの値は、実行時に更新できる新しいパッケージ レベル変数を使って指定します。 また、テスト時に使用する新しいサンプル データを作成します。  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a>Directory プロパティにマップする新しいパッケージ レベル変数を作成するには  
  
1.  **デザイナーで、** [制御フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブの背景をクリックします。 これにより、作成する変数のスコープがこのパッケージに限定されます。  
  
2.  [ [!INCLUDE[ssIS](../includes/ssis-md.md)] ] メニューの **[変数]** をクリックします。  
  
3.  **[変数]** ウィンドウで、[変数の追加] アイコンをクリックします。  
  
4.  **[名前]** ボックスに「 **varFolderName**」と入力します。  
  
    > [!IMPORTANT]  
    >  変数名では大文字と小文字が区別されます。  
  
5.  [**スコープ**] ボックスにパッケージの名前 (レッスン 5) が表示されていることを確認します。  
  
6.  **変数の** [データ型] `varFolderName` ボックスの値を **[String]** に設定します。  
  
7.  **[制御フロー]** タブに戻り、 **[Foreach File in Folder]** コンテナーをダブルクリックします。  
  
8.  [ **Foreach ループエディター**] の [**コレクション**] ページで、[**式**] をクリックし、省略記号ボタン ([. **..])** をクリックします。  
  
9. [**プロパティ式エディター**] で、**プロパティ**リスト内をクリックし、を選択し `Directory` ます。  
  
10. [**式**] ボックスで、省略記号ボタン **([...])** をクリックします。  
  
11. **[式ビルダー]** で [変数] フォルダーを展開し、 **User::varFolderName** 変数を **[式]** ボックスへドラッグします。  
  
12. **[OK]** をクリックして **[式ビルダー]** を閉じます。  
  
13. **[OK]** をクリックして **[プロパティ式エディター]** を閉じます。  
  
14. **[OK]** をクリックし、 **[Foreach ループ エディター]** を閉じます。  
  
### <a name="to-enable-package-configurations"></a>パッケージ構成を有効にするには  
  
1.  **[プロジェクト]** メニューの **[パッケージ配置モデルに変換]** をクリックします。  
  
2.  警告のメッセージで **[OK]** をクリックし、変換が完了したら、 **[パッケージ配置モデルに変換]** ダイアログで **[OK]** をクリックします。  
  
3.  **デザイナーで、** [制御フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブの背景をクリックします。  
  
4.  **[SSIS]** メニューの **[パッケージ構成]** をクリックします。  
  
5.  **[パッケージ構成オーガナイザー]** ダイアログ ボックスで **[パッケージの構成を有効にする]** をクリックし、 **[追加]** をクリックします。  
  
6.  パッケージ構成ウィザードの [ようこそ] ページで、[**次へ**] をクリックします。  
  
7.  **[構成の種類の選択]** ページで、 **[構成の種類]** が **[XML 構成ファイル]** に設定されていることを確認します。  
  
8.  **[構成の種類の選択]** ページで **[参照]** をクリックします。  
  
9. **[構成ファイルの場所の選択]** ダイアログ ボックスが開きます。既定の場所はプロジェクト フォルダーです。  
  
10. **[構成ファイルの場所の選択]** ダイアログ ボックスで、 **[ファイル名]** に「 **SSISTutorial**」と入力し、 **[保存]** をクリックします。  
  
11. **[構成の種類の選択]** ページで **[次へ]** をクリックします。  
  
12. [**エクスポートするプロパティの選択**] ページの [**オブジェクト**] ペインで、[**変数**] を展開し、[ **varfoldername**]、[ **Properties**] の順に展開して、[**値**] を選択します。  
  
13. **[エクスポートするプロパティの選択]** ページで **[次へ]** をクリックします。  
  
14. **[ウィザードの完了]** ページで、作成した構成の構成名を入力します。たとえば、「 **SSIS Tutorial Directory configuration**」と入力します。 ここに入力した構成名が **[パッケージ構成オーガナイザー]** ダイアログ ボックスに表示されます。  
  
15. **[完了]** をクリックします。  
  
16. **[閉じる]** をクリックします。  
  
17. ウィザードによって、Ssistutorial.dtsconfig という名前の構成ファイルが作成されます。この構成ファイルには、変数のの構成設定が含まれています。これにより、 `value` `Directory` 列挙子のプロパティが設定されます。  
  
    > [!NOTE]  
    >  通常、構成ファイルにはパッケージのプロパティに関する複雑な情報が含まれていますが、このチュートリアルでは、次の構成情報のみを使用します:  
    > <Configuration ConfiguredType="Property"  
    > Path = "\ Package. Variables [User:: varFolderName]。プロパティ [値] "ValueType =" 文字列 "\>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > \</Configuration>.  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a>新しいサンプル データ フォルダーを作成して、データを取り込むには  
  
1.  Windows エクスプローラーで、ドライブのルートレベル (C: など \\ ) に、という名前の新しいフォルダーを作成し `New Sample Data` ます。  
  
2.  コンピューター上でサンプル ファイルを探し、フォルダーから 3 つのファイルをコピーします。  
  
3.  フォルダーに、 `New Sample Data` コピーしたファイルを貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 3:Directory プロパティの構成値の変更](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
