---
title: Member 要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f193cb746b8df43c33aa65ea3d69d87ab7c36655
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218832"
---
# <a name="member-element-csdlbi"></a>Member 要素 (CSDLBI)
  Member 要素は、その他の要素のベースとなる複合型です。  
  
 その属性は、列、メジャー、ナビゲーション プロパティ、階層、およびレベルに表示される場合があります。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、Member 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|名前||TMember 型の実装によって定義されるメンバー (列、メジャー、ナビゲーション プロパティ、階層、またはレベル) に与えられた名前|  
|Caption|はい|メンバーの表示名。|  
|ContextualNameRule|はい|メンバーを明確に識別するために使用される名前付け形式。 この属性の内容は ContextualNameRule 単純型によって定義されます。|  
|[非表示]||メンバーがクライアントに対して非表示になるかどうかを示すブール値です。<br /><br /> 既定値は false で、これは列がクライアントに表示されることを意味します。|  
|ReferenceName||DAX クエリでメンバーを参照するために使用される識別子。 この属性が省略されている場合は、フィールド名が使用されます。|  
  
## <a name="contextualnamerule-element"></a>ContextualNameRule 要素  
 この単純型は、メンバーを明確に識別するために使用される名前付け形式を定義します。  
  
|値|説明|  
|-----------|-----------------|  
|なし|属性名を使用します。|  
|コンテキスト|入力リレーションシップの名前を使用します。|  
|Merge|入力リレーションシップの名前とプロパティ名を連結します。|  
  
## <a name="see-also"></a>関連項目  
 [テーブル オブジェクト モデルについて](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
