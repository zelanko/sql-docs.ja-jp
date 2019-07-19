---
title: 分布 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f4789a0e312decb2a46a9a1ba656fc5e4d3e9d47
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070749"
---
# <a name="distributions-dmx"></a>分布 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、マイニング モデルを作成するときに、アルゴリズムがこれらの列にデータを処理する方法に影響を与える、マイニング構造列のコンテンツを定義することができます。 いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。 分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] データ マイニング アルゴリズムでは、次の配布の種類をサポートします。  
  
 **標準**  
 連続列の値は、正規のガウス分布によるヒストグラムを形成します。  
  
 **Log Normal**  
 連続列の値は、値の対数が正規分布であるヒストグラムを形成します。  
  
 **UNIFORM**  
 連続列の値はフラット曲線を形成し、すべての値が等しくなります。  
  
 詳細については[!INCLUDE[msCoName](../includes/msconame-md.md)]データ マイニング アルゴリズムを参照してください[データ マイニング アルゴリズム&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)します。 サードパーティのアルゴリズム プロバイダーは、追加の分布の種類をサポートしている場合があります。 サポートする分布の種類のアルゴリズムを決定するを使用して、 **SUPPORTED_DISTRIBUTION_FLAGS**スキーマ行セット。  
  
 分布の種類の詳細については、次を参照してください。[列の分布&#40;データ マイニング&#41;](../analysis-services/data-mining/column-distributions-data-mining.md)します。  
  
## <a name="see-also"></a>参照  
 [コンテンツの種類 &#40;です。 データ マイニング&#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
