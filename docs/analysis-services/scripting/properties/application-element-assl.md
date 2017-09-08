---
title: "Application 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Application Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Application
helpviewer_keywords:
- Application element
ms.assetid: dfd780ad-f643-4a1c-b58b-34271ae91240
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b54a82a6a6dce39de5de1f4f262958dfe8415e90
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="application-element-assl"></a>Application 要素 (ASSL)
  関連付けられているアプリケーションを識別、[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action>  
   ...  
   <Application>...</Application>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)またはその派生要素のいずれか: [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)、 [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)、 [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **アプリケーション**要素は、特定のクライアント アプリケーションに適用可能なアクションを決定するクライアント アプリケーションで使用できます。 この要素の値の評価は、クライアント アプリケーションによって行います。  
  
 親に対応する要素**アプリケーション**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [Actions 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
