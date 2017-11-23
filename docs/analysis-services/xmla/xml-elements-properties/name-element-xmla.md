---
title: "要素 (XMLA) の名前を付けます |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Name Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords: Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 112f5f154bcbdb262542ba81859304fc5af8e632
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="name-element-xmla"></a>Name 要素 (XMLA)
  親の属性メンバーの名前を含む[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)または[翻訳](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|[翻訳](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)、[翻訳](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **属性**、要素、**名前**要素が挿入または実行時に、それぞれ、更新される属性メンバーの名前を含む、**挿入**または**更新**コマンド。  
  
 **翻訳**、要素、**名前**要素で指定された言語では、属性メンバーのキャプションを格納する、**言語**の親要素**翻訳**オブジェクト。 場合、**名前**要素が指定されていないか、空の文字列値にはが含まれています、**名前**要素を**属性**要素を含む、 **翻訳**要素を使用します。  
  
## <a name="see-also"></a>参照  
 [要素 &#40; を挿入します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [言語要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Update 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
