---
title: 共変性 (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06b86c47b5da75c44d528f77a60e8168fd8b2260
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577884"
---
# <a name="covariance-mdx"></a>Covariance (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  バイアスをかけた母集団の公式 (X と Y のペアの数で除算) を使用して、セットに対して評価された X と Y の値のペアの母共分散を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Covariance(Set_Expression,Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **共変性**関数は、y 軸の値を取得する、最初の数値式に対して指定されたセットを評価します。 次に、2 番目の数値式が指定されている場合は、指定されているセットをその式に対して評価し、X 軸の値のセットを取得します。 2 番目の数値式が指定されていない場合関数は、x 軸の値として指定されたセット内のセルの現在のコンテキストを使用します。  
  
 **共変性**関数は、バイアスをかけた母集団の公式を使用します。 これは、対照的に、 [CovarianceN](../mdx/covariancen-mdx.md)バイアスをかけない母集団の公式 (x と y のペアの数で除算し、1 を減算) を使用する関数。  
  
> [!NOTE]  
>  **共変性**関数は空のセルまたはテキストを含むセルを無視するか、論理値は無視されます。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="example"></a>例  
 次の例では、Covariance 関数を使用する方法を示します。  
  
```  
WITH   
MEMBER [Measures].[CovarianceDemo] AS  
COVARIANCE([Date].[Date].[Date].Members, [Measures].[Internet Sales Amount], [Measures].[Internet Order Count])   
SELECT {[Measures].[CovarianceDemo]} ON 0   
FROM  
[Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
