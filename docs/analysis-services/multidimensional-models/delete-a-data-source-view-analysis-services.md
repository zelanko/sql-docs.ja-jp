---
title: "データ ソース ビューの削除 (Analysis Services) | Microsoft Docs"
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
  - "データ ソース ビューの削除"
  - "データ ソース ビュー [Analysis Services]、削除"
  - "データ ソース ビューの除去"
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# データ ソース ビューの削除 (Analysis Services)
  OLAP プロジェクトでデータ ソース ビュー (DSV) を使用していない場合、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でプロジェクトから DSV を削除できます。  
  
 DSV は、削除すると完全に失われます。 削除した DSV を、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のプロジェクトまたはデータベースに復元することはできません。  
  
 他のオブジェクトが依存している DSV は、オンライン モードの [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって開かれた [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースから削除できません。 サーバーで実行中のデータベースに接続されているプロジェクトから DSV を削除するには、DSV 自体を削除する前に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内でその DSV に依存しているすべてのオブジェクトを削除する必要があります。  
  
 DSV を削除すると、依存している他の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが無効になります。そのため、DSV を削除する前に、DSV を削除すると無効になるオブジェクトの一覧が表示されます。 使用する予定のあるオブジェクトが含まれていないか、この一覧で確認します。  
  
 ![[オブジェクトの削除] ダイアログ ボックス](../../analysis-services/multidimensional-models/media/ssas-olapdsv-deleteobjects.gif "[オブジェクトの削除] ダイアログ ボックス")  
  
## 参照  
 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [データ ソース ビューのプロパティの変更 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  