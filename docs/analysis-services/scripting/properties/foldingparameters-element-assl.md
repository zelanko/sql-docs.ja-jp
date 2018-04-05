---
title: FoldingParameters 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: Schema
applies_to:
- SQL Server 2016 Preview
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
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8f6fa2a178bc1d8f9722a101d7305cedfa248663
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="foldingparameters-element-assl"></a>FoldingParameters 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]によって使用されるパラメーターを指定します、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバーのマイニング モデルのクロス検証の実行時にします。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|*FoldIndex*|クロス検証に使用するパーティションの開始位置を示す整数です。|  
|*FoldCount*|クロス検証後のモデル内のパーティション数を示す整数です。|  
|*MaxCases*|クロス検証に使用するモデル ケースの数を示す整数です。<br /><br /> 値 0 はすべてのケースを使用することを示します。|  
|*FoldTargetAttribute*|予測可能な属性を格納するモデル列の ID を示す文字列です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|子要素|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>解説  
 これらのプロパティは内部でのみ使用され、DDL ステートメントで使用することはできません。  
  
 クロス検証を使用する方法については[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]を参照してください[クロス検証レポート内のメジャー](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)です。  
  
 使用してクロス検証を実行する方法については[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ストアド プロシージャを参照してください[データ マイニングのストアド プロシージャと #40 です。Analysis Services - データ マイニング &#41;](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
