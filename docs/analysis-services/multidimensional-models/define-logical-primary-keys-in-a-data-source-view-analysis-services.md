---
title: "データ ソース ビューでの論理主キーの定義 (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "論理主キーの除去"
  - "論理主キー [SQL Server]"
  - "論理主キーの削除"
  - "データ ソース ビュー [Analysis Services], 論理主キーの定義"
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
caps.latest.revision: 36
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 36
---
# データ ソース ビューでの論理主キーの定義 (Analysis Services)
  データ ソース ビュー ウィザードとデータ ソース ビュー デザイナーでは、データベース テーブルから生成されたデータ ソース ビューにテーブルを追加した場合、そのテーブルの主キーが自動的に定義されます。  
  
 場合によっては、データ ソース ビューの主キーは手動で定義しなければならない場合があります。 たとえば、パフォーマンスまたは設計上の理由から、データ ソース内のテーブルに主キー列が明示的に定義されていない場合があります。 名前付きクエリおよびビューでも、テーブルの主キー列が省略されることがあります。 テーブル、ビュー、または名前付きクエリに物理主キーが定義されていない場合は、データ ソース ビュー デザイナーでテーブル、ビュー、または名前付きクエリの論理主キーを手動で定義できます。  
  
## 論理主キーの設定  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、テーブル内のレコードの一意の識別、ディメンション テーブル内のキー列の識別、テーブル、ビュー、および名前付きクエリ間のリレーションシップのサポートのために主キーが必要になります。 これらのリレーションシップを使用して、基になるデータ ソースからデータやメタデータを取得するためのクエリを作成したり、高度なビジネス インテリジェンス機能を活用したりできます。  
  
 論理主キーには、名前付き計算を含む、任意の列を使用できます。 論理主キーを作成すると、データ ソース ビューに一意の制約が作成され、主キー制約として設定されます。 選択したテーブルで指定されている他の既存の論理主キーは削除されます。  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でプロジェクトを開くか、論理主キーを設定するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、**[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックします。  
  
     テーブルまたはビューを検索するには、**[データ ソース ビュー]** メニューをクリックするか、**テーブル** ペインまたは **ダイアグラム** ペインの空いている領域を右クリックして、**[テーブルの検索]** をクリックします。  
  
3.  **テーブル** ペインまたは**ダイアグラム** ペインで、論理主キーの定義に使用する列を右クリックし、**[論理主キーの設定]** をクリックします。  
  
     論理主キーを設定するオプションは、主キーを持たないテーブルにのみ使用できます。  
  
     これで、キーの設定後、キー アイコンによって主キー列を識別できるようになりました。  
  
## 参照  
 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [データ ソース ビューでの名前付き計算の定義 (Analysis Services)](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  