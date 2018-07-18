---
title: ReadWriteMode 要素 |Microsoft Docs
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994854"
---
# <a name="readwritemode-element"></a>ReadWriteMode 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  **ReadWriteMode**データベース プロパティは、データベースがあるかどうかを指定します**ReadWrite**モードまたは**ReadOnly**モード。 このプロパティの使用可能な値は 2 つだけです。  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[データベース]](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 データベースに作成されます**ReadWrite**モードのみです。 データベースを作成することはできません**ReadOnly**モード。  
  
 値、 **ReadWriteMode**要素は、次の表に示す文字列の 1 つに制限されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ReadOnly*|変更または更新をデータベースに適用できません。|  
|*ReadWrite*|変更または更新をデータベースに適用できます。|  
  
## <a name="see-also"></a>参照
 [Attach 要素](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [アタッチし、Analysis Services データベースのデタッチ](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [データベースの Readwritemode](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
