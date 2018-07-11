---
title: HoldoutMaxPercent 要素 |Microsoft Docs
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
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 53689f28351a4a5505f1c1bc1d4c8a9586074704
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278148"
---
# <a name="holdoutmaxpercent-element"></a>HoldoutMaxPercent 要素
  テスト セットを含む、提示されたパーティションに使用されるデータ ソース内のケースの最大割合を指定します、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。 残りのケースは、トレーニングに使用されます。 値が 0 の場合、テスト セットとして提示できるケースの数は制限されません。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|0 ～ 99 の整数|  
|既定値|30|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `HoldoutMaxPercent` と `HoldoutMaxCases` の両方の値を指定すると、アルゴリズムによって、2 つの値のいずれか小さい方の値にテスト セットが制限されます。  
  
 `HoldoutMaxCases` が既定値の 0 に設定され、`HoldoutMaxPercent` に値が設定されていない場合、すべてのデータ セットがトレーニングに使用されます。  
  
 新しいプロパティ`HoldoutMaxCases`、 `HoldoutMaxPercent`、 `HoldoutSeed`、または`HoldoutActualSize`でのみ使用可能な[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]以降のバージョン。 したがって、構文の説明に示されているように、新しい名前空間を使用してこれらのプロパティにプレフィックスを付ける必要があります。プレフィックスを付けないと、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はマイニング構造での提示されたパーティションの使用をサポートしていませんでした。 したがって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、提示されたパラメーター (`HoldoutMaxCases`、`HoldoutMaxPercent`、`HoldoutSeed`、または `HoldoutActualSize`) のいずれかを含む [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] スクリプト言語 (ASSL) ステートメントは使用できません。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の ASSL ステートメントでこれらの提示されたパラメーターのいずれかを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
 親に対応する要素`HoldoutMaxPercent`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)   
 [HoldoutMaxCases 要素](holdoutmaxcases-element.md)   
 [HoldoutSeed 要素](holdoutseed-element.md)   
 [HoldoutActualSize 要素](holdoutactualsize-element.md)  
  
  
