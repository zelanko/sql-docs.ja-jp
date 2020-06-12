---
title: '[属性の特性] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: e62e42dc1cc405f5515e40b0b050036b673a7b89
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527945"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a>[属性の特性] タブ (マイニング モデル ビューアー)
  Naïve Bayes モデルの結果と入力属性との関係を調べるには、 **[属性の特性]** ペインを使用します。 対象となる属性の値を選択した後、結果に対する影響が最も大きい入力属性の一覧を確認できます。  
  
 **詳細:** [Microsoft Naive Bayes アルゴリズム](data-mining/microsoft-naive-bayes-algorithm.md)、 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **[マイニング モデル]**  
 現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。 選択した種類のマイニング モデルに最適のカスタム ビューアーが開いてモデルが表示されます。  
  
 **Viewer**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 モデルごとに、カスタム ビューアーまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを選択できます。 利用可能な場合、プラグイン ビューアーもリストに表示されます。  
  
 **属性**  
 分析する予測可能な属性を選択します。  
  
 **Value**  
 **[属性]** に設定する予測可能な属性の状態を選択します。 Naive Bayes モデルは連続変数をサポートしないため、すべての対象となる属性は、不連続結果または分離された結果になります。 不明属性は、常に自動的にリストに追加されます。  
  
 **の特性\<predictable state>**  
 グラフには、入力属性の状態が、選択した予測可能な属性の状態とどのように関係するかを記述する次の列が含まれます。  
  
|値|説明|  
|-----------|-----------------|  
|**変数**|マイニング モデルの入力属性を一覧表示します。|  
|**値**|**[変数]** の入力属性の状態を一覧表示します。|  
|**確率**|バーは、その行の属性と値が、予測可能な属性の選択した状態に関連付けられている確率を表します。 パーセントで表される確率を表示するには、バーの上にマウス ポインターを置きます。|  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
