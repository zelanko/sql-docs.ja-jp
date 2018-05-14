---
title: Application 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1bf836c6184e6ac487382f170cd8d52e31ce05d8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="application-element-assl"></a>Application 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Actions 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/actions-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
