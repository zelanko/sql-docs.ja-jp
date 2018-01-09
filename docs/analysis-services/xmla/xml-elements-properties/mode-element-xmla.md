---
title: "Mode 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Mode Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords: Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 656ea9623b7dea8296bc10221c916fe7afdd0568
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mode-element-xmla"></a>Mode 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]親によって使用されるモードを示す[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)要素を指定したオブジェクトのロックを作成するとき。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)、[のロックを解除](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 親**ロック**要素を使用して、**モード**要素オブジェクトを作成するロックの種類を判断します。 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|*CommitShared*|指定されたオブジェクトに対して共有ロックが設定されます。 同じオブジェクトに対して他の共有ロックを作成できます。<br /><br /> 共有ロックなどの書き込み操作を含むトランザクションを使用する、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しを実行している、 [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)コマンドを共有ロックが解除されるまでにコミットしてから、指定されたオブジェクトでします。 共有ロックは、読み取り操作をなどを含むトランザクションを妨げません、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドの呼び出しまたは**Execute**メソッドの呼び出しを実行している、[ステートメント](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)からのコマンドコミットしています。|  
|*CommitExclusive*|指定されたオブジェクトに対して排他ロックが設定されます。 同じオブジェクトに対して、他の共有ロックまたは排他ロックを作成することはできません。<br /><br /> 排他ロックを使用すると、指定されたオブジェクトに対する読み取り操作または書き込み操作を伴うトランザクションは、排他ロックが解除されるまでコミットできません。|  
  
## <a name="see-also"></a>参照  
 [ID 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Object 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
