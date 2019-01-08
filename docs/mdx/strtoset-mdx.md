---
title: StrToSet (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ee1e0cbeaa4e33be223e1b777ff243b5c3ef2d01
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52524414"
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)


  MDX 形式の文字列によって指定されたセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *Set_Specification*  
 直接的または間接的にセットを指定する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 **StrToSet**関数は、文字列式で指定されたセットを返します。 **StrToSet**またはを返すセットの指定を外部関数から MDX ステートメントで MDX クエリがパラメーター化されたときに関数が通常使用のユーザー定義関数。  
  
-   修飾名または修飾されていないメンバー名または修飾名または修飾されていないメンバー名の中かっこで囲まれたを含む組のセットをセットの指定を含める必要があります、CONSTRAINED フラグを使用すると、{}します。 このフラグは、指定された文字列によるインジェクション攻撃の危険性を軽減するために使用します。 文字列が指定されている場合は、修飾名または修飾されていないに直接解決できないメンバー名は次のエラーが表示されます。"CONSTRAINED によって設定された制限 STRTOSET 関数でフラグに違反しました"。  
  
-   CONSTRAINED フラグを使用しない場合、セットを返す有効な多次元式 (MDX) 式に解決されるセットの指定を指定できます。  
  
-   セットとメンバーの違いを理解するには、「セット式の使用」および「メンバー式の使用」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例を使用して、State-province 属性階層のメンバーのセットを返します、 **StrToSet**関数。 セットの指定には、有効な MDX セット式が指定されています。  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、CONSTRAINED フラグが原因でエラーが返されます。 セットの指定には有効な MDX セット式が指定されていますが、CONSTRAINED フラグを使用する場合は、セットの指定に修飾されたメンバー名または修飾されていないメンバー名を含める必要があります。  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、ドイツとカナダの Reseller Sales Amount メジャーを返しています。 セットの指定には、CONSTRAINED フラグによって必要とされる、修飾されたメンバー名が含まれています。  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
