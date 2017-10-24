---
title: "パス式のステップで述語の指定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- predicates [XQuery]
- qualifiers [XQuery]
- path expressions [XQuery]
ms.assetid: 2660ceca-b8b4-4a1f-98a0-719ad5f89f81
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a5b417b2bfe5d995657ad86cf44b650b751f6a30
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="path-expressions---specifying-predicates"></a>パス式で述語の指定
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  」の説明に従って[XQuery パス式](../xquery/path-expressions-xquery.md)パス式での軸ステップには、次のコンポーネントが含まれています。  
  
-   [軸](../xquery/path-expressions-specifying-axis.md)です。  
  
-   ノード テスト。 詳細については、次を参照してください。[パス式のステップでノードのテストを指定する](../xquery/path-expressions-specifying-node-test.md)です。  
  
-   0 個以上の述語。 これは省略可能です。  
  
 省略可能な述語は、パス式の軸ステップの 3 番目の要素です。  
  
## <a name="predicates"></a>述語  
 述語は、指定されたテストを適用して、ノード シーケンスをフィルター処理するために使用されます。 述語式は、角かっこで囲み、パス式の最後のノードにバインドされます。  
  
 たとえば、あると想定の SQL パラメーター値 (x)、 **xml**データ型が宣言されている、次に示すようにします。  
  
```  
declare @x xml  
set @x = '  
<People>  
  <Person>  
    <Name>John</Name>  
    <Age>24</Age>  
  </Person>  
  <Person>  
    <Name>Goofy</Name>  
    <Age>54</Age>  
  </Person>  
  <Person>  
    <Name>Daffy</Name>  
    <Age>30</Age>  
  </Person>  
</People>  
'  
```  
  
 この場合、次の式は、述語の値 [1] が 3 つの異なるノード レベルで使用されていますが、いずれも有効です。  
  
```  
select @x.query('/People/Person/Name[1]')  
select @x.query('/People/Person[1]/Name')  
select @x.query('/People[1]/Person/Name')  
```  
  
 どの式でも、述語は適用対象のパス式のノードにバインドされていることに注意してください。 たとえば、最初のパス式が 1 つ目を選択 <`Name`> 要素内での各///people/person ノードと、提供された XML インスタンスは、次を返します。  
  
```  
<Name>John</Name><Name>Goofy</Name><Name>Daffy</Name>  
```  
  
 ただし、2 番目のパス式は、最初の /People/Person ノードの下にあるすべての <`Name`> 要素を選択します。 したがって、次の結果を返します。  
  
```  
<Name>John</Name>  
```  
  
 また、かっこを使用して、述語の評価の順序を変えることもできます。 たとえば、次の式では、述語 [1] と (/People/Person/Name) というパスを分離するために、かっこが使用されています。  
  
```  
select @x.query('(/People/Person/Name)[1]')  
```  
  
 この例では、述語が適用される順序が変わります。 これで、かっこで囲まれたパス (/People/Person/Name) が最初に評価された後に、このパスに一致するすべてのノードを含むセットに述語操作 [1] が適用されます。 かっこでは、操作の順序がなければ異なるととして [1] が適用される点で、`child::Name`ノード テストは、最初のパス式の例に似ています。  
  
### <a name="quantifiers-and-predicates"></a>量化子と述語  
 量化子は、述語自体の角かっこ内で、複数回使用および追加できます。 たとえば、前の例を使用すると、次の式は複雑な述語のサブ式内で複数の量化子を使用する有効な式です。  
  
```  
select @x.query('/People/Person[contains(Name[1], "J") and xs:integer(Age[1]) < 40]/Name/text()')  
```  
  
 述語式の結果は、ブール値に変換され、述語の真偽値として参照されます。 述語の真偽値が True であるシーケンスのノードのみが、結果として返されます。 それ以外のすべてのノードは破棄されます。  
  
 たとえば、次のパス式では、2 番目のステップに述語があります。  
  
```  
/child::root/child::Location[attribute::LocationID=10]  
```  
  
 この述語で指定される条件は、すべての <`Location`> 要素ノードの子に適用されます。 結果として、LocationID 属性値が 10 であるワーク センターの場所のみが返されます。  
  
 上記のパス式は、次の SELECT ステートメント内で実行されます。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
 /child::AWMI:root/child::AWMI:Location[attribute::LocationID=10]  
')  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
### <a name="computing-predicate-truth-values"></a>述語の真偽値の計算  
 述語の真偽値の判定には、XQuery の仕様に従い、次の規則が適用されます。  
  
1.  述語式の値が空のシーケンスの場合、述語の真偽値は False になります。  
  
     例:  
  
    ```  
    SELECT Instructions.query('  
    declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     /child::AWMI:root/child::AWMI:Location[attribute::LotSize]  
    ')  
    FROM Production.ProductModel  
    WHERE ProductModelID=7  
    ```  
  
     この式のパス式は、LotSize 属性が指定されている <`Location`> 要素ノードのみを返します。 述語が、特定の空のシーケンスを返すかどうかは <`Location`>、ワーク センターの場所が結果に返されません。  
  
2.  値のみできます xs:integer、xs:Boolean、またはノードの述語\*です。 ノードの\*述語を任意のノードがある場合は True および False 空のシーケンスを評価します。 double 型や float 型など、他の数値型では、静的な型指定エラーが生成されます。 式の述語の真偽値は、結果の整数がコンテキストの位置の値と同じ場合にのみ、True になります。 唯一の整数リテラル値も、および**last()**関数が 1 にフィルター処理されたステップ式の基数を減らします。  
  
     たとえば、次のクエリは、3 番目の子要素ノードを取得します。、<`Features`> 要素。  
  
    ```  
    SELECT CatalogDescription.query('  
    declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /child::PD:ProductDescription/child::PD:Features/child::*[3]  
    ')  
    FROM Production.ProductModel  
    WHERE ProductModelID=19  
    ```  
  
     上のクエリに関して、次の点に注意してください。  
  
    -   式の 3 番目のステップは、値が 3 である述語式を指定しています。 したがって、この式の述語の真偽値は、コンテキストの位置が 3 であるノードに対してのみ True になります。  
  
    -   3 番目のステップには、ノード テストのすべてのノードを意味するワイルドカード文字 (*) も指定されています。 ただし、述語により、ノードがフィルター処理され、3 番目の位置にあるノードのみが返されます。  
  
    -   このクエリは、ドキュメント ルートの <`ProductDescription`> 子要素の <`Features`> 子要素ノードの 3 番目の子要素ノードを返します。  
  
3.  述語式の値が Boolean 型の単純なデータ型値である場合、述語の真偽値は、述語式の値と同じになります。  
  
     に対して、次のクエリを指定するなど、 **xml**という XML インスタンスを顧客調査 XML インスタンスを保持する型の変数です。 このクエリは、子供がいる顧客を取得します。 このクエリでが\<HasChildren > 1\</HasChildren >。  
  
    ```  
    declare @x xml  
    set @x='  
    <Survey>  
      <Customer CustomerID="1" >  
      <Age>27</Age>  
      <Income>20000</Income>  
      <HasChildren>1</HasChildren>  
      </Customer>  
      <Customer CustomerID="2" >  
      <Age>27</Age>  
      <Income>20000</Income>  
      <HasChildren>0</HasChildren>  
      </Customer>  
    </Survey>  
    '  
    declare @y xml  
    set @y = @x.query('  
      for $c in /child::Survey/child::Customer[( child::HasChildren[1] cast as xs:boolean ? )]  
      return   
          <CustomerWithChildren>  
              { $c/attribute::CustomerID }  
          </CustomerWithChildren>  
    ')  
    select @y  
    ```  
  
     上のクエリに関して、次の点に注意してください。  
  
    -   内の式、**の**ループに 2 つの手順と、2 番目の手順は、述語を指定します。 この述語の値は、Boolean 型の値です。 この値が True の場合は、述語の真偽値も True になります。  
  
    -   クエリを返します、<`Customer`> が述語の値が True の場合、子要素の\<Survey > ドキュメント ルートの子要素です。 結果を次に示します。  
  
        ```  
        <CustomerWithChildren CustomerID="1"/>   
        ```  
  
4.  述語式の値が少なくとも 1 つのノードを含むシーケンスの場合、述語の真偽値は True になります。  
  
 たとえば、次のクエリは XML カタログの説明には、少なくとも 1 つの機能子要素にはが含まれています製品モデルの ProductModelID を取得、<`Features`> に関連付けられている名前空間からの要素、 **wm**プレフィックス。  
  
```  
SELECT ProductModelID  
FROM   Production.ProductModel  
WHERE CatalogDescription.exist('  
             declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
             declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
             /child::PD:ProductDescription/child::PD:Features[wm:*]  
             ') = 1  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   WHERE 句を指定します、 [exist() メソッド (XML データ型)](../t-sql/xml/exist-method-xml-data-type.md)です。  
  
-   内のパス式、 **exist()**メソッドは、2 番目のステップで述語を指定します。 述語式が少なくとも 1 つの機能のシーケンスを返す場合、この述語式の真偽値は True になります。 この場合、ため、 **exist()**メソッドが True を返す、ProductModelID が返されます。  
  
## <a name="static-typing-and-predicate-filters"></a>静的な型指定フィルターおよび述語フィルター  
 述語は、静的に推定される式の型にも影響する場合があります。 整数リテラル値、および**last()**関数は、多くても 1 つのフィルター処理されたステップ式の基数を減らします。  
  
  

