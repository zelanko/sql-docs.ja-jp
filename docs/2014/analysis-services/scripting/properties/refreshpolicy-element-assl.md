---
title: RefreshPolicy 要素 (ASSL) |Microsoft ドキュメント
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
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6d2dc0549eb8151f93c817e9e59bc1a8990fac87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070547"
---
# <a name="refreshpolicy-element-assl"></a>RefreshPolicy 要素 (ASSL)
  どのくらいの頻度を決定ディメンションまたはメジャー グループの動的部分 (で指定されたとおり、[永続化](persistence-element-assl.md)要素) の変更がチェックされます。  
  
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
|*ByInterval*|ソース データがで指定された間隔での変更チェックのみ[RefreshInterval](refreshinterval-element-assl.md)です。|  
  
 許可される値に対応する列挙`RefreshPolicy`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RefreshPolicy>します。  
  
## <a name="see-also"></a>参照  
 [Persistence 要素&#40;ASSL&#41;](persistence-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  