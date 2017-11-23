---
title: "Type 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords: Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 51a4b4a76054aa5c425533561add9ca8405039e1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="type-element-xmla"></a>Type 要素 (XMLA)
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
 インスタンスでオブジェクトを使用できるオプションの処理の詳細については[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
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
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
