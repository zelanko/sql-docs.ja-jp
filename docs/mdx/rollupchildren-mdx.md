---
title: "RollupChildren (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROLLUPCHILDREN
dev_langs:
- kbMDX
helpviewer_keywords:
- RollupChildren function
ms.assetid: 6f092540-067d-443f-b631-8523836a0d86
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b29a351d8425d235adc29b8a5b997915b70de047
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

