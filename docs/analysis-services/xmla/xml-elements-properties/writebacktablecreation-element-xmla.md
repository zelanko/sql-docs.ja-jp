---
title: WritebackTableCreation 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e04f44d9caa3ae51ea141997e83de54524000fee
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046732"
---
# <a name="writebacktablecreation-element-xmla"></a>WritebackTableCreation 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  中に、書き戻しテーブルを作成するかどうかを決定、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)操作。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[処理]](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 Analysis Services インスタンス上のオブジェクトで使用できる処理オプションの詳細については、次を参照してください。[多次元モデルの処理&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)します。  
  
 値、 **WritebackTableCreation**要素は、次の表に示す文字列の 1 つに制限されています。  
  
|値|説明|  
|-----------|-----------------|  
|*作成*|既存の書き戻しテーブルが存在しない場合、新しい書き戻しテーブルを作成します。 書き戻しテーブルが既に存在する場合、エラーが発生します。|  
|*CreateAlways*|既存の書き戻しテーブルを上書きする、新しい書き戻しテーブルを作成します。|  
|*UseExisting*|既に存在する場合は、既存の書き戻しテーブルを使用します。 存在しない場合は、エラーが発生します。|  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
