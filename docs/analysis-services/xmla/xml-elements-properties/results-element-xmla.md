---
title: 結果の要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 97cebdade566f796ff09bd68e8b292868e37e0a9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="results-element-xmla"></a>results 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  コレクションを格納[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)要素によって返される、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドを使用して、[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンド。  
  
 **名前空間** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[戻り値](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|子要素|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 場合、**バッチ**によってコマンドを実行、 **Execute** 、メソッド、**返す**要素には、1 つが含まれています**結果**要素の代わりに、。1 つ**ルート**要素。 内容、**結果**要素は、実行に使用される設定によって異なります、**バッチ**コマンド。  
  
 非トランザクション**バッチ**コマンド、**結果**要素を 1 つ**ルート**で実行される各コマンドの要素、**バッチ**コマンド、コマンドは成功と失敗が完了するかどうか。 トランザクション**バッチ**コマンドを**結果**要素は 1 つだけ**ルート**要素は、内で失敗したコマンドのエラー情報が含まれています、**バッチ**コマンド。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
