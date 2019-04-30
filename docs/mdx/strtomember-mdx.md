---
title: StrToMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c5878a553895dccc3350ddbae9397d5a48c6349
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149272"
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)


  MDX 形式の文字列によって指定されたメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *Member_Name*  
 、直接的または間接的にメンバーを指定する有効な文字列式。  
  
## <a name="remarks"></a>コメント  
 **StrToMember**関数、文字列式で指定されたメンバーを返します。 **StrToMember**またはを返す、メンバー指定を外部関数から MDX ステートメントで MDX クエリがパラメーター化されたときに関数が通常使用のユーザー定義関数。  
  
-   CONSTRAINED フラグを使用するときは、メンバー名には修飾されているメンバー名または修飾されていないメンバー名に直接解決できる文字列を指定する必要があります。 このフラグは、指定された文字列によるインジェクション攻撃のリスク軽減のために使用されます。 文字列は、修飾名または修飾されていないメンバー名に直接解決ではありませんが、次のエラーが表示されます。"CONSTRAINED によって設定された制限 STRTOMEMBER 関数でフラグに違反しました"。  
  
-   CONSTRAINED フラグを使用しない場合、メンバー名に直接解決されるメンバーも、名前に解決される MDX 式に解決されるメンバーも指定できます。  
  
-   セットとメンバー間の違いを理解するには、セット式を使用して、メンバー式の使用を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、Bayern メンバーの Reseller Sales Amount メジャーを返しますを使用して、State-province 属性階層で、 **StrToMember**関数。 文字列の指定により、修飾されているメンバー名が指定されています。  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 次の例を使用して、Bayern メンバーの Reseller Sales Amount メジャーを返します、 **StrToMember**関数。 メンバー名文字列には修飾されていないメンバー名のみを指定したので、クエリは指定メンバーの最初のインスタンスを返します。この最初のインスタンスは、Reseller Sales と交差しない Customer ディメンションの Customer Geography 階層にあります。 ベスト プラクティスでは、予想される結果を得ることの修飾名を指定することによって決まります。  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 次の例では、Bayern メンバーの Reseller Sales Amount メジャーを返しますを使用して、State-province 属性階層で、 **StrToMember**関数。 指定されたメンバー名文字列は、修飾されたメンバー名に解決されます。  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 次の例では、CONSTRAINED フラグによってエラーを返します。 指定されたメンバー名文字列には、修飾されたメンバー名に解決される有効な MDX メンバー式が含まれますが、CONSTRAINED フラグによって、メンバー名文字列内の修飾名または修飾されていないメンバー名が必要です。  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
