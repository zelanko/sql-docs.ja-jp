---
title: "メジャーの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 43aeb504c51707b98fc0f9240ae722ad88b73daa
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-3-1---modifying-measures"></a>レッスン 3-1-メジャーの変更
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]使用することができます、 **FormatString**プロパティをユーザーにメジャーを表示する方法を制御する書式設定を定義します。 この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの通貨メジャーと比率メジャーの書式プロパティを指定します。  
  
### <a name="to-modify-the-measures-of-the-cube"></a>キューブのメジャーを変更するには  
  
1.  **Tutorial キューブのキューブ デザイナーで、** [キューブ構造] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブに切り替えます。次に、 **[メジャー]** ペインの **[Internet Sales]** メジャー グループを展開し、 **[Order Quantity]**を右クリックして、 **[プロパティ]**をクリックします。  
  
2.  [プロパティ] ウィンドウの **[自動的に隠す]** 押しピン アイコンをクリックし、[プロパティ] ウィンドウを開いたまま固定します。  
  
    [プロパティ] ウィンドウを開いたままにしておくと、キューブ内のアイテムごとにプロパティを変更する操作が容易になります。  
  
3.  [プロパティ] ウィンドウで、 **[FormatString]** ボックスの一覧をクリックし、「 **#,#**」と入力します。  
  
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
  
6.  [プロパティ] ウィンドウで、 **FormatString** プロパティのセルをクリックして、 **[Currency]**を選択します。  
  
7.  [プロパティ] ウィンドウの一番上 (タイトル バーのすぐ下) にあるドロップダウン リストで、 **[Unit Price Discount Pct]**メジャーを選択します。次に、 **FormatString** プロパティのセルをクリックして **[Percent]** を選択します。  
  
8.  [プロパティ] ウィンドウで、 **Unit Price Discount Pct** メジャーの **Name** プロパティを **Unit Price Discount Percentage**に変更します。  
  
9. **[メジャー]** ペインで **[Tax Amt]** をクリックし、このメジャーの名前を " **Tax Amount**" に変更します。  
  
10. [プロパティ] ウィンドウの **[自動的に隠す]** アイコンをクリックし、[プロパティ] ウィンドウを非表示にします。次に、 **[キューブ構造]** タブのツール バーで、 **[メジャー ツリーの表示]** をクリックします。  
  
11. **[ファイル]** メニューの **[すべてを保存]**をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[Customer ディメンションの変更](../analysis-services/lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>参照  
[データベース ディメンションの定義](../analysis-services/multidimensional-models/define-database-dimensions.md)  
[メジャーのプロパティの構成](../analysis-services/multidimensional-models/configure-measure-properties.md)  
  
  
  
