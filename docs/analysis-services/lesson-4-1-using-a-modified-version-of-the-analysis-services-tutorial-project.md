---
title: 解析の変更済みバージョンを使用してサービスのチュートリアル プロジェクト |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 685aa217-de1b-4df2-bf22-095228c40775
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 47d4ce5b877b360e7e340fff65199080cfb7441b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-4-1---using-a-modified-version-of-the-analysis-services-tutorial-project"></a>レッスン 4-1-Analysis Services チュートリアル プロジェクトの変更済みバージョンを使用します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

このチュートリアルの残りのレッスンでは、最初の 3 つのレッスンで作成した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正版を使用します。 まず、新しいテーブルと名前付き計算が **Adventure Works DW 2012** データ ソース ビューに追加されています。次に、新しいディメンションがプロジェクトおよび [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに追加されています。 そして、2 つ目のメジャー グループが追加されています。このメジャー グループには、2 番目のファクト テーブルのメジャーが含まれています。 修正されたこのプロジェクトを使用すれば、これまでに習得したスキルを繰り返し使用せずに、ビジネス インテリジェンス アプリケーションに機能を追加する方法を学習していくことができます。  
  
チュートリアルを続ける前に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正版のダウンロード、展開、読み込み、および処理を行う必要があります。  すべての手順を確実に実行するために、このレッスンでの指示に従ってください。  
  
## <a name="downloading-and-extracting-the-project-file"></a>プロジェクト ファイルのダウンロードと展開  
  
1.  このチュートリアルのサンプル プロジェクトをダウンロードできるページに移動するには、[ここをクリック](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services)してください。 チュートリアルのプロジェクトに含まれる、 **adventure-works-マルチ ディメンションのチュートリアル-projects.zip**をダウンロードします。  
  
2.  をクリックして**adventure-works-マルチ ディメンションのチュートリアル-projects.zip**このチュートリアルでは、プロジェクトを含むパッケージをダウンロードします。  
  
    既定では、.zip ファイルはダウンロード フォルダーに保存されます。 より短いパスの場所に .zip ファイルを移動する必要があります (たとえば、ファイルを保存するための C:\Tutorials フォルダーを作成します)。  その後、.zip ファイルに含まれているファイルを展開します。 長いパスのダウンロード フォルダーからファイルを解凍しようとすると、レッスン 1 しか取得できない場合があります。  
  
3.  ルート ドライブか、それに近い場所にサブフォルダーを作成します (C:\Tutorial など）。  
  
4.  移動、 **adventure-works-マルチ ディメンションのチュートリアル-projects.zip**サブフォルダーにファイル。  
  
5.  ファイルを右クリックし、 **[すべて展開]** をクリックします。  
  
6.  **Lesson 4 Start** フォルダーに移動して、 **Analysis Services Tutorial.sln** ファイルを見つけます。  
  
## <a name="loading-and-processing-the-enhanced-project"></a>修正したプロジェクトの読み込みと処理  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[ファイル]** メニューの **[ソリューションを閉じる]** をクリックして、使用しないファイルを閉じます。  
  
2.  **[ファイル]** メニューの **[開く]** をポイントし、**[プロジェクト/ソリューション]** をクリックします。  
  
3.  チュートリアルのプロジェクト ファイルを展開した場所を参照します。  
  
    **Lesson 4 Start**という名前のフォルダーを見つけて、Analysis Services Tutorial.sln をダブルクリックします。  
  
4.  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正版を、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスに配置します。別のインスタンスに配置することもできますが、処理が正常に完了することを確認してください。  
  
## <a name="understanding-the-enhancements-to-the-project"></a>プロジェクトの修正について  
プロジェクトの修正版は、最初の 3 つのレッスンで作成した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトとは異なります。 この相違点について、次のセクションで説明します。 チュートリアルの残りのレッスンを続ける前に、この情報を確認してください。  
  
### <a name="data-source-view"></a>データ ソース ビュー  
修正したプロジェクトのデータ ソース ビューには、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースから取得された 1 つのファクト テーブルと 4 つのディメンション テーブルが追加されています。  
  
このデータ ソース ビューには 10 個のテーブルがあり、 <All Tables> ダイアグラムの情報が整理されていません。 このため、テーブル間のリレーションシップがわかりにくく、簡単には特定のテーブルを探すことができません。 この問題を解決するために、テーブルを 2 つの論理ダイアグラムに整理します。2 つのダイアグラムとは、 **Internet Sales** ダイアグラムと **Reseller Sales** ダイアグラムです。 1 つのファクト テーブルに対し、これらのダイアグラムを 1 つずつ構成します。 1 つのダイアグラムにテーブルやそのリレーションシップをすべて表示しなくとも、論理ダイアグラムを作成することにより、複数のテーブルから特定のサブセットのみをデータ ソース ビューに表示し、操作できます。  
  
#### <a name="internet-sales-diagram"></a>Internet Sales ダイアグラム  
**Internet Sales** ダイアグラムには、インターネット経由で直接顧客に販売された、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 製品の売上に関連するテーブルが含まれています。 このダイアグラムには、レッスン 1 で **Adventure Works DW 2012** データ ソース ビューに追加した、4 つのディメンション テーブルと 1 つのファクト テーブルがあります。 これらのテーブルを以下に示します。  
  
-   **Geography**  
  
-   **Customer**  
  
-   **日付**  
  
-   **Product**  
  
-   **InternetSales**  
  
#### <a name="reseller-sales-diagram"></a>Reseller Sales ダイアグラム  
**Reseller Sales** ダイアグラムには、販売店による [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 製品の売上に関するテーブルが含まれています。 このダイアグラムには、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースから取得された、次の 7 つのディメンション テーブルと 1 つのファクト テーブルが含まれています。  
  
-   **Reseller**  
  
-   **Promotion**  
  
-   **SalesTerritory**  
  
-   **Geography**  
  
-   **日付**  
  
-   **Product**  
  
-   **Employee**  
  
-   **ResellerSales**  
  
**DimGeography**、 **DimDate**、および **DimProduct** テーブルは、 **Internet Sales** ダイアグラムと **Reseller Sales** ダイアグラムの両方で使用されます。 ディメンション テーブルは、複数のファクト テーブルにリンクさせることができます。  
  
### <a name="database-and-cube-dimensions"></a>データベースとキューブ ディメンション  
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトには、5 つの新しいデータベース ディメンションがあります。また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブは、これらと同じ 5 つのディメンションをキューブ ディメンションとして保持します。 これらのディメンションには、名前付き計算、複合メンバー キー、および表示フォルダーを使用しながら修正したユーザー階層とユーザー属性が存在します (そのようなユーザー階層とユーザー属性を持つようにディメンションが定義されています)。 この新しいディメンションの内容は次のとおりです。  
  
Reseller ディメンション  
Reseller ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Reseller** テーブルに基づいています。  
  
Promotion ディメンション  
Promotion ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Promotion** テーブルに基づいています。  
  
Sales Territory ディメンション  
Sales Territory ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Sales Territory** テーブルに基づいています。  
  
Employee ディメンション  
Employee ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Employee** テーブルに基づいています。  
  
Geography ディメンション  
Geography ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Geography** テーブルに基づいています。  
  
#### <a name="analysis-services-cube"></a>Analysis Services キューブ  
**Analysis Services Tutorial** キューブには 2 つのメジャー グループがあります。1 つは、 **InternetSales** テーブルに基づく元のメジャー グループ、もう 1 つは、 **Adventure Works DW 2012** データ ソース ビューの **ResellerSales** テーブルに基づくメジャー グループです。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[親子階層の親属性プロパティの定義](../analysis-services/lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services プロジェクトの展開](../analysis-services/lesson-2-5-deploying-an-analysis-services-project.md)  
  
