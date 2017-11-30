---
title: "UPDATE CUBE ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- UPDATE CUBE
- UPDATE_CUBE
- UPDATE
dev_langs: kbMDX
helpviewer_keywords:
- updating cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
ms.assetid: 6c8f23bb-401b-49de-843a-5324ac977239
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a006fd31f2a89215387dba48074adcb6a2add509
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-data-manipulation---update-cube"></a>MDX データ操作、UPDATE CUBE
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  UPDATE CUBE ステートメントは、SUM 集計によって親に対して集計を行うキューブ内の任意のセルにデータを書き戻すために使用します。 詳細な説明と例では、このブログ投稿の割り当てについて」を参照してください: [Analysis Services (ブログ) での書き戻しアプリケーションを構築](http://go.microsoft.com/fwlink/?LinkId=394977)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブの名前を指定する有効な文字列です。  
  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
 *New_Value*  
 有効な数値式です。  
  
 *Weight_Expression*  
 0 ～ 1 の範囲の 10 進値を返す有効な多次元式 (MDX) 数値式です。  
  
## <a name="remarks"></a>解説  
 キューブ内の指定されたリーフ セルまたは非リーフ セルの値を更新できます。指定された非リーフ セルの値を、それに依存するすべてのリーフ セルに割り当てることもできます。 Tuple_Expression で指定するセルには、多次元領域内の任意の有効なセルを指定できます (リーフ セルでなくてもかまいません)。 ただしでのセルは集計する必要があります、[合計](../mdx/sum-mdx.md)集計関数と、セルの識別に使用される組の中の計算されるメンバーを含めないでください。  
  
 役に立つと考えると、 **UPDATE CUBE**ステートメントは、一連の指定された合計にロール アップされるリーフと非リーフ セルに個々 のセルの書き戻し操作は自動的に生成するサブルーチンです。  
  
 割り当ての方法の説明を次に示します。  
  
 **USE_EQUAL_ALLOCATION:**更新されるセルに貢献するすべてのリーフ セルに次の式に基づく同じ値が割り当てられます。  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:**更新されるセルに貢献するすべてのリーフ セルは、次の式に基づいて変更されます。  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:**更新されるセルに貢献するすべてのリーフ セルに次の式に基づく同じ値が割り当てられます。  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:**更新されるセルに貢献するすべてのリーフ セルは、次の式に基づいて変更されます。  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Weight_expression を指定しない場合、 **UPDATE CUBE**ステートメントは、次の式を暗黙的に使用します。  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Weight_Expression は、0 ～ 1 の範囲の 10 進値で表す必要があります。 この値には、割り当て対象となるリーフ セルに割り当てる値の比率を指定します。 クライアント アプリケーションのプログラマは、式の割り当て値とロールアップ集計値が等しくなるように式を作成する必要があります。  
  
> [!CAUTION]  
>  クライアント アプリケーションでは、ロール アップ値の間違いやデータの不整合などの予期しない結果を避けるために、すべてのディメンションの割り当てを同時に検討しなければなりません。  
  
 各**UPDATE CUBE**割り当てがトランザクションとしてのアトミックである見なす必要があります。 つまり、数式のエラーやセキュリティ違反など、何かの理由でいずれかの割り当て操作が失敗すると、UPDATE CUBE 操作全体が失敗します。 個々の割り当て操作の計算が処理される前に、データのスナップショットが作成され、計算結果が正しいかどうかの確認が行われます。  
  
> [!CAUTION]  
>  整数を含むメジャーに対して USE_WEIGHTED_ALLOCATION の方法を使用すると、増分変更に丸めが伴うので不正確な結果が返される可能性があります。  
  
> [!IMPORTANT]  
>  更新されるセルが重ならない場合は、 **Update Isolation Level** 接続文字列プロパティを使用して、UPDATE CUBE のパフォーマンスを向上させることができます。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [MDX データ操作ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
