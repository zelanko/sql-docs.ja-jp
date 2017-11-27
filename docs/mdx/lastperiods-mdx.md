---
title: "LastPeriods (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LASTPERIODS
dev_langs:
- kbMDX
helpviewer_keywords:
- LastPeriods function
ms.assetid: a15df7a1-b261-48ed-aacc-d2804db8dbf7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dc24f14f734c697946226974a8d51761a6d8182e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバーを含む、指定されたメンバーまでのメンバーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *インデックス*  
 期間の数を指定する有効な数値式です。  
  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 場合は、指定した期間の数が正の値、 **LastPeriods**後退したメンバーで始まるメンバーのセットを返します*インデックス*-指定したメンバー式、および最後に、指定されたメンバーから 1 です。 関数によって返されるメンバーの数と等しい*インデックス*です。  
  
 指定した期間数が負の場合、 **LastPeriods**関数は、指定されたメンバーで始まるメンバーのセットが返され、潜在顧客をメンバーで終わる (-*インデックス*- 1) 指定されたメンバーからです。 関数によって返されるメンバーの数がの絶対値と等しい*インデックス*です。  
  
 指定した期間数が 0 の場合、 **LastPeriods**関数は、空のセットを返します。 これとは異なり、 **Lag**関数で 0 が指定されている場合、指定されたメンバーを返します。  
  
 メンバーが指定されていない場合、 **LastPeriods**関数は**Time.CurrentMember**です。 ディメンションが時間ディメンションに設定されていない場合、エラーを生じることなく解析および実行されますが、クライアント アプリケーションではセルのエラーが発生します。  
  
## <a name="examples"></a>使用例  
 次の例では、2002 会計年度の第 2、第 3、および第 4 会計四半期の既定のメジャーの値を返します。  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  この例は、コロン (:) 演算子を使用して記述することもできます。  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 次の例では、2002 会計年度の第 1 会計四半期の既定のメジャーの値を返します。 指定された期間の数は 3 ですが、この会計年度より前の期間が存在しないため、返すことができる期間は 1 つだけです。  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

