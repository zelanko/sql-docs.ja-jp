---
title: XPath クエリ (SQLXML 4.0) の使用の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 382fd81302cfccb378ef6c1a52cf996857cd2dcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083843"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>XPath クエリの使用について (SQLXML 4.0)
  XML パス言語 (XPath) クエリは、URL の一部として、またはテンプレート内で指定できます。 この結果のフラグメントの構造はマッピング スキーマによって決定され、値はデータベースから取得されます。 このプロセスは、CREATE VIEW ステートメントを使用してビューを作成し、そのビューに対して SQL クエリを記述するのと概念的には同じです。  
  
> [!NOTE]  
>  SQLXML 4.0 の XPath クエリを理解するには、XML ビューと、それに関連するテンプレートやマッピング スキーマなどの概念について理解している必要があります。 詳細については、次を参照してください。[注釈付き XSD スキーマの概要&#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)、と World Wide Web Consortium (W3C) で定義されている XPath 標準です。  
  
 XML ドキュメントは、要素ノード、属性ノード、テキスト ノードなどのノードで構成されます。 たとえば、次の XML ドキュメントを考えてみます。  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 このドキュメントで**\<顧客 >** 要素ノード、 **cid**が属性ノード、および **"Important"** テキスト ノードします。  
  
 XPath は、XML ドキュメントからノード セットを選択するときに使用できるグラフ ナビゲーション言語です。 XPath の各演算子では、前の XPath 演算子によって選択されたノード セットに基づいて、ノード セットを選択します。 たとえば、特定のセット**\<顧客 >** XPath のノードで、すべてを選択できます**\<順序 >** を持つノード、**日付**属性の値を指定します。**「7/14/1999」** です。 結果のノード セットには、注文日が 1999 年 7 月 14 日となっているすべての注文が含まれます。  
  
 XPath 言語は W3C (World Wide Web Consortium) によって標準のナビゲーション言語として定義されています。 SQLXML 4.0 である W3C XPath 仕様のサブセットを実装するhttp://www.w3.org/TR/1999/PR-xpath-19991008.htmlです。  
  
 次に、W3C XPath 実装と SQLXML 4.0 実装の主な違いを示します。  
  
-   **ルート クエリ**  
  
     SQLXML 4.0 では、ルート クエリ (/) はサポートされません。 すべての XPath クエリは、最上位から始める必要があります **\<ElementType >** スキーマです。  
  
-   **エラーの報告**  
  
     W3C XPath 仕様では、エラー状態は定義されていません。 ノードの選択に失敗した XPath クエリでは、空のノード セットが返されます。 SQLXML 4.0 では、さまざまな種類のエラー メッセージが返されます。  
  
-   **ドキュメント順**  
  
     SQL XML 4.0 では、ドキュメント序数が必ずしも決まっていません。 このため、`following` などのドキュメント序数を使用する数値型の述語や軸は実装されていません。  
  
     ドキュメント序数がないため、ノードの文字列値は、ノードが単一行の単一列にマップされる場合にのみ評価できます。 子要素を含む要素や IDREFS または NMTOKENS ノードは、文字列に変換できません。  
  
    > [!NOTE]  
    >  場合によっては、`key-fields` 注釈、または `relationship` 注釈のキーから、決定的なドキュメント序数が得られますが、 ただし、これはこれらの注釈の主な用途の詳細ではありませんを参照してください[を識別するキー列を使用して sql:key-フィールド&#40;SQLXML 4.0&#41; ](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)と[を指定するリレーションシップを使用して sql:リレーションシップ&#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)です。  
  
-   **データ型**  
  
     SQLXML 4.0 には、XPath の `string`、`number`、および `boolean` 型の実装に関して制限があります。 詳細については、次を参照してください。 [XPath データ型&#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md)です。  
  
-   **クロス積クエリ**  
  
     SQLXML 4.0 では、`Customers[Order/@OrderDate=Order/@ShipDate]` などのクロス積 XPath クエリはサポートされません。 このクエリでは、任意の Order の OrderDate が任意の Order の ShipDate と等しいすべての Customer が選択されます。  
  
     ただし、SQLXML 4.0 では、`Customer[Order[@OrderDate=@ShippedDate]]` などのクエリはサポートされます。このクエリでは、任意の Order の OrderDate とその ShipDate が等しいすべての Customer が選択されます。  
  
-   **エラー処理とセキュリティ**  
  
     使用されるスキーマと XPath クエリ式によっては、一定の条件下において、[!INCLUDE[tsql](../../includes/tsql-md.md)] エラーがユーザーに表示されることがあります。  
  
 以下に示す表では、この分野に関する SQLXML 4.0 の XPath クエリの実装と W3C 仕様の違いを詳しく説明します。  
  
## <a name="supported-functionality"></a>サポートされている機能  
 次の表は、SQLXML 4.0 で実装されている XPath 言語の機能です。  
  
|機能|アイテム|サンプル クエリへのリンク|  
|-------------|----------|----------------------------|  
|軸|`attribute`、`child`、`parent`、`self` 軸|[XPath クエリで軸を指定する&#40;SQLXML 4.0&#41;](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|連続する述語や入れ子になった述語など、ブール値を使用する述語||[XPath クエリで算術演算子を指定する&#40;SQLXML 4.0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|すべての関係演算子|=, !=, <, \<=, >, >=|[関係演算子を指定する XPath クエリで&#40;SQLXML 4.0&#41;](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|算術演算子|+、-、*、div|[XPath クエリで算術演算子を指定する&#40;SQLXML 4.0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|明示的な変換関数|`number()`、 `string()`、 `Boolean()`|[XPath クエリで明示的な変換関数を指定する&#40;SQLXML 4.0&#41;](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|ブール演算子|AND、OR|[ブール演算子を指定する XPath クエリで&#40;SQLXML 4.0&#41;](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|論理関数|`true()`、 `false()`、 `not()`|[XPath クエリ内で論理関数を指定する&#40;SQLXML 4.0&#41;](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|XPath 変数||[XPath クエリ内で XPath 変数を指定する&#40;SQLXML 4.0&#41;](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>サポートされない機能  
 次の表は、SQLXML 4.0 で実装されていない XPath 言語の機能です。  
  
|機能|アイテム|  
|-------------|----------|  
|軸|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|数値を使用する述語||  
|算術演算子|mod|  
|ノード関数|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|文字列関数|`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`|  
|論理関数|`lang()`|  
|数値関数|`sum()`, `floor()`, `ceiling()`, `round()`|  
|Union 演算子|&#124;|  
  
 テンプレートに XPath クエリを指定する場合には、次の動作に注意してください。  
  
-   XPath には、XML で特別な意味になる < や & などの文字が含まれることがあります (テンプレートは XML ドキュメントです)。 これらの文字を、XML の & エンコードを使用してエスケープするか、URL に XPath を指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 での XPath クエリの使用](using-xpath-queries-in-sqlxml-4-0.md)  
  
  