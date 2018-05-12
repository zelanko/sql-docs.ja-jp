---
title: 列の分布 (データ マイニング) |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83da6c1ba0a278d2d6b80f309a7bc7f6a1688ba4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="column-distributions-data-mining"></a>列の分布 (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、マイニング構造内の列の分布を定義して、マイニング モデルの作成時にこれらの列のデータがアルゴリズムによってどのように処理されるかを指定できます。 いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。 分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用できるアルゴリズムでは、次の分布の種類がサポートされています。  
  
 **標準**  
 連続列の値は、正規分布のヒストグラムを形成します。  
  
 ![正規分布のヒストグラム](../../analysis-services/data-mining/media/normal-distribution.gif "正規分布のヒストグラム")  
  
 **Log Normal**  
 連続列の値は、曲線が上端で長くなり、下端に向かってスキューされるヒストグラムを形成します。  
  
 ![対数正規分布のヒストグラム](../../analysis-services/data-mining/media/log-normal-distribution.gif "対数正規分布のヒストグラム")  
  
 **Uniform**  
 連続列の値はフラット曲線を形成し、すべての値が等しくなります。  
  
 ![一様分布によるヒストグラム](../../analysis-services/data-mining/media/uniform-distribution.gif "一様分布によるヒストグラム")  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が提供するアルゴリズムの詳細については、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [コンテンツの種類 (&) #40 です。 データ マイニング (&) #41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [マイニング構造と #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [分離メソッド (&) #40";"データ マイニング"&"#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [ディストリビューション & #40";"DMX"&"#41;](../../dmx/distributions-dmx.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
