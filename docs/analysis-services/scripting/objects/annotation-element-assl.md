---
title: "Annotation 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Annotation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Annotation
helpviewer_keywords: Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9583acd747910621f79622383f9eda6232dff5e2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
|親要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[値](../../../analysis-services/scripting/properties/value-element-assl.md)、[可視性](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **注釈**要素は複合データ型を定義するためだけに使用されるもの以外のすべてのオブジェクトに対して、ASSL スキーマの拡張機能を提供します。 **値**の要素、**注釈**要素は、次のルールに従って、ASSL 以外の XML 名前空間から有効な XML を含めることができます。  
  
-   XML には要素のみを使用できます。  
  
-   すべての要素に一意な名前を付ける必要があります。 お勧めの値、**名前**の要素、**注釈**要素がターゲットの名前空間を参照します。  
  
 内容を許可するこれらの規則が課されて、**注釈**名前/値のセットとして公開する要素のペアを Decision Support オブジェクト (DSO) など、他のインターフェイスを使用します。  
  
 コメントおよび内の空白、**注釈**子要素で囲まれていない要素を保持することはできません。 また、すべての要素は読み取り書き込み要素である必要があり、読み取り専用要素は無視されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Annotation>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
