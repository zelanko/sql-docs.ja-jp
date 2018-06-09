---
title: 使用法 (DMX) |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 459d6a0240ac2588c0924eae7bdae348a71f5946
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841435"
---
# <a name="usage-dmx"></a>使用法 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング拡張機能 (DMX) を使用して新しいデータ マイニング モデルを定義するときに[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]モデルを構築するデータ マイニング アルゴリズムが各列を使用する方法を指定する必要があります。 列は次の型のうちのいずれかとして指定することができます。  
  
-   **[キー]**  
  
-   **キーのシーケンス**  
  
-   **[キー時刻]**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 指定されていない DMX 内の列は、入力列として扱われます。  
  
 モデルを正しく処理するには、各行を一意に識別するキー列はどれなのか、予測可能モデルを作成する場合に予測を作成するための対象列はどれなのか、および対象列を予測するリレーションシップを作成するために入力列として使用する列はどれなのかをアルゴリズムに理解させる必要があります。  
  
 として指定された列は、 **Predict**型は、入力と出力の両方の列として使用されます。 として指定された列は**PredictOnly**出力列としてのみ使用されます。 アルゴリズムによっては、Predict 列の扱いが異なるものもあります。  
  
 詳細については、列の使用法の型を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]サポートされておりを参照してください[マイニング モデル列](../analysis-services/data-mining/mining-model-columns.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能&#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
