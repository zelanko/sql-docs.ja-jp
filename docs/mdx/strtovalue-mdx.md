---
title: StrToValue (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cad8fec605a56a60cfcc7024739225e474fd42f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036692"
---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)


  多次元式 (MDX) 形式の文字列で指定された数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *MDX_Expression*  
 直接的または間接的に 1 つのセルに解決される有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **Strtovalue**関数は、MDX 式によって指定された数値を返します。 **Strtovalue**関数は、通常、ユーザー定義関数と共に使用して、mdx 式を外部関数から mdx ステートメントに返し、1つのセルに解決できるようにします。  
  
-   CONSTRAINED フラグを使用する場合、MDX 式にはスカラー値のみを含める必要があります。 CONSTRAINED フラグは、指定された文字列によるインジェクション攻撃の危険性を軽減するために使用します。 直接スカラー値に解決できない MDX 式を指定すると、"STRTOVALUE 関数の CONSTRAINED フラグによって設定された制限に違反しました。" というエラー メッセージが表示されます。  
  
-   CONSTRAINED フラグを使用しない場合は、1 つのセルを返す有効な多次元式 (MDX) 式に解決される範囲で複雑な MDX 式を指定できます。  
  
> [!NOTE]  
>  MDX 式の結果を数値として返すと、値がテキストとして格納され、戻り値に対して算術演算を実行する場合に役立ちます。  
  
## <a name="example"></a>例  
 次の例では、 **Strtovalue**関数を使用して、各自転車の重量を値として返します。  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
