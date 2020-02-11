---
title: '[クラスターダイアグラム] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.diagram.f1
ms.assetid: 180e6f48-5c4d-4160-b84d-608b98f7b840
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 127ff0c386a1f93c00178624b54499e33cf9042a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088006"
---
# <a name="cluster-diagram-tab-mining-model-viewer"></a>[クラスター ダイアグラム] タブ マイニング モデル ビューアー)
  
  **[クラスター ダイアグラム]** タブでは、クラスター モデルに含まれているすべてのクラスターがグラフィックで表示されます。  
  
 **詳細情報:** [microsoft クラスタリングアルゴリズム](data-mining/microsoft-clustering-algorithm.md)、 [Microsoft クラスタービューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **マイニングモデル**  
 現在のマイニング構造に含まれているマイニング モデルから選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **[ビューアー]**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 カスタム クラスター ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。 利用可能な場合はプラグイン ビューアーを使用することもできます。  
  
 **拡大**  
 ダイアグラムを拡大して、クラスターの詳細を表示します。  
  
 **縮小**  
 ダイアグラムをズーム アウトして、多数のクラスターを表示します。  
  
 **[グラフ ビューのコピー]**  
 ダイアグラムで表示されている部分をクリップボードにコピーします。  
  
 **[グラフ全体のコピー]**  
 ダイアグラム全体をクリップボードにコピーします。  
  
 **[サイズの自動調整]**  
 画面の大きさに合うようにダイアグラム全体を縮小します。  
  
 **[ノードの検索]**  
 
  **[ノードの検索]** ダイアログ ボックスを開きます。 この機能は、関心のある属性を簡単に検索できない可能性がある大規模なモデルで役に立ちます。 ダイアログ ボックスに検索条件を入力すると、クラスターのビューにフィルターが適用され、検索文字列を含むクラスターだけが表示されます。  
  
 **[レイアウトの改善]**  
 ダイアグラム内のクラスターを並べ替えて、レイアウトを改善します。  
  
 **密度**  
 クラスター ダイアグラムに表示する属性と値のペアを変更するには、このオプションを使用します。 
  **[シェーディング変数]** オプションを使用して属性を選択し、 **[状態]** を使用して値を選択します。 グラフの網かけは、クラスター内での属性と値のペアの密度を示します。  
  
 
  **[母集団]** を選択した場合、グラフには各クラスターのサポート量 (ケース数) が示されます。これは属性が選択されていないためです。  
  
 **[シェーディング変数]**  
 クラスター図で表現する属性を選択します。  
  
 **State**  
 クラスター図で使用する **[シェーディング変数]** の 1 つの状態を選択します。  
  
 **リンク**  
 クラスター間に表示するリンクの数を、スライダーを上下に移動することで調整します。 スライダーを下に移動すると、クラスター間の最も強い関連性だけが残ります。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
