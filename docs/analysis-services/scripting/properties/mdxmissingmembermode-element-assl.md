---
title: "MdxMissingMemberMode 要素 (ASSL) |Microsoft ドキュメント"
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
- MdxMissingMemberMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MdxMissingMemberMode element
ms.assetid: aca6130b-5fb8-4fa1-af8b-8e1ef361926f
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b938068f6e9f55f5d9d94ea5c65a01b5281152f2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|既定値|*既定値*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*無視します。*|欠落しているメンバーは無視されます。|  
|*[エラー]*|欠落しているメンバーが検出された場合、エラーを発生します。|  
|*既定値*|欠落しているメンバーは無視されます。|  
  
 親に対応する要素**MdxMissingMemberMode**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [多次元式 & #40 です。MDX と #41 です。参照](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

