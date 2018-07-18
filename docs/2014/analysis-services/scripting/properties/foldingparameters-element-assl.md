---
title: FoldingParameters 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac348aa326c53b1266edfff3396feadda6c80ea6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161143"
---
# <a name="foldingparameters-element-assl"></a>FoldingParameters 要素 (ASSL)
  マイニング モデルのクロス検証を実行するときに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーによって使用されるパラメーターを指定します。  
  
> [!NOTE]  
>  これらのパラメーターは内部でのみ使用されます。 この情報は単なる参照用です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel>  
   ...  
   <ddl100_100:FoldingParameters>...  
      <ddl100_100:FoldIndex>...</ddl100_100:FoldIndex>  
      <ddl100_100:FoldCount>...</ddl100_100:FoldCount>  
      <ddl100_100:MaxCases>...</ddl100_100:MAxCases>  
      <ddl100_100:FoldTargetAttribute>...</ddl100_100:FoldTargetAttribute  
...</ddl100_100:FoldingParameters>  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|*FoldIndex*|クロス検証に使用するパーティションの開始位置を示す整数です。|  
|*FoldCount*|クロス検証後のモデル内のパーティション数を示す整数です。|  
|*MaxCases*|クロス検証に使用するモデル ケースの数を示す整数です。<br /><br /> 値 0 はすべてのケースを使用することを示します。|  
|*FoldTargetAttribute*|予測可能な属性を格納するモデル列の ID を示す文字列です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel](../objects/miningmodel-element-assl.md)|  
|子要素|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>コメント  
 これらのプロパティは内部でのみ使用され、DDL ステートメントで使用することはできません。  
  
 クロス検証を使用する方法については[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]を参照してください[クロス検証レポートのメジャー](../../data-mining/measures-in-the-cross-validation-report.md)します。  
  
 使用してクロス検証を実行する方法については[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ストアド プロシージャを参照してください[データ マイニングのストアド プロシージャ&#40;Analysis Services - データ マイニング&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
