---
title: HoldoutMaxCases 要素 |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f66fca3656bfe0e0e778bf24e500f03c8f2816ba
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="holdoutmaxcases-element"></a>HoldoutMaxCases 要素
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  テスト セットを含む、提示されたパーティションに使用するデータ ソース内のケースの最大数を指定、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。 データ セット内の残りのケースは、トレーニングに使用されます。 値が 0 の場合、テスト セットとして提示できるケースの数は制限されません。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|0 より大きい整数値|  
|既定値|0|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 両方の値を指定する場合**HoldoutMaxPercent**と**HoldoutMaxCases**アルゴリズムにテスト セットを制限する 2 つの値のいずれか小さい方です。  
  
 場合**HoldoutMaxCases** 、既定値は 0 に設定されているため、値が設定されていないと**HoldoutMaxPercent**アルゴリズムでは、トレーニング データ セット全体を使用します。  
  
 新しいプロパティ**HoldoutMaxCases**、 **HoldoutMaxPercent**、 **HoldoutSeed**、または**HoldoutActualSize** でしか使用できません。[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]以降のバージョン。 構文の説明に示すように、これらのプロパティを新しい名前空間を付ける必要がありますので、または[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はエラーを返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はマイニング構造での提示されたパーティションの使用をサポートしていませんでした。 したがって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を含む、提示されたパラメーターのいずれかのスクリプト言語 (ASSL) ステートメント**HoldoutMaxCases**、 **HoldoutMaxPercent**、 **HoldoutSeed**、または**HoldoutActualSize**では使用できません[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の ASSL ステートメントでこれらの提示されたパラメーターのいずれかを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
 親に対応する要素**HoldoutMaxCases**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [HoldoutMaxPercent 要素](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [HoldoutSeed 要素](../../../analysis-services/scripting/properties/holdoutseed-element.md)   
 [HoldoutActualSize 要素](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)  
  
  
