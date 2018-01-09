---
title: "PerspectiveAttribute データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PerspectiveAttribute Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PerspectiveAttribute
helpviewer_keywords: PerspectiveAttribute data type
ms.assetid: bf4d45c1-e48d-4ada-bbab-49c3ac74948d
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 21e0d5402d970e37eda486fd7ae2ba9f6bbadd18
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="perspectiveattribute-data-type-assl"></a>PerspectiveAttribute データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]内の属性に関する情報を表すプリミティブ データ型を定義、 [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveAttribute>  
      <AttributeID>...</AttributeID>  
   <DefaultMember>...</DefaultMember>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
      <Annotations>...</Annotations>  
</PerspectiveAttribute>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md)、 [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)、 [DefaultMember](../../../analysis-services/scripting/properties/defaultmember-element-assl.md)|  
|派生要素|[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)([属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)のコレクション[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.PerspectiveAttribute>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
