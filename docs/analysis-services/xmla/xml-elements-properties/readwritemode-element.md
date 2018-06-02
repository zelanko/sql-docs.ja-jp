---
title: ReadWriteMode 要素 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0d528567e22c3ba19b49eefff10d886703a0d29a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576494"
---
# <a name="readwritemode-element"></a>ReadWriteMode 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  **ReadWriteMode**データベース プロパティを指定するかどうか、データベースで**ReadWrite**モードまたは**ReadOnly**モード。 このプロパティの使用可能な値は 2 つだけです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|ReadWrite|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[データベース]](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 データベースを作成**ReadWrite**モードのみです。 データベースを作成することはできません**ReadOnly**モード。  
  
 値、 **ReadWriteMode**要素は次の表に示す文字列の 1 つに制限されます。  
  
|[値]|説明|  
|-----------|-----------------|  
|*ReadOnly*|変更または更新をデータベースに適用できません。|  
|*読み取り/書き込み*|変更または更新をデータベースに適用できます。|  
  
## <a name="see-also"></a>参照
 [Attach 要素](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [アタッチし、Analysis Services データベースのデタッチ](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [データベースの Readwritemode](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
