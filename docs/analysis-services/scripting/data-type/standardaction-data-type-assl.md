---
title: StandardAction データ型 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- StandardAction Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- StandardAction
helpviewer_keywords:
- StandardAction data type
ms.assetid: 81b574d5-06c1-4587-8bd2-0e5c5e3b1d99
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ed7b9f423a7318f46008a6058870cacc1623d868
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="standardaction-data-type-assl"></a>StandardAction データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]いずれかを表す派生データ型を定義[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)以外の要素、 [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)要素または[ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<StandardAction>  
   <!-- The following elements extend Action -->  
   <Expression>...</Expression>  
</StandardAction>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|[操作](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[[式]](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
|派生要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)([アクション](../../../analysis-services/scripting/collections/actions-element-assl.md)のコレクション[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.StandardAction>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
