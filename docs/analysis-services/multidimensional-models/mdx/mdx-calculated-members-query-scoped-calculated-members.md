---
title: "クエリ スコープを作成する計算されるメンバー (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8a621061e7b9b04dfea37443c631ae611ee031ab
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-calculated-members---query-scoped-calculated-members"></a>MDX の計算されるメンバーのクエリ スコープの計算されるメンバー
  1 つの多次元式 (MDX) クエリでのみ計算されるメンバーが必要な場合は、WITH キーワードを使用してその計算されるメンバーを定義できます。 WITH キーワードを使用して作成した計算されるメンバーは、そのクエリの実行が終了した時点で存在しなくなります。  
  
 このトピックで説明するように、WITH キーワードの構文は非常に柔軟なので、計算されるメンバーに基づいて別の計算されるメンバーを定義することも可能です。  
  
> [!NOTE]  
>  計算されるメンバーの詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md)」を参照してください。  
  
## <a name="with-keyword-syntax"></a>WITH キーワードの構文  
 MDX の SELECT ステートメントに WITH キーワードを追加するための構文は、以下のとおりです。  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 WITH キーワードの構文で使用する `Member_Identifier` の値は、計算されるメンバーの完全修飾名です。 完全修飾名には、計算されるメンバーを関連付けるディメンションまたはレベルが含まれます。 `MDX_Expression` の値は、その式の値が評価された後の計算されるメンバーの値を返します。 必要に応じて、 `MemberProperty_Identifier` の値にセル プロパティの名前を、 `Scalar_Expression` の値にセル プロパティの値を指定して、計算されるメンバーの固有セル プロパティの値を指定できます。  
  
## <a name="with-keyword-examples"></a>WITH キーワードの例  
 次の MDX クエリは、計算されるメンバー `[Measures].[Special Discount]`を定義し、元の割引額に基づいて特殊な割引額を計算します。  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 計算されるメンバーは、階層内のどこにでも作成できます。 たとえば、次の例に示す MDX クエリは、仮想的な Sales キューブの計算されるメンバー `[BigSeller]` を定義しています。 この計算されるメンバーは、指定したストアのビールとワインの売上数量が 100.00 以上かどうかを判別します。 ただし、このクエリは、 `[BigSeller]` という計算されるメンバーを `[Product]` ディメンションの子メンバーではなく `[Beer and Wine]` メンバーの子メンバーとして作成します。  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 計算されるメンバーの基になるメンバーは、キューブ内の既存のメンバーである必要はありません。 同じ MDX 式で定義する他の計算されるメンバーに基づく計算されるメンバーを作成することも可能です。 たとえば、次の MDX クエリは、最初の計算されるメンバー `[Measures].[Special Discount]`で作成する値に基づいて、2 番目の計算されるメンバー `[Measures].[Special Discounted Amount]`の値を生成します。  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [SELECT ステートメント (MDX)](../../../mdx/mdx-data-manipulation-select.md)   
 [計算されるメンバー &#40; のセッション スコープの作成MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
