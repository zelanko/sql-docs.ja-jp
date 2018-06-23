---
title: Mode 要素 (XMLA) |Microsoft ドキュメント
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
- Mode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5634e273e1708f9de213436e20008cc6874f50a7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179396"
---
# <a name="mode-element-xmla"></a>Mode 要素 (XMLA)
  親によって使用されるモードを示す[ロック](../xml-elements-commands/lock-element-xmla.md)要素を指定したオブジェクトのロックを作成するとき。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
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
|親要素|[ロック](../xml-elements-commands/lock-element-xmla.md)、[のロックを解除](../xml-elements-commands/unlock-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親要素 `Lock` は、オブジェクトに対して作成するロックの種類を指定するために `Mode` 要素を使用します。 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*CommitShared*|指定されたオブジェクトに対して共有ロックが設定されます。 同じオブジェクトに対して他の共有ロックを作成できます。<br /><br /> 共有ロックなどの書き込み操作を含むトランザクションを使用する、 [Execute](../xml-elements-methods-execute.md)メソッドの呼び出しを実行している、 [Alter](../xml-elements-commands/alter-element-xmla.md)コマンドを共有ロックが解除されるまでにコミットしてから、指定されたオブジェクトでします。 共有ロックは、読み取り操作をなどを含むトランザクションを妨げません、 [Discover](../xml-elements-methods-discover.md)メソッドの呼び出しまたは`Execute`メソッドの呼び出しを実行している、[ステートメント](../xml-elements-commands/statement-element-xmla.md)コマンドをコミットします。|  
|*CommitExclusive*|指定されたオブジェクトに対して排他ロックが設定されます。 同じオブジェクトに対して、他の共有ロックまたは排他ロックを作成することはできません。<br /><br /> 排他ロックを使用すると、指定されたオブジェクトに対する読み取り操作または書き込み操作を伴うトランザクションは、排他ロックが解除されるまでコミットできません。|  
  
## <a name="see-also"></a>参照  
 [ID 要素&#40;XMLA&#41;](id-element-xmla.md)   
 [オブジェクトの要素&#40;XMLA&#41;](object-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  