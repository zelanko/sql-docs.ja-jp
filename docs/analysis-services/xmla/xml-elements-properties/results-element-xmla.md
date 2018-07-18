---
title: 結果の要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7fc64d6b31f1b05d8bf5b4d1c80d75dff0583e86
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968664"
---
# <a name="results-element-xmla"></a>results 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  コレクションを含む[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)要素によって返される、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドを使用して、[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンド。  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[return](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|子要素|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 場合、**バッチ**によってコマンドが実行される、 **Execute**メソッド、**返す**要素には、1 つが含まれています**結果**要素の代わりに、。1 つ**ルート**要素。 コンテンツ、**結果**要素は、実行に使用される設定によって異なります、**バッチ**コマンド。  
  
 非トランザクション**バッチ**コマンドを**結果**要素には、1 つ含まれる**ルート**で実行される各コマンドの要素、**バッチ**コマンド、成功したか、コマンドが完了するかどうか。 トランザクション**バッチ**コマンド、**結果**要素が 1 つだけ含まれています**ルート**内で失敗したコマンドのエラー情報を格納する要素を**バッチ**コマンド。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
