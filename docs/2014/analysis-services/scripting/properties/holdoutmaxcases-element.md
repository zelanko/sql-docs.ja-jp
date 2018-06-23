---
title: HoldoutMaxCases 要素 |Microsoft ドキュメント
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
- HoldoutMaxCases
helpviewer_keywords:
- HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 083ff97f8d739f4f970a6fec8a5c7353b43b5763
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176708"
---
# <a name="holdoutmaxcases-element"></a>HoldoutMaxCases 要素
  テスト セットを含む、提示されたパーティションに使用するデータ ソース内のケースの最大数を指定、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。 データ セット内の残りのケースは、トレーニングに使用されます。 値が 0 の場合、テスト セットとして提示できるケースの数は制限されません。  
  
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
|親要素|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `HoldoutMaxPercent` と `HoldoutMaxCases` の両方の値を指定すると、アルゴリズムによって、2 つの値のいずれか小さい方の値にテスト セットが制限されます。  
  
 `HoldoutMaxCases` が既定値の 0 に設定され、`HoldoutMaxPercent` に値が設定されていない場合、データ セット全体がトレーニングに使用されます。  
  
 新しいプロパティ`HoldoutMaxCases`、 `HoldoutMaxPercent`、 `HoldoutSeed`、または`HoldoutActualSize`でのみ使用可能な[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]以降のバージョン。 構文の説明に示すように、これらのプロパティを新しい名前空間を付ける必要がありますので、または[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はエラーを返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はマイニング構造での提示されたパーティションの使用をサポートしていませんでした。 したがって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、提示されたパラメーター (`HoldoutMaxCases`、`HoldoutMaxPercent`、`HoldoutSeed`、または `HoldoutActualSize`) のいずれかを含む [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] スクリプト言語 (ASSL) ステートメントは使用できません。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の ASSL ステートメントでこれらの提示されたパラメーターのいずれかを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
 親に対応する要素`HoldoutMaxCases`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)   
 [HoldoutMaxPercent 要素](holdoutmaxpercent-element.md)   
 [HoldoutSeed 要素](holdoutseed-element.md)   
 [HoldoutActualSize 要素](holdoutactualsize-element.md)  
  
  