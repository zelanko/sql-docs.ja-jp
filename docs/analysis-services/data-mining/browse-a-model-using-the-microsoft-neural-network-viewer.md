---
title: "Microsoft ニューラル ネットワーク ビューアーを使用してモデルを参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fea303682881b5cb660dbdc7b5c411dc0880ef4e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a>Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ニューラル ネットワーク ビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムを使用して作成されたマイニング モデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムでは、複数の入力と出力を分析できる分類および回帰マイニング モデルを作成します。このアルゴリズムは、制限のない分析と探索に非常に役立ちます。 このアルゴリズムの詳細については、「 [Microsoft Neural Network Algorithm](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)」を参照してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク ビューアーを使用してモデルを調べる場合、通常は対象の属性と状態を選択してから、ビューアーを使用して入力属性が結果に与える影響を確認します。  
  
 たとえば、潜在的な顧客のクラスについて次の事実がわかっているとします。  
  
-   中高年 (40 ～ 50 歳)。  
  
-   持ち家所有。  
  
-   2 人の子供と同居。  
  
 これらの属性を顧客が購入する可能性とどのように関連付けることができるでしょうか。  
  
 購入行動を対象となる結果として使用してニューラル ネットワーク モデルを作成することにより、高所得などの顧客属性の複数の組み合わせを調べ、購入行動に影響する可能性が最も高い属性の組み合わせを検出できます。 たとえば、決定要因が通勤距離であることを検出できます。  
  
 検出された各パターンを表す式などの詳細情報をさらに表示する必要がある場合は、ビューを切り替えて [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用できます。 詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)」を参照してください。  
  
##  <a name="BKMK_ViewerTabs"></a> ビューアーのタブ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク ビューアーには、ニューラル ネットワーク マイニング モデルを調べるための次のタブがあります。  
  
-   [入力](#BKMK_Inputs)  
  
-   [出力](#BKMK_Outputs)  
  
-   [変数](#BKMK_Characteristics)  
  
###  <a name="BKMK_Inputs"></a> 入力  
 **[入力]** タブを使用して、モデルの入力として使用される属性と属性値を選択します。 既定では、ビューアーはすべての属性が含まれた状態で開きます。 この既定のビューでは、表示する最も重要な属性値がモデルによって選択されます。  
  
 入力属性を選択するには、 **[入力]** グリッドの **[属性]** 列内をクリックし、一覧から属性を選択します。 (モデルに含まれている属性のみが一覧に表示されます)。  
  
 **[値]** 列の下に、最初の個別の値が表示されます。 既定値をクリックすると、関連する属性で考えられるすべての状態が含まれた一覧が表示されます。 調査する状態を選択できます。 属性はいくつでも選択できます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Outputs"></a> 出力  
 **[出力]** タブを使用して、調査対象の結果属性を選択します。 モデルの作成時に列が予測可能な属性として定義されたことを前提として、比較する 2 つの結果状態を選択できます。  
  
 **[出力属性]** 一覧を使用して、属性を選びます。 **[値 1]** 一覧と **[値 2]** 一覧から、属性に関連付けられている 2 つの状態を選択できます。 出力属性のこれらの 2 つの状態は、 **[変数]** ペインで比較されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> 変数  
 **[変数]** タブのグリッドには、 **[属性]**、 **[値]**、 **[[値 1] を優先]**、および **[[値 2] を優先]**という列があります。 既定では、列は **[[値 1] を優先]**の強度によって並べ替えられます。 列見出しをクリックすると、並べ替え順が選択した列に変わります。  
  
 属性の右側のバーには、指定した入力属性の状態によって優先される出力属性の状態が示されます。 バーのサイズで、出力の状態によって入力の状態が優先される強度が示されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>参照  
 [Microsoft Neural Network Algorithm](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)   
 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  

