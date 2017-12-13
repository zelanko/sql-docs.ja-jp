---
title: "既定のテーブル名を変更する |Microsoft ドキュメント"
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
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 37923455444f171842e84349a2ce6fc71cd7fd57
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-1-4---modifying-default-table-names"></a>レッスン 1 ~ 4 - 既定のテーブル名の変更
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]値を変更することができます、 **FriendlyName**を確認してを使用しやすくためのデータ ソース ビュー内のオブジェクトのプロパティです。  
  
この実習では、データ ソース ビューの各テーブルの表示名から "**Dim**" プレフィックスと "**Fact**" プレフィックスを削除して、わかりやすい名前にします。 これにより、次のレッスンで定義するキューブ オブジェクトとディメンション オブジェクトがわかりやすく (使いやすく) なります。  
  
> [!NOTE]  
> より簡単に使用できるようにするため、列の表示名を変更して、計算列を定義し、データ ソース ビューのテーブルやビューを結合します。  
  
### <a name="to-modify-the-default-name-of-a-table"></a>テーブルの既定の名前を変更するには  
  
1.  **データ ソース ビュー デザイナー** の **[テーブル]**ペインで **FactInternetSales** テーブルを右クリックし、 **[プロパティ]**をクリックします。  
  
2.  Microsoft Visual Studio ウィンドウの右側の [プロパティ] ウィンドウが表示されていない場合は、[プロパティ] ウィンドウのタイトル バーにある **[自動的に隠す]** ボタンをクリックして、[プロパティ] ウィンドウが常に開いたままになるようにします。  
  
    データ ソース ビューの各テーブルのプロパティを変更するときは、[プロパティ] ウィンドウを開いたままにしておくと便利です。 **[自動的に隠す]** ボタンをクリックしてウィンドウを開いたまま固定しておかないと、 **ダイアグラム** ペイン内の別のオブジェクトをクリックしたときに [プロパティ] ウィンドウが閉じてしまいます。  
  
3.  **FactInternetSales** オブジェクトの **FriendlyName** プロパティをクリックして、「 ***InternetSales***」と入力します。  
  
    **FriendlyName** 以外のセルをクリックすると、変更が適用されます。 次のレッスンでは、このファクト テーブルを基にしてメジャー グループを定義します。 このレッスンで表示名を変更したので、次に作成するファクト テーブルの名前も FactInternetSales ではなく InternetSales になります。  
  
4.  **[テーブル]** ペインで **[DimProduct]** をクリックします。 [プロパティ] ウィンドウで、 **FriendlyName** プロパティを ***Product***に変更します。  
  
5.  データ ソース ビューの他のテーブルについても、同じ方法で **FriendlyName** プロパティを変更します。つまり、**Dim**プレフィックスを削除します。  
  
6.  操作が完了したら、 **[自動的に隠す]** ボタンをクリックして、[プロパティ] ウィンドウを再び非表示にします。  
  
7.  **[ファイル]** メニューまたは [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のツール バーで、 **[すべてを保存]** をクリックして、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトに対するこの時点までの変更を保存します。 ここでチュートリアルを終了しても、後でこの続きから再開できます。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2 : キューブの定義と配置](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>参照  
[多次元モデルのデータ ソース ビュー](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
[データ ソース ビューのプロパティの変更 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
  
