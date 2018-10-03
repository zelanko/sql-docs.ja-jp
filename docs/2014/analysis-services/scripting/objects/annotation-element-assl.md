---
title: Annotation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Annotation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c8c8b70e9e15e01a0864cd9f3491aa188be6777
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103402"
---
# <a name="annotation-element-assl"></a>Annotation 要素 (ASSL)
  Analysis Services スクリプト言語 (ASSL) スキーマを拡張するために使用される要素を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
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
|親要素|[注釈](../collections/annotations-element-assl.md)|  
|子要素|[名前](../properties/name-element-assl.md)、[値](../properties/value-element-assl.md)、[可視性](../properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `Annotation` 要素は、複雑なデータ型を定義するためにのみ使用されるオブジェクト以外のすべてのオブジェクトに対して、ASSL スキーマの拡張性を提供します。 `Value` 要素の `Annotation` 要素には、次のルールに従って、ASSL 以外の XML 名前空間の有効な XML を使用できます。  
  
-   XML には要素のみを使用できます。  
  
-   すべての要素に一意な名前を付ける必要があります。 `Name` 要素の `Annotation` 要素の値が対象の名前空間を参照するように指定してください。  
  
 これらのルールは、`Annotation` 要素の内容を名前/値ペアのセットとして Decision Support オブジェクト (DSO) などの他のインターフェイスを介して公開できるようにするために設定されています。  
  
 子要素で囲まれていない `Annotation` 要素内のコメントおよび空白は保存されません。 また、すべての要素は読み取り書き込み要素である必要があり、読み取り専用要素は無視されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Annotation>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
