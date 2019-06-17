---
title: StrToTuple (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 054786440afaf2b7ab458b4704bd5f8e2e26c135
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136165"
---
# <a name="strtotuple-mdx"></a>StrToTuple (MDX)


  MDX 形式の文字列によって指定された組を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Specification*  
 直接的または間接的に組を指定する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 **StrToTuple**関数は、指定されたセットを返します。 **StrToTuple**組指定を外部関数から MDX ステートメントを返す関数は通常使用のユーザー定義関数。  
  
-   CONSTRAINED フラグを使用するときは、組指定に修飾されているメンバー名または修飾されていないメンバー名を含める必要があります。 このフラグは、指定された文字列によるインジェクション攻撃のリスク軽減のために使用されます。 文字列が指定されている場合は、修飾名または修飾されていないに直接解決できないメンバー名は次のエラーが表示されます。"CONSTRAINED によって設定された制限 STRTOTUPLE 関数でフラグに違反しました"。  
  
-   CONSTRAINED フラグを使用しない場合、組を返す有効な MDX 式に解決される組を指定できます。  
  
## <a name="examples"></a>使用例  
 次の例では、2004 年の Bayern メンバーの Reseller Sales Amount メジャーを返します。 組の指定には、有効な MDX 組式が含まれています。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2004 年の Bayern メンバーの Reseller Sales Amount メジャーを返します。 提供されている組の指定には、CONSTRAINED フラグによって必要に応じて、修飾されたメンバー名が含まれています。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2004 年の Bayern メンバーの Reseller Sales Amount メジャーを返します。 組の指定には、有効な MDX 組式が含まれています。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、CONSTRAINED フラグによってエラーを返します。 指定された組の指定には、有効な MDX 組式が含まれますが、CONSTRAINED フラグには、組仕様内の修飾名または修飾されていないメンバー名が必要です。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
