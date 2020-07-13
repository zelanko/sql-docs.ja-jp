---
title: 列の分布 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
ms.openlocfilehash: 29aad33535c4cc4d9baf4c453249ce3b51595e78
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84524393"
---
# <a name="column-distributions-data-mining"></a>列の分布 (データ マイニング)
  では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、マイニングモデルの作成時にアルゴリズムがこれらの列のデータを処理する方法に影響を与えるように、マイニング構造で列の分布を定義できます。 いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。 分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。

 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用できるアルゴリズムでは、次の分布の種類がサポートされています。

 `Normal`連続列の値は、正規分布のヒストグラムを形成します。

 ![正規分布のヒストグラム](../media/normal-distribution.gif "正規分布のヒストグラム")

 `Log Normal`連続列の値は、曲線が上端に長くなり、下側に傾斜するヒストグラムを形成します。

 ![対数正規分布のヒストグラム](../media/log-normal-distribution.gif "対数正規分布のヒストグラム")

 `Uniform`連続列の値は、すべての値が等しくなる可能性があるフラットな曲線を形成します。

 ![単一ディストリビューションのヒストグラム](../media/uniform-distribution.gif "単一ディストリビューションのヒストグラム")

 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が提供するアルゴリズムの詳細については、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。

## <a name="see-also"></a>参照
 [コンテンツの種類 &#40;データマイニング&#41;](content-types-data-mining.md) [マイニング構造 &#40;Analysis Services データマイニング](mining-structures-analysis-services-data-mining.md)&#41;データマイニング &#40;&#41;の[分離方法](discretization-methods-data-mining.md)&#40;[DMX](/sql/dmx/distributions-dmx)&#41;[マイニング構造列](mining-structure-columns.md)


