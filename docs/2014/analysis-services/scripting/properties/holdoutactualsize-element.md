---
title: HoldoutActualSize 要素 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8610024c3eb0b3460883fc5eeddb80f057aff86b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096412"
---
# <a name="holdoutactualsize-element"></a>HoldoutActualSize 要素
  テスト セットを含む、提示されたパーティションの処理後の実際のサイズを示す、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。 データ セット内の残りのケースは、トレーニングに使用されます。 このプロパティは読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutActualSize>...</ddl100_100:HoldoutActualSize>  
   ...  
</MiningStructure  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|読み取り専用の整数値|  
|既定値|適用なし|  
|Cardinality|0-1:省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値は、`HoldoutActualSize`はの値と、ソース データに依存[HoldoutMaxCases](holdoutmaxcases-element.md)、 [HoldoutMaxPercent](holdoutmaxpercent-element.md)、および[HoldoutSeed](holdoutseed-element.md)します。 このため、`HoldoutActualSize` の値は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でマイニング構造が処理されるまで使用できません。  
  
 親に対応する要素`HoldoutActualSize`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はマイニング構造での提示されたパーティションの使用をサポートしていませんでした。 したがって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、提示されたパラメーター (`HoldoutMaxCases`、`HoldoutMaxPercent`、`HoldoutSeed`、または `HoldoutActualSize`) のいずれかを含む [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] スクリプト言語 (ASSL) ステートメントは使用できません。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の ASSL ステートメントでこれらの提示されたパラメーターのいずれかを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)   
 [HoldoutMaxCases 要素](holdoutmaxcases-element.md)   
 [HoldoutMaxPercent 要素](holdoutmaxpercent-element.md)   
 [HoldoutSeed 要素](holdoutseed-element.md)  
  
  
