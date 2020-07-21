---
title: '[モデル] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.timeseries.decisiontree.f1
ms.assetid: 50570bb4-fcac-411e-b530-0398437efda7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42285f94057441d01259c5fd54ce896dd0316b94
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537364"
---
# <a name="model-tab-mining-model-viewers"></a>[モデル] タブ (マイニング モデル ビューアー)
  Microsoft タイム シリーズ ビューアーの **[モデル]** タブは、タイム シリーズの表現をグラフのノードとして表示します。これは、デシジョン ツリー モデルで使用されるものに似ています。  
  
 時系列分析に関する有用な情報を抽出するには、グラフの式、ARIMA 期間、および係数を含むタイム シリーズ モデルのこのビューを使用します。  
  
 **詳細情報:** [Microsoft Time Series アルゴリズム](data-mining/microsoft-time-series-algorithm.md)、 [Microsoft タイム シリーズ ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)、 [Microsoft Time Series アルゴリズム](data-mining/microsoft-time-series-algorithm.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **[マイニング モデル]**  
 表示するマイニング モデルを選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **Viewer**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 このモデルの種類用のカスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー** ビューアーを使用できます。 利用可能な場合プラグイン ビューアーを使用することもできます。  
  
 **拡大**  
 ダイアグラムを拡大します。  
  
 **縮小**  
 グラフを縮小します。  
  
 **[グラフ ビューのコピー]**  
 ダイアグラムで表示されている部分をクリップボードにコピーします。  
  
 **[グラフ全体のコピー]**  
 ダイアグラム全体をクリップボードにコピーします。  
  
 **[サイズの自動調整]**  
 画面の大きさに合うようにダイアグラム全体を縮小します。  
  
 **ツリー**  
 ビューアーに表示するツリーをドロップダウン リストから選択します。  
  
 タイム シリーズ モデルに複数のシリーズが含まれている場合、各シリーズは個別のツリーで表されます。 たとえば、[Quantity] と [Sales Amount] の両方に対して期間の予測を作成した場合、予測可能な属性ごとにシリーズが作成されます。  
  
 リストで強調表示される色の長さは、ツリーのレベル数を示します。 つまり、単一のノードで表すことができるタイム シリーズ モデルには傾向を記述する式が 1 つだけ存在し、色分けされたバーの長さは非常に短くなります (言うまでもなく、モデルが MIXED モデルの場合、ノードには ARIMA 式と ARTXP 式の両方が含まれます)。  
  
 ドロップダウン リストに表示されるツリーの色分けされたバーが長い場合は、モデルのツリーに多数の分岐が存在します。 分岐は、回帰がより複雑であり、各ノードで異なる式 (または式のペア) を使用してモデルを複数のセグメントに分割する必要があることを意味します。  
  
 **背景**  
 このコントロールを使用して、各ノードの背景色によって表される状態を選択します。  
  
 **既定の展開**  
 モデル内のすべてのツリーに対して表示される、レベルの既定の数を調整します。  
  
 **[表示レベル]**  
 ツリーに表示されるレベルの数を変更します。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
