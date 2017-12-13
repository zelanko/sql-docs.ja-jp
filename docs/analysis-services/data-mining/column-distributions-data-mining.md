---
title: "列の分布 (データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 19954e49cd65f9a4307da2ecda03fefa1d2b14bd
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="column-distributions-data-mining"></a>列の分布 (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、マイニング モデルを作成するときに、アルゴリズムがこれらの列にデータを処理する方法に影響を与える、マイニング構造列の分布を定義することができます。 いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。 分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。  
  
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
 [コンテンツの種類 &#40;データ マイニング&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [マイニング構造 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [分離メソッド &#40;データ マイニング&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [ディストリビューション &#40;DMX&#41;](../../dmx/distributions-dmx.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
