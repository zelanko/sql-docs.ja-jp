---
title: "ディメンションの定義 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# ディメンションの定義
この実習では、ディメンション ウィザードを使用して Date ディメンションを構築します。  
  
> [!NOTE]  
> このレッスンを学習するには、レッスン 1 のすべての手順を完了している必要があります。  
  
### ディメンションを定義するには  
  
1.  ソリューション エクスプローラー (Microsoft Visual Studio の右側) で、**[ディメンション]** を右クリックし、**[新しいディメンション]** をクリックします。 ディメンション ウィザードが表示されます。  
  
2.  **[ディメンション ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  **[作成方法の選択]** ページで **[既存のテーブルの使用]** オプションが選択されていることを確認し、**[次へ]** をクリックします。  
  
4.  **[基になる情報の指定]** ページで、**Adventure Works DW 2012** データ ソース ビューが選択されていることを確認します。  
  
5.  **[メイン テーブル]** ボックスの一覧で、**[Date]** を選択します。  
  
6.  **[次へ]**をクリックします。  
  
7.  **[ディメンション属性の選択]** ページで、次の属性の横にあるチェック ボックスをオンにします。  
  
    -   **Date Key**  
  
    -   **Full Date Alternate Key**  
  
    -   **English Month Name**  
  
    -   **Calendar Quarter**  
  
    -   **Calendar Year**  
  
    -   **Calendar Semester**  
  
8.  **Full Date Alternate Key** 属性の **[属性の型]** 列の設定を **Regular** から **Date** に変更します。 これを行うには、**[属性の型]** 列で **[Regular]** をクリックします。 次に、矢印をクリックしてオプションを展開し、 **[Date]** > **[Calendar]** > **[Date]** の順にクリックします。 **[OK]**をクリックします。 次の属性について同じ手順を繰り返し、属性の型を次のように変更します。  
  
    -   **English Month Name** を **Month** に  
  
    -   **Calendar Quarter** を **Quarter** に  
  
    -   **Calendar Year** を **Year** に  
  
    -   **Calendar Semester** を **Half Year** に  
  
9. **[次へ]**をクリックします。  
  
10. **[ウィザードの完了]** ページの [プレビュー] ペインで、**Date** ディメンションとその属性を確認できます。  
  
11. **[完了]** をクリックしてウィザードを終了します。  
  
    ソリューション エクスプローラーでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの **[ディメンション]** フォルダー内に Date ディメンションが表示されます。 開発環境の中央では、ディメンション デザイナーに Date ディメンションが表示されます。  
  
12. **[ファイル]** メニューの **[すべてを保存]**をクリックします。  
  
## このレッスンの次の作業  
[キューブの定義](../analysis-services/defining-a-cube.md)  
  
## 参照  
[多次元モデル内のディメンション](../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)  
[既存のテーブルを使用したディメンションの作成](../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)  
[ディメンション ウィザードを使用したディメンションの作成](../analysis-services/multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
  
