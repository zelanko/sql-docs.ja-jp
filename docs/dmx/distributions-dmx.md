---
title: "分布 (DMX) |Microsoft ドキュメント"
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
- column distributions [DMX]
- distributions [DMX]
- DMX [Analysis Services], distributions
- Data Mining Extensions [Analysis Services], distributions
ms.assetid: cfbb9f38-ae71-401e-867f-15c6a2b6fb97
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 85d01b1e2637b938d093fce3b4cfcc5c1f99abda
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="distributions-dmx"></a>分布 (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、マイニング モデルを作成するときに、アルゴリズムがこれらの列にデータを処理する方法に影響を与える、マイニング構造列のコンテンツを定義することができます。 いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。 分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]データ マイニング アルゴリズムでは、次の分布の種類をサポートします。  
  
 **標準**  
 連続列の値は、正規のガウス分布によるヒストグラムを形成します。  
  
 **Log Normal**  
 連続列の値は、値の対数が正規分布であるヒストグラムを形成します。  
  
 **UNIFORM**  
 連続列の値はフラット曲線を形成し、すべての値が等しくなります。  
  
 詳細については[!INCLUDE[msCoName](../includes/msconame-md.md)]データ マイニング アルゴリズムを参照してください[データ マイニング アルゴリズムと #40 です。Analysis Services - データ マイニング &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). サードパーティのアルゴリズム プロバイダーは、追加の分布の種類をサポートしている場合があります。 サポートする分布の種類のアルゴリズムを決定するを使用して、 **SUPPORTED_DISTRIBUTION_FLAGS**スキーマ行セット。  
  
 分布の種類の詳細については、次を参照してください。[列の分布 (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/column-distributions-data-mining.md)です。  
  
## <a name="see-also"></a>参照  
 [コンテンツの種類 (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般的な予測関数 &#40;DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

