---
title: StrToTuple (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRTOTUPLE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToTuple function
ms.assetid: e162cc01-cddd-4654-baab-d73abdc33b80
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6f2d047b0745c152fe880216854a1af146dcd87f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="strtotuple-mdx"></a>StrToTuple (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 形式の文字列によって指定されている組を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Specification*  
 直接的または間接的に組を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **StrToTuple**関数には、指定されたセットが返されます。 **StrToTuple**関数は、通常のユーザー定義関数を使用、組指定を外部関数から MDX ステートメントに返します。  
  
-   CONSTRAINED フラグを使用するときは、組指定に修飾されているメンバー名または修飾されていないメンバー名を含める必要があります。 このフラグは、指定された文字列によるインジェクション攻撃の危険性を軽減するために使用します。 修飾されているメンバー名または修飾されていないメンバー名に直接解決できない文字列を指定すると、"STRTOTUPLE 関数の CONSTRAINED フラグによって設定された制限に違反しました。" というエラーが表示されます。  
  
-   CONSTRAINED フラグを使用しない場合、組を返す有効な MDX 式に解決される組を指定できます。  
  
## <a name="examples"></a>使用例  
 次の例では、2004 年の Bayern メンバーの Reseller Sales Amount メジャーを返しています。 組の指定には、有効な MDX 組式が含まれています。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2004 年の Bayern メンバーの Reseller Sales Amount メジャーを返しています。 組の指定には、CONSTRAINED フラグによって必要とされる、修飾されたメンバー名が含まれています。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、2004 年の Bayern メンバーの Reseller Sales Amount メジャーを返しています。 組の指定には、有効な MDX 組式が含まれています。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、CONSTRAINED フラグが原因でエラーが返されます。 組の指定には有効な MDX 組式が含まれていますが、CONSTRAINED フラグを使用する場合は、組の指定に修飾されたメンバー名または修飾されていないメンバー名が必要になります。  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
