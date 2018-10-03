---
title: Member 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Member Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Member
- microsoft.xml.analysis.member
- http://schemas.microsoft.com/analysisservices/2003/engine#Member
helpviewer_keywords:
- Member element
ms.assetid: 5cc33a1f-192e-4821-a4ef-9a5f2bb7a9f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ab24b02a46a5e6416018d9f77c733b0d3de7153
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168972"
---
# <a name="member-element-xmla"></a>Member 要素 (XMLA)
  1 つの親メンバーを表す[メンバー](members-element-xmla.md)または[タプル](tuple-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メンバー](members-element-xmla.md)、[タプル](tuple-element-xmla.md)|  
|子要素|[キャプション](caption-element-xmla.md)、 [DisplayInfo](displayinfo-element-xmla.md)、 [LName](name-element-xmla.md)、 [LNum](lnum-element-xmla.md)、 [UName](uname-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|Hieararchy|必須で、`String` 型の属性 (親要素が `Tuple` の場合のみ)。 `Member` 要素によって表されるメンバーが属する階層の名前です。|  
  
## <a name="remarks"></a>コメント  
 `Member` 要素は、特定の階層内のメンバーを識別および表示するために必要な情報を含みます。 親要素が `Members` の場合、階層は親要素の `Hierarchy` 属性によって既に指定されています。 親要素が `Tuple` の場合、`Hierarchy` 要素の `Member` 属性を使用して階層が指定されます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
