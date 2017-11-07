---
title: "Member 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bc33ebc0cd970c58f4f27d4b49a972c9ed724c0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="member-element-csdlbi"></a>Member 要素 (CSDLBI)
  Member 要素は、その他の要素のベースとなる複合型です。  
  
 その属性は、列、メジャー、ナビゲーション プロパティ、階層、およびレベルに表示される場合があります。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、Member 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|名前||TMember 型の実装によって定義されるメンバー (列、メジャー、ナビゲーション プロパティ、階層、またはレベル) に与えられた名前|  
|Caption|可|メンバーの表示名。|  
|ContextualNameRule|可|メンバーを明確に識別するために使用される名前付け形式。 この属性の内容は ContextualNameRule 単純型によって定義されます。|  
|[非表示]||メンバーがクライアントに対して非表示になるかどうかを示すブール値です。<br /><br /> 既定値は false で、これは列がクライアントに表示されることを意味します。|  
|ReferenceName||DAX クエリでメンバーを参照するために使用される識別子。 この属性が省略されている場合は、フィールド名が使用されます。|  
  
## <a name="contextualnamerule-element"></a>ContextualNameRule 要素  
 この単純型は、メンバーを明確に識別するために使用される名前付け形式を定義します。  
  
|値|Description|  
|-----------|-----------------|  
|なし|属性名を使用します。|  
|コンテキスト|入力リレーションシップの名前を使用します。|  
|Merge|入力リレーションシップの名前とプロパティ名を連結します。|  
  
## <a name="see-also"></a>参照  
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  

