---
title: "列の分布 (データ マイニング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "正規分布 [データ マイニング]"
  - "均一分布 [データ マイニング]"
  - "列 [data mining], 分布"
  - "正規分布の記録 [データ マイニング]"
  - "連続列"
  - "分布 [データ マイニング]"
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 32
---
# 列の分布 (データ マイニング)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、マイニング構造内の列の分布を定義して、マイニング モデルの作成時にこれらの列のデータがアルゴリズムによってどのように処理されるかを指定できます。 いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。 分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用できるアルゴリズムでは、次の分布の種類がサポートされています。  
  
 **標準**  
 連続列の値は、正規分布のヒストグラムを形成します。  
  
 ![正規分布のヒストグラム](../../analysis-services/data-mining/media/normal-distribution.png "正規分布のヒストグラム")  
  
 **Log Normal**  
 連続列の値は、曲線が上端で長くなり、下端に向かってスキューされるヒストグラムを形成します。  
  
 ![対数正規分布のヒストグラム](../../analysis-services/data-mining/media/log-normal-distribution.png "対数正規分布のヒストグラム")  
  
 **Uniform**  
 連続列の値はフラット曲線を形成し、すべての値が等しくなります。  
  
 ![単一ディストリビューションのヒストグラム](../../analysis-services/data-mining/media/uniform-distribution.png "単一ディストリビューションのヒストグラム")  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が提供するアルゴリズムの詳細については、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。  
  
## 参照  
 [コンテンツの種類 &#40;データ マイニング&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [マイニング構造 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [分離メソッド &#40;データ マイニング&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [分布 &#40;DMX&#41;](../../dmx/distributions-dmx.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  