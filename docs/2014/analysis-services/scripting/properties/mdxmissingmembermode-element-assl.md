---
title: MdxMissingMemberMode 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MdxMissingMemberMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MdxMissingMemberMode element
ms.assetid: aca6130b-5fb8-4fa1-af8b-8e1ef361926f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c942587601c5e62d9e876be8eb1277f638eaa7ef
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126741"
---
# <a name="mdxmissingmembermode-element-assl"></a>MdxMissingMemberMode 要素 (ASSL)
  欠落しているメンバーを多次元式 (MDX) ステートメントでどのように処理するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
   ...  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*[Default]*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../data-type/dimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*無視します。*|欠落しているメンバーは無視されます。|  
|*Error*|欠落しているメンバーが検出された場合、エラーを発生します。|  
|*[Default]*|欠落しているメンバーは無視されます。|  
  
 親に対応する要素`MdxMissingMemberMode`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [多次元式&#40;MDX&#41;リファレンス](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
