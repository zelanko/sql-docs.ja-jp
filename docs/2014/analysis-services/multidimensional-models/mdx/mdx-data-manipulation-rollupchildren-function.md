---
title: RollupChildren 関数の操作 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
ms.openlocfilehash: 341468d521cebe1fda33d73ea999f3b6571cb01e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546354"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a>RollupChildren 関数の操作 (MDX)
  多次元式 (MDX) [Rollupchildren](/sql/mdx/rollupchildren-mdx) [Script for Search and Replace] 関数は、メンバーの子をロールアップし、それぞれの子に異なる単項演算子を適用して、このロールアップの値を数値として返します。 単項演算子は、子メンバーに関連付けられたメンバー プロパティによって提供されるか、関数に直接指定される文字列式の場合もあります。  
  
## <a name="rollupchildren-function-examples"></a>RollupChildren 関数の例  
 `RollupChildren` 関数を多次元式 (MDX) ステートメントで使用する方法は簡単に説明できますが、この関数が MDX クエリに与える影響は広範囲にわたります。  
  
 `RollupChildren` 関数は、既存のキューブ データに対して選択的な分析を実行するように設計されている MDX クエリに影響を与えます。 たとえば、次の表は、Net Sales 親メンバーの子メンバーの一覧です。かっこ内は各子メンバーの単項演算子です (`UNARY_OPERATOR` メンバー プロパティによって表されます)。  
  
|[親メンバー]|子メンバー|  
|-------------------|------------------|  
|純売上高|国内売上 (+)<br /><br /> 国内返品 (-)<br /><br /> 国外売上 (+)<br /><br /> 国外返品 (-)|  
  
 現在、Net Sales 親メンバーは、売上の総合計から、国内と国外の返品の合計値を差し引いた値に相当します。国内と国外の返品は、ロールアップの一部として減算されています。  
  
 ここで、国内と国外の返品は無視し、国内と国外の総売上が 10% 増加した場合の予測をすばやく簡単に行いたいとします。 この値を計算するには、`RollupChildren` 関数を 2 つの方法で使用できます。1 つはカスタム メンバー プロパティを使用する方法で、もう 1 つは `IIf` 関数を使用する方法です。  
  
### <a name="using-a-custom-member-property"></a>カスタム メンバー プロパティの使用  
 ロールアップ計算を頻繁に実行する場合、特定の関数に対してそれぞれの子が使用する演算子を格納するメンバー プロパティを作成しておくという方法があります。 次の表では、有効な単項演算子を示し、予期される結果を説明します。  
  
|演算子|結果|  
|--------------|------------|  
|+|合計 = 合計 + 現在の子|  
|-|合計 = 合計 - 現在の子|  
|*|合計 = 合計 * 現在の子|  
|/|合計 = 合計 / 現在の子|  
|~|子はロールアップでは使用されません。 子の値は無視されます。|  
  
 たとえば、`SALES_OPERATOR` というメンバー プロパティを作成し、次の表に示すように、単項演算子をそのメンバー プロパティに割り当てます。  
  
|[親メンバー]|子メンバー|  
|-------------------|------------------|  
|純売上高|国内売上 (+)<br /><br /> 国内返品 (~)<br /><br /> 国外売上 (+)<br /><br /> 国外返品 (~)|  
  
 この新しいメンバー プロパティを使用すれば、次の MDX ステートメントで、総売上の予測をすばやく効率的に実行できます (国外と国内の返品は無視されます)。  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 関数が呼び出されると、それぞれの子の値は、メンバー プロパティに格納されている演算子を使用して合計に算入されます。 国内と国外の返品のメンバーは無視され、`RollupChildren` 関数によって返されるロールアップ合計に 1.1 が乗算されます。  
  
### <a name="using-the-iif-function"></a>IIf 関数の使用  
 この例の操作が一般的でない場合、または操作が1つの MDX クエリのみに適用される場合は、関数と共に[IIf](/sql/mdx/iif-mdx)関数を使用して同じ結果を得ることができ `RollupChildren` ます。 次の MDX クエリでは、前の例の MDX クエリと同じ結果を返します。ただし、カスタム メンバー プロパティは使用していません。  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 MDX ステートメントは、子メンバーの単項演算子を調べます。 単項演算子が減算 (この例では、国内と国外の返品のメンバーの場合) のために使用されている場合、`IIf` 関数はその代わりにティルダ (~) 単項演算子を使用します。 それ以外の場合、`IIf` 関数は子メンバーの単項演算子を使用します。 最後に、返されたロールアップ合計に 1.1 が乗算され、国内と国外の総売上の予測値が得られます。  
  
## <a name="see-also"></a>参照  
 [データの操作 (MDX)](mdx-data-manipulation-manipulating-data.md)  
  
  
