---
title: 属性の要素 (XMLA) |Microsoft ドキュメント
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
caps.latest.revision: 17
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 665626323e435eeed50b73f4d94de4506dba4f19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073827"
---
# <a name="attribute-element-xmla"></a>Attribute 要素 (XMLA)
  定義またはフィルターの対象である属性内のメンバー、親[挿入](../xml-elements-commands/insert-element-xmla.md)、[更新](../xml-elements-commands/update-element-xmla.md)、または[ドロップ](../xml-elements-commands/drop-element-xmla.md)コマンドを実行します。  
  
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
|[挿入](../xml-elements-commands/insert-element-xmla.md)、[更新](../xml-elements-commands/update-element-xmla.md)|[AttributeName](name-element-xmla.md)、 [[customrollup]](customrollup-element-xmla.md)、 [[customrollupproperties]](properties-element-xmla.md)、[キー](keys-element-xmla.md)、[名前](name-element-xmla.md)、 [SkippedLevels](skippedlevels-element-xmla.md)、[翻訳](translations-element-xmla.md)、 [[unaryoperator]](unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Attribute`要素が挿入、更新、または削除して、それぞれ、属性メンバーの定義、 `Insert`、 `Update`、または`Drop`コマンド。 1 つの属性メンバーだけで、一度に処理できるためにこれらのコマンド、[属性](attributes-element-xmla.md)のコレクション、 `Insert`、 `Update`、および`Drop`コマンドには、1 つだけ含めることができます`Attribute`要素。 ただし、`Attributes` および `Where` コマンドの `Drop` 要素の `Update` コレクションには複数の `Attribute` 要素を含めることができ、書き込み許可ディメンション内の削除または更新対象の属性をフィルター処理できます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)   
 [書き込み許可ディメンション](../../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  