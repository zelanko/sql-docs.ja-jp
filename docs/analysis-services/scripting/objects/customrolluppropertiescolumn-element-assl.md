---
title: "CustomRollupPropertiesColumn 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CustomRollupPropertiesColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CustomRollupPropertiesColumn
helpviewer_keywords: CustomRollupPropertiesColumn element
ms.assetid: 7f4a9825-c768-4523-acb3-511a5160fd44
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 69b3bc9989783ab18d204c275bcc33654d1faa92
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="customrolluppropertiescolumn-element-assl"></a>CustomRollupPropertiesColumn 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]カスタム ロールアップ式のプロパティを提供する列の詳細を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <CustomRollupPropertiesColumn xsi:type="DataItem">...</CustomRollupPropertiesColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、 **DataItem**の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**を入力しを参照してください[DataItem データ型と #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 親に対応する要素**CustomRollupPropertiesColumn**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [CustomRollupColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
