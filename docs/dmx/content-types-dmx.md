---
title: "コンテンツの種類 (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], content types
- content types [DMX]
- DMX [Analysis Services], content types
ms.assetid: ab9dd887-df8d-4878-96b0-635881892573
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 33af21a44066e96223bbfc07e39f4718edf87fc2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="content-types-dmx"></a>コンテンツの種類 (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ マイニング アルゴリズムが正しく機能するためには、コンテンツの種類など、データ型以外の追加情報が必要です。 コンテンツの種類は、列内のデータが機能する方法をアルゴリズムが判断するために役立ちます。  
  
 各アルゴリズムは特定のコンテンツの種類をサポートします。 たとえば、[!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes アルゴリズムは、連続列を使用できません。 連続列を使用する、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes モデルでは、列のデータを分離する必要があります。 いくつかのアルゴリズムは、正しく機能するために特定のコンテンツの種類が必要です。 たとえば、[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムは、データが収集された経過時間を識別する、Key Time 列が必要です。  
  
 コンテンツの完全な説明の種類を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]サポートされておりを参照してください[コンテンツ タイプ (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/content-types-data-mining.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

