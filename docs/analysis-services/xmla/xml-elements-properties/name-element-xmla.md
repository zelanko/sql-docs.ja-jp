---
title: 要素 (XMLA) の名前を付けます |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Name Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 995792653603bd7ff5954a34755e7704544675b6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="name-element-xmla"></a>Name 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]親の属性メンバーの名前を含む[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)または[翻訳](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|基数|次の表を参照してください。|  
  
|先祖または親|基数|  
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
  
  
