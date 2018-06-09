---
title: CASE ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fb53db11e9c7ec816299d1541d27e962ab8650df
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740111"
---
# <a name="case-statement-mdx"></a>CASE ステートメント (MDX)


  複数の比較から、条件付きで特定の値を返します。 case ステートメントには、次の 2 種類があります。  
  
-   単純 case ステートメントは、1 つの式を一連の単純式と比較して、特定の値を返します。  
  
-   検索 case ステートメントは、一連のブール式を評価して、特定の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Simple Case Statement  
CASE [input_expression]  
WHEN when_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
  
Search Case Statement  
CASE   
WHEN Boolean_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
```  
  
## <a name="arguments"></a>引数  
 *input_expression*  
 スカラー値に解決される多次元式 (MDX) 式です。  
  
 *when_expression*  
 指定された対象となるスカラー値、 *input_expression*が評価され、true を返しますのスカラー値に評価されるときにどの、*戻り値*です。  
  
 *when_true_result_expression*  
 ときに返すスカラー値を true に評価される WHEN 句。  
  
 *戻り値*  
 WHEN 句が true と評価された場合に返されるスカラー値です。  
  
 *Boolean_expression*  
 スカラー値に評価される MDX 式です。  
  
## <a name="remarks"></a>コメント  
 ELSE 句が指定されていない場合、すべての WHEN 句が false と評価されると、結果は空のセルになります。  
  
## <a name="simple-case-expression"></a>単純 case 式  
 MDX では、解決することによって単純 case 式を評価、 *input_expression*スカラー値にします。 このスカラー値はのスカラー値と比較し、 *when_expression*です。 CASE ステートメントの値を返します 2 つのスカラー値が一致した場合、 *when_true_expression*です。 2 つのスカラー値が一致しなかった場合は、次の WHEN 句が評価されます。 WHEN 句のすべてが false の値に評価されるかどうか*戻り値*から、ELSE 句が存在する場合、返されます。  
  
 次の例では、Reseller Order Count メジャーを複数の WHEN 句に対して評価し、年ごとに Reseller Order Count メジャーの値に基づいて結果を返しています。 Reseller Order Count 値で指定したスカラー値と一致しないため、 *when_expression* WHEN 句のスカラー値で、*戻り値*が返されます。  
  
```  
WITH MEMBER [Measures].x AS   
CASE [Measures].[Reseller Order Count]  
   WHEN 0 THEN 'NONE'  
   WHEN 1 THEN 'SMALL'  
   WHEN 2 THEN 'SMALL'  
   WHEN 3 THEN 'MEDIUM'  
   WHEN 4 THEN 'MEDIUM'  
   WHEN 5 THEN 'LARGE'  
   WHEN 6 THEN 'LARGE'  
      ELSE 'VERY LARGE'  
END  
SELECT Calendar.[Calendar Year] on 0  
, NON EMPTY [Geography].[Postal Code].Members ON 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="searched-case-expression"></a>検索 case 式  
 case 式でもっと複雑な評価を実行するには、検索 case 式を使用します。 検索式の 1 つである検索 case 式を使用すると、入力式が一定範囲内の値であるかどうかを評価できます。 MDX は、WHEN 句を CASE ステートメント内に出現する順序で評価します。  
  
 次の例では、Reseller Order Count メジャーが評価される、指定された*Boolean_expression*につき複数の WHEN 句。 年ごとの Reseller Order Count メジャーの値に基づいて、結果が返されます。 個々の WHEN 句は出現順序で評価されるので、それぞれの値を明示的に指定しなくても、6 より大きい値にはすべて、"VERY LARGE" という値を容易に割り当てることができます。 WHEN 句のスカラー値で指定されていない Reseller Order Count 値に対して、*戻り値*が返されます。  
  
```  
WITH MEMBER [Measures].x AS   
CASE   
   WHEN [Measures].[Reseller Order Count] > 6 THEN 'VERY LARGE'  
   WHEN [Measures].[Reseller Order Count] > 4 THEN 'LARGE'  
   WHEN [Measures].[Reseller Order Count] > 2 THEN 'MEDIUM'  
   WHEN [Measures].[Reseller Order Count] > 0 THEN 'SMALL'  
   ELSE "NONE"  
END  
SELECT Calendar.[Calendar Year] on 0,  
NON EMPTY [Geography].[Postal Code].Members on 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="see-also"></a>参照  
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
