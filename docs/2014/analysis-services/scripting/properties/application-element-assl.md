---
title: Application 要素 (ASSL) |Microsoft Docs
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
api_name:
- Application Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Application
helpviewer_keywords:
- Application element
ms.assetid: dfd780ad-f643-4a1c-b58b-34271ae91240
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e04ce46a9fc2797885e3c8dff0acd697a782b95a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279498"
---
# <a name="application-element-assl"></a>Application 要素 (ASSL)
  関連付けられているアプリケーションを識別、[アクション](../objects/action-element-assl.md)要素。  
  
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../objects/action-element-assl.md)またはその派生要素のいずれか: [DrillThroughAction](../data-type/action-data-type-assl.md)、 [ReportAction](../data-type/reportaction-data-type-assl.md)、 [StandardAction](../data-type/standardaction-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Application` 要素は、クライアント アプリケーションで使用して、特定のクライアント アプリケーションに適用可能なアクションを調べることができます。 この要素の値の評価は、クライアント アプリケーションによって行います。  
  
 親に対応する要素`Application`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [Actions 要素&#40;ASSL&#41;](../collections/actions-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
