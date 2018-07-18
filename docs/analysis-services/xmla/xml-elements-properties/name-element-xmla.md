---
title: 要素 (XMLA) の名前を付けます |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c0686dfbb5949c9b2fe3a20e34824e731369b266
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968884"
---
# <a name="name-element-xmla"></a>Name 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|[翻訳](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)、[翻訳](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **属性**、要素、**名前**要素には挿入または実行中に、それぞれ、更新対象の属性メンバーの名前が含まれています、**挿入**または**Update**コマンド。  
  
 **翻訳**、要素、**名前**要素にはで指定された言語では、属性メンバーのキャプションが含まれています、**言語**の親要素**翻訳**オブジェクト。 場合、**名前**要素が指定されていないか、空の文字列値にはが含まれています、**名前**の要素、**属性**要素を含む、 **翻訳**要素を使用します。  
  
## <a name="see-also"></a>参照
 [要素を挿入&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [言語要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
