---
title: MeasureGroupHierarchy データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e68bd657f2dc1a279ed6e0aec1cf0499d9c004f6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="measuregrouphierarchy-data-type-assl"></a>MeasureGroupHierarchy データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メジャー グループの階層に関する情報を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroupHierarchy>  
   <HierarchyID>...</HierarchyID>  
      <Annotations>...</Annotations>  
</MeasureGroupHierarchy>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [HierarchyID](../../../analysis-services/scripting/properties/hierarchyid-element-assl.md)|  
|派生要素|[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)([階層](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)のコレクション[RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md))|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
