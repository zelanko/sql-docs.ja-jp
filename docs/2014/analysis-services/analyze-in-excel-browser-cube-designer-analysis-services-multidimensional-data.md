---
title: '[Excel で分析] (キューブデザイナーの [ブラウザー] タブ) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2833fb2ecbbac269442ce149cd5673abedcf83c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062366"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>[Excel で分析] (キューブ デザイナーの [ブラウザー] タブ) (Analysis Services - 多次元データ)
  " **Excel で分析**" を使用すると、キューブの開発者は、プロジェクトがエンドユーザーにどのように表示されるかをすばやく確認することができます。 
  **"Excel で分析"** 機能によって Microsoft Excel が開き、モデル ワークスペース データベースへのデータ ソース接続が作成され、自動的にピボットテーブルがワークシートに追加されます。 この機能は、以前のリリースで [ブラウザー] タブに組み込みのピボットテーブルを提供していた Office Web コントロールに替わるものです。  
  
 **キューブ データを表示するには:**  
  
1.  
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のソリューション エクスプローラーでキューブをダブルクリックすると、キューブ デザイナーでそのキューブが開きます。  
  
2.  
  **[ブラウザー]** タブをクリックします。  
  
3.  
  **[再接続]** をクリックして、接続を検証します。  
  
4.  メニュー バーの Excel アイコンをクリックします。  
  
5.  データ接続の有効化を求めるメッセージが表示されたら、 **[有効]** をクリックします。 現在のデータ接続を使用して Excel が開かれ、ワークシートにはピボットテーブルが追加されて、データの参照が可能になります。  
  
 これで、メジャーをファクト テーブルから値領域にドラッグしたり、ディメンション属性を行領域や列領域にドラッグしたりして、ピボットテーブルを対話的に構築できます。 階層がある場合は、行領域または列領域に追加します。 階層をロール アップまたはドリル ダウンして、異なるレベルのファクト データを参照できます。  
  
 オブジェクトとデータは、有効なユーザーまたはロールおよびパースペクティブのコンテキスト内で表示されます。 Excel を使用している場合、クエリ実行時のデータ ソースへの接続には、 **[権限借用情報]** ページで指定された資格情報ではなく、現在のユーザーの資格情報が使用されます。  
  
> [!NOTE]  
>  "Excel で分析" 機能を使用するには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]と同じコンピューターに Excel がインストールされている必要があります。 Excel が同じコンピューターにインストールされていない場合は、別のコンピューターの Excel を使用して、データ ソースとしてキューブに接続できます。 これにより、ピボットテーブルをワークシートに手動で追加することができます。 モデル オブジェクト (テーブル、列、メジャー、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。  
  
 
  **"Excel で分析"** 機能の詳細については、以下のリソースを参照してください。  
  
 [Excel での分析 &#40;SSAS 表形式&#41;](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [Excel でのテーブルモデルの分析 &#40;SSAS 表形式&#41;](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [キューブ内のデータおよびメタデータの参照](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a>参照  
 [ブラウザー &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [ツールバー &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [[メタデータ &#40;ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [キューブデザイナーの [&#40;ブラウザー] タブの [クエリとフィルター]&#41; &#40;Analysis Services-多次元データ&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
