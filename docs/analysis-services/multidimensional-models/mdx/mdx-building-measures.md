---
title: "MDX でのメジャーを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d7c10b66d6ba27d406c2682b2aea3b8858c8fd12
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-building-measures"></a>メジャーの MDX の作成
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]多次元式 (MDX) でメジャーとは、テーブル モデルで値を返すように式を計算することによって解決される名前付き DAX 式。 これは一見なにげない定義ですが、非常に広範囲に影響を及ぼします。 MDX クエリでメジャーを作成して使用する機能によって、テーブル データの操作能力が大幅に向上します。  
  
> [!WARNING]  
>  メジャーは、テーブル モデルでのみ定義できます。データベースが多次元モードに設定されている場合、メジャーを作成するとエラーになります。  
  
 MDX クエリの一部として定義されるメジャーを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 そのメジャーは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した計算されるメンバーを、SELECT ステートメントを修正せずに変更できます。 ただし、MDX では、DAX 式とは異なる方法でメジャーを参照します。メジャーを参照するには、[Measures] ディメンションのメンバーとして指定します。次の MDX の例を参照してください。  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 これを実行すると、次のデータが返されます。  
  
||Total Sales Amount||  
|-|------------------------|-|  
|2001|11331808.96||  
|2002|30674773.18||  
|2003|41993729.72||  
|2004|25808962.34||  
  
## <a name="see-also"></a>参照  
 [CREATE MEMBER ステートメント &#40;MDX&#41;](../../../mdx/mdx-data-definition-create-member.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [SELECT ステートメント &#40;です。MDX と #41 です。](../../../mdx/mdx-data-manipulation-select.md)  
  
  
