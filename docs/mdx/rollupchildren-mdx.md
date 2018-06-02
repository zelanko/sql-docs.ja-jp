---
title: RollupChildren (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 18996c8126ceddad73aad65e50099764429b830f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580704"
---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された単項演算子を使用して、指定されたメンバーの子メンバーの値をロール アップして生成した値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Unary_Operator*  
 単項演算子を指定する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 **RollupChildren**関数は指定された単項演算子を使用して、指定されたメンバーの子の値をロールアップします。  
  
 次の表に、この関数で使用できる有効な単項演算子を示します。  
  
|演算子|結果|  
|--------------|------------|  
|**+**|合計 = 合計 + 現在の子|  
|**-**|合計 = 合計 - 現在の子|  
|**\***|合計 = 合計 * 現在の子|  
|**/**|合計 = 合計 / 現在の子|  
|**%**|合計 = (合計 / 現在の子) * 100|  
|**~**|子は、プログラムのロールアップには使用されません。 その値は無視されます。|  
  
 メンバー プロパティの演算子がこの表にない場合は、エラーが発生します。 評価の順序は、演算子の優先順位ではなく、兄弟の順序によって決まります。  
  
## <a name="example"></a>例  
 次の例は、単項演算子の代替値が格納されている "Alternate Rollup Operator" というメンバー プロパティを使用して、Account ディメンションの Net Profit 階層の子メンバーを別の方法でロール アップします。 Adventure Works キューブにはこのメンバー プロパティが存在しませんが、作成できます。 このように使用する、 **RollupChildren**予算アプリケーションの what-if 分析関数を使用できます。  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
