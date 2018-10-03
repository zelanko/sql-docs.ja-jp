---
title: RefreshPolicy 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RefreshPolicy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshPolicy
helpviewer_keywords:
- RefreshPolicy element
ms.assetid: f4c36280-1a39-4f1c-a3ab-fbeb81742d6d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6322c725a0c4b339425b9cc9e10aa6596c9fc34c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144432"
---
# <a name="refreshpolicy-element-assl"></a>RefreshPolicy 要素 (ASSL)
  どのくらいの頻度を決定します。 ディメンションまたはメジャー グループの動的な部分 (で指定されたとおり、[永続化](persistence-element-assl.md)要素) が変更されています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
|先祖または親|既定値|  
|------------------------|-------------------|  
|[DimensionBinding](../data-type/binding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|なし|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionBinding](../data-type/binding-data-type-assl.md)、 [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ByQuery*|すべてのクエリで、ソース データが変更されたかどうかを確認します。|  
|*ByInterval*|ソース データがで指定した間隔での変更チェックのみ[RefreshInterval](refreshinterval-element-assl.md)します。|  
  
 許容された値に対応する列挙体`RefreshPolicy`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RefreshPolicy>します。  
  
## <a name="see-also"></a>参照  
 [Persistence 要素&#40;ASSL&#41;](persistence-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
