---
title: XPath クエリでの関係演算子の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], relational operators
- relational operators [SQLXML]
- XPath operators [SQLXML]
- operators [SQLXML]
ms.assetid: 177a0eb2-11ef-4459-a317-485a433ee769
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 180962ac5afae577625415d94cb9beda65f9537a
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909439"
---
# <a name="specifying-relational-operators-in-xpath-queries-sqlxml-40"></a>XPath クエリ内での関係演算子の指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  以下の例では、XPath クエリに関係演算子を指定する方法を示します。 これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。 このサンプルスキーマの詳細については、「 [XPath サンプルの注釈&#40;付き XSD&#41;スキーマの例 SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-specify-relational-operator"></a>A. 関係演算子を指定する  
 この XPath クエリは **\<Customer >** 要素の子要素を返します。この要素の**CustomerID**属性値は "1" で、子 **\<Order >** 要素には **\<orderdetail >** 子が含まれています。次のように、値が3より大きい**OrderQty**属性を使用します。  
  
```  
/child::Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
 角かっこで指定された述語は、 **\<Customer >** 要素をフィルター処理します。 OrderQty 属性値が3を超える **\<OrderDetail >** 孫が1つ以上含まれている **\<Customer >** 要素のみが返されます。  
  
 **子**軸が既定値です。 そのため、クエリは次のように指定できます。  
  
```  
/Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  [サンプルスキーマコード](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
2.  次のテンプレート (SpecifyRelationalA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  

     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 このテンプレートを実行した場合の結果セットは次のとおりです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-760" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-766" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-757" UnitPrice="1049.7528" OrderQty="4" UnitPriceDiscount="0" />   
</ROOT>  
```  
  
### <a name="b-specify-relational-operator-in-the-xpath-query-and-use-boolean-function-to-compare-the-result"></a>b. XPath クエリに関係演算子を指定し、論理関数を使用して結果を比較する  
 このクエリでは、 **SalesPersonID**属性値が270未満であるコンテキストノードの子要素 > すべての **\<の順序**が返されます。  
  
```  
/child::Customer/child::Order[(attribute::SalesPersonID < 270)=true()]  
```  
  
 **属性**軸 (@) へのショートカットを指定できます。また、**子**軸が既定値であるため、クエリから省略できます。  
  
```  
/Customer/Order[(@SalesPersonID < 270)=true()]  
```  
  
> [!NOTE]  
>  このクエリがテンプレートで指定されている場合、< 文字は XML ドキュメント内で特別な意味を持つため、< 文字はエンティティエンコードされている必要があります。 テンプレートでは、`<` を使用して < 文字を指定します。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  [サンプルスキーマコード](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
2.  次のテンプレート (SpecifyRelationalB.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="SampleSchema1.xml">  
            /Customer/Order[(@SalesPersonID<270)=true()]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 テンプレートを実行して得られる結果セットの一部を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-46613" SalesPersonID="268"   
         OrderDate="2002-07-01T00:00:00"   
         DueDate="2002-07-13T00:00:00"   
         ShipDate="2002-07-08T00:00:00">  
    <OrderDetail ProductID="Prod-739" UnitPrice="917.9363"   
                 OrderQty="2" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-779" UnitPrice="1491.4221"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-825" UnitPrice="242.1391"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  <Order SalesOrderID="Ord-71919" SalesPersonID="268"  
         OrderDate="2004-06-01T00:00:00"   
         DueDate="2004-06-13T00:00:00"   
         ShipDate="2004-06-08T00:00:00">  
    <OrderDetail ProductID="Prod-961" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-965" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-966" UnitPrice="1716.5304"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  ...  
</ROOT>  
```  
  
  
