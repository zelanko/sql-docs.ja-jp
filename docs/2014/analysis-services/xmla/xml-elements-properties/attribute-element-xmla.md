---
title: 要素 (XMLA) の属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Attribute Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords:
- Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7baad7e154cda5ce52e67f08af46e7344f6af1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128212"
---
# <a name="attribute-element-xmla"></a>Attribute 要素 (XMLA)
  定義またはとする属性のメンバーをフィルター処理を親[挿入](../xml-elements-commands/insert-element-xmla.md)、 [Update](../xml-elements-commands/update-element-xmla.md)、または[ドロップ](../xml-elements-commands/drop-element-xmla.md)コマンドを実行します。  
  
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
|親要素|[Attributes](attributes-element-xmla.md)|  
  
 **子要素**  
  
|||  
|-|-|  
|**先祖または親**|**子要素**|  
|[Drop](../xml-elements-commands/drop-element-xmla.md)、[場所](name-element-xmla.md)、[キー](keys-element-xmla.md)|  
|[挿入](../xml-elements-commands/insert-element-xmla.md)、 [Update](../xml-elements-commands/update-element-xmla.md)|[AttributeName](name-element-xmla.md)、 [CustomRollup](customrollup-element-xmla.md)、 [CustomRollupProperties](properties-element-xmla.md)、[キー](keys-element-xmla.md)、[名前](name-element-xmla.md)、 [SkippedLevels](skippedlevels-element-xmla.md)、[翻訳](translations-element-xmla.md)、 [[unaryoperator]](unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Attribute`要素が挿入、更新、または削除によって、属性メンバーの定義、 `Insert`、 `Update`、または`Drop`コマンド。 一度に 1 つの属性のメンバーでのみこれらのコマンドが処理できるため、[属性](attributes-element-xmla.md)のコレクション、 `Insert`、 `Update`、および`Drop`コマンドは 1 つだけを含めることができます`Attribute`要素。 ただし、`Attributes` および `Where` コマンドの `Drop` 要素の `Update` コレクションには複数の `Attribute` 要素を含めることができ、書き込み許可ディメンション内の削除または更新対象の属性をフィルター処理できます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)   
 [書き込み許可ディメンション](../../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
