---
title: NameToSet (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 766049ff2c285de2b16e1aa67745a98eb22ef05f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580274"
---
# <a name="nametoset-mdx"></a>NameToSet (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 形式の文字列によって指定されているメンバーを含むセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Name*  
 メンバーの名前を表す有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 指定したメンバー名が存在する場合、 **NameToSet**関数は、そのメンバーを含むセットを返します。 そうでない場合は、空のセットを返します。  
  
> [!NOTE]  
>  メンバーの名前には、メンバー名のみを指定する必要があります。メンバー式を指定することはできません。 メンバー式を使用するのを参照してください。 [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)です。  
  
## <a name="example"></a>例  
 次の例では、指定されたメンバー名の既定のメジャー値を返しています。  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
