---
title: '[クラスターの特性] タブ (マイニングモデルビューアー)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c0b4a798f9a395741ae831d3b22fc06a71f55607
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087988"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a>[クラスターの特性] タブ (マイニング モデル ビューアー)
  
  **[クラスターの特性]** タブを使用して、クラスター モデル内のクラスター特性またはモデル内のすべてのケースのセットを調査できます。 クラスターを定義する特性としての各属性と値のペアの重要度が、他のクラスターと比較したグラフとして表示されます。  
  
 **詳細情報:** [microsoft クラスタリングアルゴリズム](data-mining/microsoft-clustering-algorithm.md)、 [Microsoft クラスタービューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **マイニングモデル**  
 現在のマイニング構造に含まれているマイニング モデルから選択します。 マイニング モデルがカスタム ビューアーに表示されます。  
  
 **[ビューアー]**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 モデルの種類に関連付けられたカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。 利用可能な任意のプラグイン ビューアーを使用することもできます。  
  
 **クラスター**  
 表示するクラスターを選択するか、**[母集団 (すべて)]** を選択して、全体としてのモデルの属性の分布を確認します。  
  
 **クラスター>\<の特性**  
 選択したクラスターの特性を記述する次の列がグラフに含まれます。  
  
|値|[説明]|  
|-----------|-----------------|  
|**変数**|選択したクラスターで見つかったマイニング モデルの属性を一覧表示します。|  
|**値**|現在選択されているクラスターで見つかった現在の属性の値を一覧表示します。|  
|**確率**|属性と値のペアの強度が、クラスターの特徴としてバーで示されます。 バーの上にマウス ポインターを置くことで、パーセントで表現された確率値を確認できます。 この値は、この属性と値の組み合わせが特定のケースで発生する場合、そのようなケースがこのクラスターに属する確率がどの程度あるかを示します。|  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
