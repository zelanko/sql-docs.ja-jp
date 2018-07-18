---
title: Type 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a080a1af46df731befc8ab66ce925b961be9b16
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051600"
---
# <a name="type-element-xmla"></a>Type 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって実行される処理の種類を判断、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[処理]](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 Analysis Services のインスタンス上のオブジェクトで使用できる処理オプションの詳細については、次を参照してください。[多次元モデルの処理&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)します。  
  
 値、**型**要素は、次の表に示す文字列の 1 つに制限されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ProcessFull*|処理の影響を受けるオブジェクト内のすべてのデータを削除した後、そのオブジェクトを処理します。|  
|*ProcessAdd*|処理の影響を受けるオブジェクトに新しいデータを追加します。|  
|*ProcessUpdate*|処理の影響を受けるオブジェクト内のデータを更新します。|  
|*ProcessIndexes*|処理の影響を受けるオブジェクト内のインデックスと集計を、作成または再構築します。|  
|*ProcessScriptCache*|キューブが処理されている場合は、サーバーが MDX スクリプト キャッシュを再構築します。 それ以外の場合はエラーが発生します。<br /><br /> **注**キューブにのみ適用されます。|  
|*ProcessData*|処理の影響を受けるオブジェクト内のデータだけを処理します。|  
|*ProcessDefault*|処理の影響を受けるオブジェクトを最適化して完全に処理された状態に戻すために、そのオブジェクトの状態を検出してから、適切な処理オプションをそのオブジェクトに対して実行します。|  
|*ProcessClear*|処理の影響を受けるオブジェクト内のデータ、および関連するすべてのオブジェクト内のデータを削除します。|  
|*ProcessStructure*|処理の影響を受けるオブジェクトの構造だけを処理します。|  
|*ProcessClearStructureOnly*|処理の影響を受けるオブジェクトのデータだけを消去します。|  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
