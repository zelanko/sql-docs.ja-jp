---
title: "UserName (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: UserName
dev_langs: kbMDX
helpviewer_keywords: UserName function
ms.assetid: ecae549b-5c5e-4483-84e6-b713cd297d7e
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ce19801da4c9748852a9c2508bbbde259ebd9c83
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="username-mdx"></a>UserName (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  現在の接続のドメイン名とユーザー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
