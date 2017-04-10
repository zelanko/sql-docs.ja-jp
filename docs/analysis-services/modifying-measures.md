---
title: "メジャーの変更 | Microsoft Docs"
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
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# メジャーの変更
**FormatString** プロパティを使用して書式設定を定義することによって、メジャーの表示方法を調整できます。 この実習では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの通貨メジャーと比率メジャーの書式プロパティを指定します。  
  
### キューブのメジャーを変更するには  
  
1.  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーで、**[キューブ構造]** タブに切り替えます。次に、**[メジャー]** ペインの **[Internet Sales]** メジャー グループを展開し、**[Order Quantity]** を右クリックして、**[プロパティ]** をクリックします。  
  
2.  [プロパティ] ウィンドウの **[自動的に隠す]** 押しピン アイコンをクリックし、[プロパティ] ウィンドウを開いたまま固定します。  
  
    [プロパティ] ウィンドウを開いたままにしておくと、キューブ内のアイテムごとにプロパティを変更する操作が容易になります。  
  
3.  [プロパティ] ウィンドウで、**[FormatString]** ボックスの一覧をクリックし、「**#,#**」と入力します。  
  
4.  **[キューブ構造]** タブのツール バーで、左側の **[メジャー グリッドの表示]** アイコンをクリックします。  
  
    グリッド ビューで複数のメジャーを同時に選択できます。  
  
5.  次のメジャーを選択します。 Ctrl キーを押しながらクリックすると、複数のメジャーを選択できます。  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Sales Amount**  
  
    -   **Tax Amt**  
  
    -   **Freight**  
  
6.  [プロパティ] ウィンドウで、**FormatString** プロパティのセルをクリックして、**[Currency]** を選択します。  
  
7.  [プロパティ] ウィンドウの一番上 (タイトル バーのすぐ下) にあるドロップダウン リストで、**[Unit Price Discount Pct]** メジャーを選択します。次に、**FormatString** プロパティのセルをクリックして **[Percent]** を選択します。  
  
8.  [プロパティ] ウィンドウで、**Unit Price Discount Pct** メジャーの **Name** プロパティを **Unit Price Discount Percentage** に変更します。  
  
9. **[メジャー]** ペインで **[Tax Amt]** をクリックし、このメジャーの名前を "**Tax Amount**" に変更します。  
  
10. [プロパティ] ウィンドウの **[自動的に隠す]** アイコンをクリックし、[プロパティ] ウィンドウを非表示にします。次に、**[キューブ構造]** タブのツール バーで、**[メジャー ツリーの表示]** をクリックします。  
  
11. **[ファイル]** メニューの **[すべてを保存]**をクリックします。  
  
## このレッスンの次の作業  
[Customer ディメンションの変更](../analysis-services/modifying-the-customer-dimension.md)  
  
## 参照  
[データベース ディメンションの定義](../analysis-services/multidimensional-models/define-database-dimensions.md)  
[メジャーのプロパティの構成](../analysis-services/multidimensional-models/configure-measure-properties.md)  
  
  
  
