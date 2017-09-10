---
title: "レッスン 1: 分析結果内のデータ ソース ビューを定義するサービス プロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 7d3ffabd-78ae-4204-8323-29949d030c16
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22c30f82afe518a11758ec27868d8883c0b85483
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-1-defining-a-data-source-view-within-an-analysis-services-project"></a>レッスン 1 : Analysis Services プロジェクト内でのデータ ソース ビューの定義
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でビジネス インテリジェンス アプリケーションを設計するには、まず、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]プロジェクトを作成します。 このプロジェクト内で、ソリューションに必要なすべての要素を定義します。最初に定義するのはデータ ソース ビューです。  
  
このレッスンの内容は次のとおりです。  
  
[Analysis Services プロジェクトの作成](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)  
この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モデル テンプレートに基づいて [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトを作成します。  
  
[データ ソースの定義](../analysis-services/lesson-1-2-defining-a-data-source.md)  
この実習では、この後のレッスンで定義する **ディメンションおよびキューブのデータ ソースとして、** AdventureWorksDW2012 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを指定します。  
  
[データ ソース ビューの定義](../analysis-services/lesson-1-3-defining-a-data-source-view.md)  
この実習では、 **AdventureWorksDW2012** データベースの選択したテーブルに格納されているメタデータを 1 つにまとめた統合ビューを定義します。  
  
[既定のテーブル名の変更](../analysis-services/lesson-1-4-modifying-default-table-names.md)  
この実習では、この後で定義する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを識別しやすくするために、データ ソース ビューのテーブル名をわかりやすい名前に変更します。  
  
結果を、このレッスン用にビルドされたサンプル プロジェクト ファイルと比較してください。 このチュートリアルのサンプル プロジェクトのダウンロードの詳細については、CodePlex の製品サンプル ページで「 [SSAS Multidimensional Model Projects for SQL Server 2012](http://go.microsoft.com/fwlink/p/?LinkID=221866) 」を参照してください。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2 : キューブの定義と配置](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services プロジェクトの作成 (SSDT)](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
[サポートされるデータ ソース (SSAS - 多次元)](https://msdn.microsoft.com/library/ms175608(v=sql.110).aspx)  
[多次元モデルのデータ ソース ビュー](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
[Analysis Services のチュートリアル シナリオ](../analysis-services/analysis-services-tutorial-scenario.md)  
[多次元モデリング (Adventure Works チュートリアル)](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
  

