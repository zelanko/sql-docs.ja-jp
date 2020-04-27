---
title: 'Sql: キーフィールドを使用したキー列の識別 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc3c063da7bb9133f8687a908c4bd7e0e13bae8f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013818"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a>sql:key-fields を使用した、キー列の指定 (SQLXML 4.0)
  XSD スキーマに対して XPath クエリを指定する場合、結果内に適切な入れ子を生成するには、多くの場合キー情報が必要です。 `sql:key-fields` 注釈の指定は、適切な階層を確実に生成するための 1 つの方法です。  
  
> [!NOTE]  
>  適切な入れ子を生成するには、テーブルにマップする要素に `sql:key-fields` を指定することをお勧めします。 作成される XML は、基になる結果セットの順序指定に影響を受けます。 `sql:key-fields` を指定しない場合、適切な XML が作成されない可能性があります。  
  
 `sql:key-fields` の値で、リレーションの行を一意に識別する列を指定します。 行を一意に識別するために複数の列が必要な場合、列の値はスペースで区切られます。  
  
 要素に、要素`sql:key-fields`と子要素の間に定義されている** \<sql: relationship>** が含まれていても、親要素で指定されているテーブルの主キーが提供されていない場合は、注釈を使用する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a>A. Sql: relationship> が\<十分な情報を提供しない場合に適切な入れ子を生成する  
 この例では、`sql:key-fields` をどこに指定すればよいかを示します。  
  
 次のスキーマについて考えてみます。 このスキーマでは、order ** \<>** 要素が親で、 ** \<customer>** 要素が子である、 ** \<order>** と** \<customer>** 要素の間の階層を指定します。  
  
 ** \<Sql: relationship>** タグは、親子のリレーションシップを指定するために使用されます。 このタグでは、Sales.SalesOrderHeader テーブルの CustomerID を親キーとして識別し、Sales.Customer テーブルの子キー CustomerID を参照します。 ** \<Sql: relationship>** で提供される情報は、親テーブル (SalesOrderHeader) 内の行を一意に識別するのに十分ではありません。 `sql:key-fields` 注釈を指定しないと、不正確な階層が生成されます。  
  
 `sql:key-fields` ** \<>順序**で指定した場合、注釈は親 (SalesOrderHeader テーブル) 内の行を一意に識別し、その子要素はその親の下に表示されます。  
  
 スキーマは次のようになります。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>このスキーマの実際のサンプルを作成するには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 KeyFields1.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 KeyFields1.xml を保存したディレクトリに KeyFields1T.xml として保存します。 このテンプレートの XPath クエリでは、CustomerID が3未満のすべての** \<注文>** 要素が返されます。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (KeyFields1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 結果セットの一部を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a>B. sql:key-fields を指定して結果内に適切な入れ子を生成する  
 次のスキーマでは、 ** \<sql: relationship>** を使用して階層が指定されていません。 `sql:key-fields` 注釈を指定して、HumanResources.Employee テーブルの従業員を一意に識別する必要があります。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>このスキーマの実際のサンプルを作成するには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 KeyFields2.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 KeyFields2.xml を保存したディレクトリに KeyFields2T.xml として保存します。 このテンプレートの XPath クエリは、すべての** \<humanresources.employee>** 要素を返します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (KeyFields2.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 結果を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
