---
title: ニューラルネットワーク (マイニングモデルビューアー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05654d9206f09d151abd5557d0aa6aae90b1b9ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66072316"
---
# <a name="neural-network-mining-model-viewer"></a>ニューラル ネットワーク (マイニング モデル ビューアー)
  
  **ニューラル ネットワーク** ビューアーを使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] ロジスティック回帰アルゴリズムに基づくマイニング モデルを調べることができます。  
  
 **詳細について**は、「Microsoft[ニューラルネットワークアルゴリズム](data-mining/microsoft-neural-network-algorithm.md)」、「microsoft[ロジスティック回帰アルゴリズム](data-mining/microsoft-logistic-regression-algorithm.md)」、「[microsoft ニューラルネットワークビューアーを使用したモデルの参照」を参照して](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)ください。  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **マイニングモデル**  
 現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **[ビューアー]**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 カスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。 利用可能な場合プラグイン ビューアーを使用することもできます。  
  
 **代入**  
 この領域で入力属性と値を選択します。選択した属性と値が結果にどのように影響するかを後で調べることができます。  
  
|値|[説明]|  
|-----------|-----------------|  
|**属性**|一覧から入力属性を選択します。 選択範囲を既定値の [ ** \<すべて>**] のままにした場合、グラフには、予測可能な属性に対する影響によって順位付けされたすべての入力属性の一覧が表示されます。|  
|**Value**|入力属性の値を選択します。|  
  
 **Output**  
 分析して棒グラフで比較する予測可能な属性と値を選択するには、次のコントロールを使用します。 選択を変更しなかった場合、棒グラフでは上位 2 つの結果状態を比較します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**[出力属性]**|予測可能な属性を選択します。 モデルの作成時に列を予測可能と定義しなかった場合、この時点でそれを追加することはできません。|  
|**値1**|
  **[値 2]** に指定された状態と比較する予測可能な属性の状態を選択します。<br /><br /> 2 つの不連続値または分離された値を比較できます。ただし、他のビューでは可能な、値とその補数との比較は実行できません。|  
|**値2**|
  **[値 1]** に指定された状態と比較する予測可能な属性の状態を選択します。|  
  
 **変数:**  
 
  **[ニューラル ネットワーク]** タブのこの部分には、選択した入力属性と結果属性に応じて変化する対話型棒グラフが含まれます。 ニューラル ネットワークでは特定の値が特定の結果に与える影響の可能性が計算されるので、入力を自由に組み合わせて選択できます。棒グラフには、選択した組み合わせが比較中の結果のペアにどのように影響するかが表示されます。  
  
|値|[説明]|  
|-----------|-----------------|  
|**属性**|
  **[属性]** で選択した入力属性の名前を表示します。|  
|**Value**|選択した入力属性の値を表示します。|  
|**値\<1>を優先する**|選択した属性と値の組み合わせが **[値 1]** で選択した対象となる結果にどの程度影響しているかを示す棒を表示します。|  
|**値\<2 を優先>**|選択した属性と値の組み合わせが **[値 2]** で選択した対象となる結果にどの程度影響しているかを示す棒を表示します。|  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
