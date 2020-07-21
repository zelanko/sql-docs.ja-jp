---
title: 'Sql を使用した定数要素の作成: 定数 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a0b31c68f7ebbb956c2d539dee4bc4dca2eb5ce
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060124"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>sql:is-constant を使用した、定数要素の作成 (SQLXML 4.0)
  定数要素 (つまり、データベーステーブルまたは列にマップされない XSD スキーマの要素) を指定するには、注釈を使用し `sql:is-constant` ます。 この注釈はブール値 (0 = false、1 = true) をとります。 指定できる値は 0、1、true、false です。 `sql:is-constant` 注釈は、属性のない要素に指定できます。 この注釈を値 true (または 1) と共に要素に指定した場合、その要素は XML ドキュメント内に表示されますが、データベースにはマップされなくなります。  
  
 `sql:is-constant` 注釈は次の目的に使用できます。  
  
-   最上位要素を XML ドキュメントに追加する。 XML では、ドキュメントに 1 つの最上位要素 (ルート要素) が必要です。  
  
-   **\<Orders>** すべての注文をラップする要素などのコンテナー要素を作成する。  
  
 `sql:is-constant`注釈は要素に追加でき **\<complexType>** ます。  
  
## <a name="examples"></a>例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. sql:is-constant を指定してコンテナー要素を追加する  
 この注釈付き XSD スキーマで **\<CustomerOrders>** は、値が1の属性を指定することによって、が定数要素として定義され `sql:is-constant` ます。 したがって、 **\<CustomerOrders>** は、どのデータベーステーブルまたは列にもマップされません。 この定数要素は、子要素で構成さ **\<Order>** れます。  
  
 **\<CustomerOrders>** はどのデータベーステーブルまたは列にもマップされませんが、結果の XML には子要素を含むコンテナー要素として表示され **\<Order>** ます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 isConstant.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 isConstant.xml を保存したディレクトリに isConstantT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (isConstant.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 結果セットの一部を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
