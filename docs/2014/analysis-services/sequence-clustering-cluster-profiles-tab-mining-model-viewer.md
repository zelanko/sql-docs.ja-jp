---
title: シーケンスクラスターの [クラスターのプロファイル] タブ (マイニングモデルビューアー)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.profiles.f1
ms.assetid: 44230895-0a42-4032-8d6c-0cdb8a2dbb8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f277abea585715f6a3656fffe7672f347233507
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66069101"
---
# <a name="sequence-clustering-cluster-profiles-tab-mining-model-viewer"></a>シーケンス クラスターの [クラスターのプロファイル] タブ (マイニング モデル ビューアー)
  
  **Microsoft シーケンス クラスター ビューアー** の **[クラスターのプロファイル]** タブでは、各クラスターに含まれるシーケンスの色分けされたビューが表示されます。  
  
 モデルによって検出されたシーケンスがどのようにグループ化されるかを簡単に確認するには、シーケンス クラスター モデルのこのビューを使用します。 長いシーケンスと短いシーケンスをひとめで確認できます。 クラスターをクリックして **[マイニング凡例]** を表示することで、各シーケンスの色が表している状態を正確に知ることもできます。  
  
 **詳細情報:**  [Microsoft](data-mining/microsoft-sequence-clustering-algorithm.md)シーケンスクラスターアルゴリズム、 [Microsoft シーケンスクラスタービューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **マイニングモデル**  
 現在のマイニング構造に含まれているマイニング モデルから、表示するモデルを選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **[ビューアー]**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 カスタム ビューアーまたは **Microsoft 汎用コンテンツ ツリー ビューアー**を使用できます。 利用可能な場合プラグイン ビューアーを使用することもできます。  
  
 **[凡例の表示]**  
 クラスターのプロファイルに表示されている色と状態のテキスト値との相関関係を示す凡例を表示するには、このオプションを選択します。  
  
 **ヒストグラムバー**  
 ヒストグラムに表示される色分けされたバーの数を変更するには、このオプションを使用します。 選択したバーの数よりも多くのバーが存在する場合、重要度が最も高いバーが保持され、それ以外のバーは **[その他]** にまとめられます。  
  
 **属性**と**クラスターのプロファイル**  
 グラフのこのセクションには、モデル内で検出されたシーケンスのクラスターが一覧表示されます。  
  
 各シーケンス クラスターは、 **[ヒストグラム バー]** オプションで選択した数の状態を使用して表示されます。  
  
 モデルのクラスターごとに 2 セットのヒストグラムが表示されます。各セットはグラフの異なる行を対象とします。  
  
-   **属性名>. サンプル: この行のヒストグラムは、各クラスターの代表となる項目のシーケンスを示しています。 \<** DMX 用語では、これらは各クラスターのサンプル ケースです。  
  
-   属性名>: この行のヒストグラムは、クラスターに含まれるすべてのアイテムとその全体的な分布を表します。 ** \< ** 
  **[マイニング凡例]** が表示されているときにヒストグラムをクリックすると、それぞれの数値を確認できます。  
  
 **状態**  
 グラフのこの列はオプションです。 **[凡例の表示]** をクリックすることで、表示または削除できます。 
  **[状態]** 列は、どの状態が対応するクラスターのヒストグラム内のどの色で表現されているかを示すガイドとなります。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft シーケンスクラスターアルゴリズム](data-mining/microsoft-sequence-clustering-algorithm.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データマイニングモデルビューアー](data-mining/data-mining-model-viewers.md)   
 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
