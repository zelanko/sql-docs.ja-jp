---
title: ロケーションパスの指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 795e27c020c9ea4c80c858da734ebd315d56615c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012657"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>ロケーション パスの指定 (SQLXML 4.0)
  XPath クエリは式の形式で指定され、 式の種類にはさまざまなものがあります。 ロケーション パスは、コンテキスト ノードに相対的なノードのセットを選択する式です。 ロケーション パスを評価すると、結果はノード セットになります。  
  
## <a name="types-of-location-paths"></a>ロケーション パスの種類  
 ロケーション パスは、次のいずれかの形式で指定できます。  
  
-   **絶対ロケーション パス**  
  
     絶対ロケーション パスは、ドキュメントのルート ノードから開始します。 構成要素はスラッシュ記号 (/) で、その後に相対ロケーション パスを続けることもできます。 スラッシュ記号 (/) によって、ドキュメントのルート ノードが選択されます。  
  
-   **相対ロケーション パス**  
  
     相対ロケーション パスは、ドキュメントのコンテキスト ノードから開始します。 構成要素は連続する 1 つ以上のロケーション ステップで、区切りにはスラッシュ記号 (/) を使用します。 各ステップで、コンテキスト ノードに対して相対的なノードのセットが選択されます。 最初のステップでは、コンテキスト ノードに対して相対的なノードのセットが選択され、 そのセットの各ノードが次のステップのコンテキスト ノードとして使用されます。 そのステップで指定されたノードのセットは結合されます。 たとえば、 **child:: order/child:: orderdetail**は、コンテキストノードの子要素** \<>order** ** \<detail>** 子要素を選択します。  
  
    > [!NOTE]  
    >  SQLXML 4.0 における XPath の実装では、XPath が明示的に絶対として指定されていない場合でも、各 XPath クエリはルート コンテキストから開始します。 たとえば、"Customer" で開始する XPath クエリは "/Customer" として扱われます。 XPath クエリの**customer [Order]** では、顧客はルートコンテキストから開始しますが、注文は顧客のコンテキストで開始されます。 詳細については、「 [XPath クエリの使用の概要 &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md)」を参照してください。  
  
## <a name="location-steps"></a>ロケーション ステップ  
 ロケーション パス (絶対または相対) は、次の 3 つの部分から成るロケーション ステップで構成されます。  
  
-   **軸**  
  
     軸によって、ロケーション ステップで選択されるノードと、コンテキスト ノードの間のツリー リレーションシップが指定されます。 サポートされる軸は、`parent`、`child`、`attribute`、および `self` 軸です。 ロケーション パスに `child` 軸を指定した場合、クエリで選択されるすべてのノードはコンテキスト ノードの子です。 
  `parent` 軸を指定した場合、選択されるノードはコンテキスト ノードの親ノードです。 
  `attribute` 軸を指定した場合、選択されるノードはコンテキスト ノードの属性です。  
  
-   **ノードテスト**  
  
     ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。 すべての軸 (`child`、`parent`、`attribute`、および `self`) には主ノード型があります。 `attribute`軸の場合、主ノード型は** \<属性>** です。 `parent`、 `child`、および`self`軸の場合、主ノード型は** \<要素>** です。  
  
     たとえば、ロケーションパスで**child:: customer**を指定すると、コンテキストノードの** \<customer>** 要素が選択されます。 軸に`child`は主ノード型として** \<>要素**があるため、customer が** \<要素>** ノードである場合、ノードテスト customer は TRUE になります。  
  
-   **選択述語 (0 以上)**  
  
     述語では、軸に関してノード セットをフィルター選択します。 XPath 式内に選択述語を指定するときには、SELECT ステートメント内に WHERE 句を指定するときのように、 述語はかっこで囲みます。 選択述語に指定したテストを適用すると、そのノード テストによって返されたノードがフィルター選択されます。 フィルター選択されたノード セットの各ノードに対し、ノードをコンテキスト ノード、ノード セット内のノード数をコンテキストのサイズとして、述語式が評価されます。 述語式が TRUE と評価された場合、そのノードは結果のノード セットに含められます。  
  
     ロケーション ステップの構文では、軸名とノード テストを 2 つのコロン (::) で区切り、その後に式をそれぞれ角かっこで囲んで指定します。式は指定しなくてもかまいません。 たとえば、XPath 式 (ロケーションパス) に**child:: customer@CustomerID[= ' ALFKI ']** を指定すると、コンテキストノードのすべての** \<Customer>** 子要素が選択されます。 次に、述語内のテストがノードセットに適用されます。これにより、 **CustomerID**属性の属性値が ' ALFKI ' の** \<顧客>** 要素ノードのみが返されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [&#40;SQLXML 4.0&#41;の軸の指定](specifying-an-axis-sqlxml-4-0.md)  
 軸を指定する例を示します。  
  
 [Location パスでのノードテストの指定 &#40;SQLXML 4.0&#41;](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 ノード テストを指定する例を示します。  
  
 [Location パスでの選択述語の指定 &#40;SQLXML 4.0&#41;](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 選択述語を指定する例を示します。  
  
  
