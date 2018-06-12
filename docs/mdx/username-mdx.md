---
title: UserName (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f8c08855d70d6a880607cc4310e6adcabbf7d9ad
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743481"
---
# <a name="username-mdx"></a>UserName (MDX)


  現在の接続のドメイン名とユーザー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>コメント  
 返される値は、次の形式の文字列です。  
  
 *ドメイン名 \ ユーザー名*  
  
## <a name="example"></a>例  
 次の例では、クエリを実行しているユーザーのユーザー名を返しています。  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
