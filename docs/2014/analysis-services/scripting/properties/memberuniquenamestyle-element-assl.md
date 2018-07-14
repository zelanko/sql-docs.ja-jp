---
title: MemberUniqueNameStyle 要素 (ASSL) |Microsoft Docs
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
- MemberUniqueNameStyle Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MemberUniqueNameStyle element
ms.assetid: f0771c81-0127-4203-9501-ae4f864730fa
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2448f2f45f76610e9d7298c855086cc74ab0611e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226362"
---
# <a name="memberuniquenamestyle-element-assl"></a>MemberUniqueNameStyle 要素 (ASSL)
  一意の名前が決定に含まれる階層のメンバーに対して生成される、 [CubeDimension](../data-type/dimension-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension>  
   ...  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ネイティブ*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../data-type/dimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ネイティブ*|インスタンスによって、メンバーの一意の名前が自動的に決定されます。|  
|*NamePath*|インスタンスによって、メンバーの各レベルおよびキャプションで構成される複合名が生成されます。|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`MemberUniqueNameStyle`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [CubeDimension データ型&#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)  
  
  
