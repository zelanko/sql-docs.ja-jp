---
title: Type 要素 (Binding) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: b5f5c485-dc83-4d66-a8d2-e96e96d068f9
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4bcf3e96c38dd4c2941d2d6256a62559ab3491eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148173"
---
# <a name="type-element-binding-assl"></a>Type 要素 (Binding) (ASSL)
  属性バインドの型を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Type>...</Type>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeBinding](../data-type/binding-data-type-assl.md)、 [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*すべて*|すべてのレベル|  
|*[キー]*|メンバー キー|  
|*名前*|メンバー名|  
|*[値]*|メンバー値|  
|*翻訳*|メンバー翻訳|  
|*[Unaryoperator]*|単項演算子|  
|*SkippedLevels*|スキップされるレベル|  
|*[Customrollup]*|カスタム ロールアップ式|  
|*[Customrollupproperties]*|カスタム ロールアップ プロパティ|  
  
 親に対応する要素`Type`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.AttributeBinding>と<xref:Microsoft.AnalysisServices.CubeAttributeBinding>します。  
  
## <a name="see-also"></a>参照  
 [Binding データ型&#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
