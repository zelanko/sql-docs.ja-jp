---
title: コンテンツの種類 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 30f5496247bb817d4ea7da08f95fe4a1b54dea5d
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669796"
---
# <a name="content-types-dmx"></a>コンテンツの種類 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング アルゴリズムが正しく機能するためには、コンテンツの種類など、データ型以外の追加情報が必要です。 コンテンツの種類は、列内のデータが機能する方法をアルゴリズムが判断するために役立ちます。  
  
 各アルゴリズムは特定のコンテンツの種類をサポートします。 たとえば、[!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes アルゴリズムは、連続列を使用できません。 Naive Bayes モデルで連続列を使用するには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 列のデータを分離する必要があります。 一部のアルゴリズムでは、正しく機能するために特定のコンテンツの種類が必要です。 たとえば、[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムは、データが収集された経過時間を識別する、Key Time 列が必要です。  
  
 がサポートするコンテンツの種類の詳細につい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ては、「[コンテンツの種類 &#40;データマイニング&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [DMX&#41; リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-reference.md)   
 [DMX&#41; の構文要素を &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)   
 [DMX&#41; 構文表記規則を &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
