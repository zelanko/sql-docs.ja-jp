---
title: '[属性のプロファイル] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2bb75ec06d9b5c14ce5c2dcc85561412b362b40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66063171"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a>[属性のプロファイル] タブ (マイニング モデル ビューアー)
  Naive Bayes モデルにおける入力値の分布と、結果の属性の状態との関係を確認するには、 **[属性のプロファイル]** タブを使用します。 値の分布はカラー ヒストグラムで表示され、すべての分布は値を簡単に比較できるように表形式で提示されます。  
  
 **詳細情報:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md)、 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>オプション  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **マイニングモデル**  
 現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **[ビューアー]**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 各マイニング モデル用に用意されているカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを選択できます。 可能な場合プラグイン ビューアーを使用することもできます。  
  
 **[凡例の表示]**  
 
  **[状態]** 列の値と分布図で使用される色の対応を示すキーを表示するには、このオプションを選択します。  
  
 **[ヒストグラム バー]**  
 ヒストグラムに含めるバーの数を選択します。 選択したバーの数よりも多くのバーが存在する場合、重要度が最も高いバーが保持され、それ以外のバーは **[その他]** にまとめられます。  
  
 **[予測可能]**  
 マイニング モデルの予測可能な列を選択します。  
  
 **属性のプロファイル**  
 表には次の列が含まれています。  
  
|値|[説明]|  
|-----------|-----------------|  
|**属性**|マイニング モデルに含まれているマイニング モデル列が一覧表示されます。|  
|**状態**|対応する属性の行の色が表す状態を説明するオプションの列です。 追加または削除するには、 **[凡例の表示]** チェック ボックスを使用します。|  
|**作成**|データセット全体における属性の分布が表示されます。|  
|**予測可能な属性状態の列**|予測可能な列の各状態を表す列が表示されます。各行が、モデル内の入力属性に対応しています。|  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
