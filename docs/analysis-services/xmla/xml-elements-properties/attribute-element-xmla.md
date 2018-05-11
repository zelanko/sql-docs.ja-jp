---
title: 属性の要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d96ab99730997f56460ff6ce9c3cf27ddd1f6a41
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-element-xmla"></a>Attribute 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親コマンド [Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、 [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、または [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) の実行対象である属性内のメンバーを定義またはフィルター処理します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attributes>  
   ...  
   <Attribute>  
      <AttributeName>...</AttributeName>  
      <Keys>...</Keys>  
      <!-- The following elements are included only for attributes contained in the Attributes element of a parent Insert or Update command -->  
      <Name>...</Name>  
      <Translations>...</Translations>  
      <CustomRollup>...</CustomRollup>  
      <CustomRollupProperties>...</CustomRollupProperties>  
      <UnaryOperator>...</UnaryOperator>  
      <SkippedLevels>...</SkippedLevels>  
   </Attribute>  
   ...  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)、 [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)、 [Keys](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|[Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、 [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)、 [CustomRollup](../../../analysis-services/xmla/xml-elements-properties/customrollup-element-xmla.md)、 [CustomRollupProperties](../../../analysis-services/xmla/xml-elements-properties/customrollupproperties-element-xmla.md)、 [Keys](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)、 [Name](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)、 [SkippedLevels](../../../analysis-services/xmla/xml-elements-properties/skippedlevels-element-xmla.md)、 [Translations](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md)、 [UnaryOperator](../../../analysis-services/xmla/xml-elements-properties/unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **Attribute** 要素は、 **Insert**、 **Update**、または **Drop** コマンドによって、挿入、更新、または削除される属性メンバーを定義します。 1 つの属性メンバーだけで、一度に処理できるためにこれらのコマンド、[属性](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)のコレクション、**挿入**、**更新**、および**をドロップ**コマンドには、1 つだけ含めることができます**属性**要素。 ただし、 **Attributes** および **Where** コマンドの **Drop** 要素の **Update** コレクションには複数の **Attribute** 要素を含めることができ、書き込み許可ディメンション内の削除または更新対象の属性をフィルター処理できます。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)   
 [書き込み許可ディメンション](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
