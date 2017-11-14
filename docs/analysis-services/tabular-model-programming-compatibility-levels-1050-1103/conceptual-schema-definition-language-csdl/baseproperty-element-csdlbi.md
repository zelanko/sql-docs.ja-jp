---
title: "BaseProperty 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b82b9b6f137b09768fbfdadb78d98f9cd293e81e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="baseproperty-element-csdlbi"></a>BaseProperty 要素 (CSDLBI)
  BaseProperty 要素は、その他の要素のベースとなる複合型です。  
  
 その属性は列とメジャーに表示できます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、BaseProperty 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|Alignment|いいえ|Member 型の実装によって定義されるメンバー (列、メジャー、ナビゲーション プロパティ、階層、またはレベル) に与えられた名前。|  
|FormatString|いいえ|メンバーの表示名。|  
|IsRightToLeft|いいえ|右から左に読むことができるテキストをフィールドが含むかどうかを示すブール値。<br /><br /> この属性が省略されると、(モデルの) 既定の設定が使用されます。|  
|SortDirection|いいえ|フィールド値の一般的な並べ替え方法を示す値。 この属性の内容は SortDirection 単純型によって定義されます。<br /><br /> この属性が省略されると、フィールドのデータ型に基づいて既定の並べ替え方向が決定されます。|  
|単位|いいえ|単位を表現するためにフィールド値に適用される記号。<br /><br /> 省略された場合、単位は不明です。|  
  
## <a name="alignment-element"></a>Alignment 要素  
 この単純型は、メンバーを明確に識別するために使用される名前付け形式を定義します。  
  
|値|Description|  
|-----------|-----------------|  
|なし|属性名を使用します。|  
|コンテキスト|入力リレーションシップの名前を使用します。|  
|Merge|現行の文法に従って、入力リレーションシップの名前とプロパティの名前を連結します。|  
  
## <a name="sortdirection-element"></a>SortDirection 要素  
 この単純型は、メンバーを明確に識別するために使用される名前付け形式を定義します。  
  
|値|Description|  
|-----------|-----------------|  
|なし|属性名を使用します。|  
|コンテキスト|入力リレーションシップの名前を使用します。|  
|Merge|入力リレーションシップの名前とプロパティ名を連結します。|  
  
## <a name="see-also"></a>参照  
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  

