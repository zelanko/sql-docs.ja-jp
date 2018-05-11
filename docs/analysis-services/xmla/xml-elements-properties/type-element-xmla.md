---
title: Type 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef8d986b50eb3d5efc8e490f198862be7400e566
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-xmla"></a>Type 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって実行される処理の種類を決定、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)要素。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[処理]](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 インスタンスでオブジェクトを使用できるオプションの処理の詳細については[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[多次元モデルの処理&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)です。  
  
 値、**型**要素は次の表に示す文字列の 1 つに制限されます。  
  
|値|Description|  
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
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
