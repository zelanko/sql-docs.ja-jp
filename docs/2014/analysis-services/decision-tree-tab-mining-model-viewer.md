---
title: '[デシジョンツリー] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.decisiontree.f1
ms.assetid: dc88606f-ba7c-4f8d-af65-bfa17ec16e2b
author: minewiskan
ms.author: owend
ms.openlocfilehash: b13eb819edc2a33117d45954423466343f5de18a
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528878"
---
# <a name="decision-tree-tab-mining-model-viewer"></a>[デシジョン ツリー] タブ (マイニング モデル ビューアー)
  **[デシジョン ツリー]** ペインは、デシジョン ツリー モデルで作成されたデシジョン ルールをビジュアルに表示します。 デシジョン ルールは、特定の結果に至るパスを記述します。  
  
 **詳細:** [Microsoft デシジョン ツリー アルゴリズム](data-mining/microsoft-decision-trees-algorithm.md)」、「 [Microsoft ツリー ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **[マイニング モデル]**  
 現在のマイニング構造に含まれているマイニング モデルから選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **Viewer**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 カスタム ビューアーまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。 利用可能な場合プラグイン ビューアーを使用することもできます。  
  
 **拡大**  
 デシジョン ツリーのノードと分岐の詳細が表示されるように拡大します。 複雑なモデルでは、デシジョン ツリーに多数の分岐レベルが含まれる可能性があります。  
  
 **縮小**  
 ツリー構造の全体ビューが表示されるように縮小します。  
  
 **[グラフ ビューのコピー]**  
 ダイアグラムで表示されている部分をクリップボードにコピーします。  
  
 **[グラフ全体のコピー]**  
 ダイアグラム全体をクリップボードにコピーします。  
  
 **[サイズの自動調整]**  
 画面の大きさに合うようにツリー構造全体を縮小します。  
  
 **ヒストグラム**  
 各ノードのヒストグラムに表示できる状態の数を選択します。 モデルの状態数が選択した値よりも少ない場合でも、追加のバーは表示されません。  
  
 **ツリー**  
 ビューアーに表示するツリーを選択します。 複数の予測可能な属性を含むモデルを作成した場合は、アルゴリズムによって予測可能な属性ごとに別個のツリーが作成されます。  
  
 **背景**  
 各ノードの背景色の表現で使用する予測可能な属性の値を設定します。 たとえば、サンプルの AdventureWorks モデルで **[背景情報]** を 1 ([Bike Buyer] = Yes) に設定した場合、Bike Buyer (バイク購入者) の比率が大きければ大きいほど、ノードの影が濃くなります。 このオプションは、ツリーの分岐とノードに対して視覚的な意味を追加します。  
  
 **既定の展開**  
 ツリー グラフに表示するレベル数の既定値を設定するには、リストから値を選択します。  
  
 **[表示レベル]**  
 ツリー グラフに表示するレベル数を調整するには、スライダー バーを左右に移動します。 モデルのすべてのノードを表示するには、バーを右端までスライドします。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
