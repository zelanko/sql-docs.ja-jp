---
title: Mode 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 12e792c51b2f6feb3edb4e01c12dcf4809e2d4d4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575754"
---
# <a name="mode-element-xmla"></a>Mode 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親によって使用されるモードを示す[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)要素を指定したオブジェクトのロックを作成するとき。  
  
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
|親要素|[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)、[のロックを解除](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親**ロック**要素を使用して、**モード**要素オブジェクトを作成するロックの種類を判断します。 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*CommitShared*|指定されたオブジェクトに対して共有ロックが設定されます。 同じオブジェクトに対して他の共有ロックを作成できます。<br /><br /> 共有ロックなどの書き込み操作を含むトランザクションを使用する、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しを実行している、 [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)コマンドを共有ロックが解除されるまでにコミットしてから、指定されたオブジェクトでします。 共有ロックは、読み取り操作をなどを含むトランザクションを妨げません、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドの呼び出しまたは**Execute**メソッドの呼び出しを実行している、[ステートメント](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)からのコマンドコミットしています。|  
|*CommitExclusive*|指定されたオブジェクトに対して排他ロックが設定されます。 同じオブジェクトに対して、他の共有ロックまたは排他ロックを作成することはできません。<br /><br /> 排他ロックを使用すると、指定されたオブジェクトに対する読み取り操作または書き込み操作を伴うトランザクションは、排他ロックが解除されるまでコミットできません。|  
  
## <a name="see-also"></a>参照
 [ID 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [オブジェクトの要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
