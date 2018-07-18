---
title: HoldoutSeed 要素 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutSeed
helpviewer_keywords:
- HoldoutSeed element
ms.assetid: 6b608bb3-c075-4744-9722-f5fb9fa1cc7e
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b5ba2d0d5d3cb355a4d0d6a372b41207ddce1d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185229"
---
# <a name="holdoutseed-element"></a>HoldoutSeed 要素
  テスト セットを含む反復可能な提示されたパーティションのシードを指定します、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。 このシードを指定すると、再処理中にモデルのコンテンツが変更されることはありません。 指定されていないか 0 に設定する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]マイニング構造の名前をハッシュ アルゴリズムを使用して、シードを作成します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Long|  
|既定値|0|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 最初にマイニング構造を作成した時点では、ID と名前は同じです。 ただし、マイニング構造の名前は変更できます。 したがって、パーティションを反復可能にする場合は、名前に基づいて作成されたシードは使用せずに、シードを明示的に設定してください。  
  
 さらに、使用してマイニング構造のコピーを作成するときに、`EXPORT`ステートメントでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]新しいマイニング構造の名前が保持されますが、新しい ID を自動的に生成されます したがって、名前が同じで ID が異なる 2 つのマイニング構造が存在することもありえます。 名前が同じ 2 つのマイニング構造では、同じシードが使用されます。 ただし、データのパーティション分割はソース データにも依存するので、各構造のパーティションの実際の内容は異なる場合があります。  
  
 新しいプロパティ`HoldoutMaxCases`、 `HoldoutMaxPercent`、 `HoldoutSeed`、または`HoldoutActualSize`でのみ使用可能な[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]以降のバージョン。 構文の説明に示すように、これらのプロパティを新しい名前空間を付ける必要があります、または[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はエラーを返します。  
  
 **注**で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]マイニング構造に提示されたパーティションの使用をサポートできませんでした。 したがって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、提示されたパラメーター (`HoldoutMaxCases`、`HoldoutMaxPercent`、`HoldoutSeed`、または `HoldoutActualSize`) を含む [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] スクリプト言語 (ASSL) ステートメントは使用できません。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の ASSL ステートメントでこれらの提示されたパラメーターのいずれかを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
 親に対応する要素`HoldoutSeed`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)   
 [HoldoutActualSize 要素](holdoutactualsize-element.md)   
 [HoldoutMaxPercent 要素](holdoutmaxpercent-element.md)   
 [HoldoutMaxCases 要素](holdoutmaxcases-element.md)  
  
  
