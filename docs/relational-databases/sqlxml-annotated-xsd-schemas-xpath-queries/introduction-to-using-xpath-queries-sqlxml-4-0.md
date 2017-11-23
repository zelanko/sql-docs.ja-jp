---
title: "XPath クエリ (SQLXML 4.0) の使用の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9113df3519ab212f3647b96c63620167c7913ffb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>XPath クエリの使用について (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]XML パス言語 (XPath) クエリは、テンプレート内の URL の一部として指定できます。 この結果のフラグメントの構造はマッピング スキーマによって決定され、値はデータベースから取得されます。 このプロセスは、CREATE VIEW ステートメントを使用してビューを作成し、そのビューに対して SQL クエリを記述するのと概念的には同じです。  
  
> [!NOTE]  
>  SQLXML 4.0 の XPath クエリを理解するには、XML ビューと、それに関連するテンプレートやマッピング スキーマなどの概念について理解している必要があります。 詳細については、次を参照してください[注釈付き XSD スキーマの選択 &#40; の概要。SQLXML 4.0 &#41;](../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)と World Wide Web Consortium (W3C) で定義されている XPath 標準です。  
  
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
  
 このドキュメントで**\<顧客 >**要素ノード、 **cid**が属性ノード、および**"Important"**テキスト ノードします。  
  
 XPath は、XML ドキュメントからノード セットを選択するときに使用できるグラフ ナビゲーション言語です。 XPath の各演算子では、前の XPath 演算子によって選択されたノード セットに基づいて、ノード セットを選択します。 たとえば、特定のセット**\<顧客 >** XPath のノードで、すべてを選択できます**\<順序 >**を持つノード、**日付**属性の値を指定します。**「7/14/1999」**です。 結果のノード セットには、注文日が 1999 年 7 月 14 日となっているすべての注文が含まれます。  
  
 XPath 言語は W3C (World Wide Web Consortium) によって標準のナビゲーション言語として定義されています。 SQLXML 4.0 には W3C XPath 仕様のサブセットが実装されています。W3C XPath 仕様は http://www.w3.org/TR/1999/PR-xpath-19991008.html にあります。  
  
 次に、W3C XPath 実装と SQLXML 4.0 実装の主な違いを示します。  
  
-   **ルート クエリ**  
  
     SQLXML 4.0 では、ルート クエリ (/) はサポートされません。 すべての XPath クエリは、最上位から始める必要があります **\<ElementType >**スキーマです。  
  
-   **エラーの報告**  
  
     W3C XPath 仕様では、エラー状態は定義されていません。 ノードの選択に失敗した XPath クエリでは、空のノード セットが返されます。 SQLXML 4.0 では、さまざまな種類のエラー メッセージが返されます。  
  
-   **ドキュメント順**  
  
     SQL XML 4.0 では、ドキュメント序数が必ずしも決まっていません。 そのため、数値型の述語し、軸を使用してドキュメントの順序 (など**次**) が実装されていません。  
  
     ドキュメント序数がないため、ノードの文字列値は、ノードが単一行の単一列にマップされる場合にのみ評価できます。 子要素を含む要素や IDREFS または NMTOKENS ノードは、文字列に変換できません。  
  
    > [!NOTE]  
    >  場合によっては、**キー フィールド**注釈、またはキーを**リレーションシップ**注釈決定的なドキュメントの順序で発生することができます。 ただし、これはこれらの注釈の主な用途の詳細ではありませんを参照してください[sql:key を識別するキーを使用した列のフィールドと #40 です。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)と[sql:relationship を指定するリレーションシップを使用する &#40;です。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).  
  
-   **データ型**  
  
     SQLXML 4.0 の XPath の実装の制限があります**文字列**、**数**、および**ブール**データ型。 詳細については、次を参照してください。 [XPath データ型 &#40;です。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).  
  
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
|軸|**属性**、**子**、**親**、および**self**軸|[XPath クエリで軸 &#40; を指定します。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|連続する述語や入れ子になった述語など、ブール値を使用する述語||[XPath クエリ &#40; での算術演算子の指定SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|すべての関係演算子|=, !=, <, \<=, >, >=|[XPath クエリ &#40; での関係演算子の指定SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|算術演算子|+、-、*、div|[XPath クエリ &#40; での算術演算子の指定SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|明示的な変換関数|**number()**、 **string()**、**なく Boolean()**|[XPath クエリ &#40; での明示的な変換関数の指定SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|ブール演算子|AND、OR|[XPath クエリ &#40; でのブール演算子の指定SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|論理関数|**true()**、 **false()**、 **not()**|[XPath クエリのブール関数 &#40; を指定します。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|XPath 変数||[XPath クエリ &#40; XPath 変数を指定します。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>サポートされない機能  
 次の表は、SQLXML 4.0 で実装されていない XPath 言語の機能です。  
  
|機能|アイテム|  
|-------------|----------|  
|軸|**先祖**、**先祖または self**、**子孫**、**子孫または self (//)**、**次**、 **次兄弟**、**名前空間**、**前**、**前兄弟**|  
|数値を使用する述語||  
|算術演算子|mod|  
|ノード関数|**先祖**、**先祖または self**、**子孫**、**子孫または self (//)**、**次**、 **次兄弟**、**名前空間**、**前**、**前兄弟**|  
|文字列関数|**string()**、 **concat()**、 **starts-with()**、 **contains()**、 **substring-before()**、 **substring-after()**、 **substring()**、 **string-length()**、 **normalize()**、 **translate()**|  
|論理関数|**lang()**|  
|数値関数|**sum()**、 **floor()**、 **ceiling()**、 **round()**|  
|union 演算子|&#124;|  
  
 テンプレートに XPath クエリを指定する場合には、次の動作に注意してください。  
  
-   XPath には、XML で特別な意味になる < や & などの文字が含まれることがあります (テンプレートは XML ドキュメントです)。 これらの文字を、XML の & エンコードを使用してエスケープするか、URL に XPath を指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 での XPath クエリの使用](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/using-xpath-queries-in-sqlxml-4-0.md)  
  
  
