---
title: "PerspectiveAction データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PerspectiveAction Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PerspectiveAction
helpviewer_keywords: PerspectiveAction data type
ms.assetid: a0e4a545-688c-4d4e-b05f-0008d3503349
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6c10e32a4d4655ce2c81e6c9a4c0ead45961c64a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="perspectiveaction-data-type-assl"></a>PerspectiveAction データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]内のアクションに関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID>  
   <Annotations>...</Annotations>  
</PerspectiveAction>  
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
|子要素|[ActionID](../../../analysis-services/scripting/properties/actionid-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|派生要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)([アクション](../../../analysis-services/scripting/collections/actions-element-assl.md)のコレクション[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.PerspectiveAction>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
