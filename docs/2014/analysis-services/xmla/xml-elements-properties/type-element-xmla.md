---
title: Type 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71f7745a3f3ea39309d871d5fafef737176d3a45
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054392"
---
# <a name="type-element-xmla"></a>Type 要素 (XMLA)
  によって実行される処理の種類を判断、[プロセス](../xml-elements-commands/process-element-xmla.md)要素。  
  
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
|親要素|[[処理]](../xml-elements-commands/process-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 インスタンスでオブジェクトを使用できるオプションの処理の詳細については[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[多次元モデル オブジェクトの処理](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)します。  
  
 `Type` 要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
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
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
