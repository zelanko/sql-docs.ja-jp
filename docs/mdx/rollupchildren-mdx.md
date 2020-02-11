---
title: RollupChildren (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 89f7545af0d98de2a6bd97630a893057aac36b12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037048"
---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)


  指定された単項演算子を使用して、指定されたメンバーの子の値をロールアップすることによって生成される値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Unary_Operator*  
 単項演算子を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **Rollupchildren**関数は、指定された単項演算子を使用して、指定されたメンバーの子の値をロールアップします。  
  
 次の表では、この関数の有効な単項演算子について説明します。  
  
|演算子|結果|  
|--------------|------------|  
|**+**|合計 = 合計 + 現在の子|  
|**-**|合計 = 合計 - 現在の子|  
|**\***|合計 = 合計 * 現在の子|  
|**/**|合計 = 合計 / 現在の子|  
|**%**|合計 = (合計/現在の子) * 100|  
|**~**|子はロールアップでは使用されません。 この値は無視されます。|  
  
 メンバープロパティの演算子が一覧に表示されない場合は、エラーが発生します。 評価の順序は、演算子の優先順位ではなく、兄弟の順序によって決まります。  
  
## <a name="example"></a>例  
 次の例は、単項演算子の代替値が格納されている "Alternate Rollup Operator" というメンバー プロパティを使用して、Account ディメンションの Net Profit 階層の子メンバーを別の方法でロール アップします。 このメンバープロパティは、Adventure Works キューブには存在しませんが、作成することもできます。 この**Rollupchildren**関数の使用は、what-if 分析のために、予算アプリケーションで使用できます。  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
