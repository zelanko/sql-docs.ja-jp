---
title: Target Namespace を使用して、targetNamespace 属性 (SQLXML 4.0) を指定する |Microsoft ドキュメント
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
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 92bb667c5189d24207207d19c2779b070cbc2cea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178401"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>targetNamespace 属性を使用した、対象名前空間の指定 (SQLXML 4.0)
  XSD スキーマを作成するには、XSD を使用することができます**targetNamespace**属性をターゲットの名前空間を指定します。 このトピックについて説明する方法、XSD **targetNamespace**、 **elementFormDefault**と**attributeFormDefault**は XML インスタンスに影響する属性の機能生成されると、名前空間を持つ XPath クエリを指定する方法とします。  
  
 使用することができます、 **xsd:targetNamespace**属性を要素と属性を既定の名前空間から別の名前空間に配置します。 また、スキーマでローカルに宣言された要素と属性を、名前空間で修飾して表示するかどうかも指定できます。名前空間は、プレフィックスを使って明示的に、または既定により暗黙的に指定できます。 使用することができます、 **elementFormDefault**と**attributeFormDefault**属性を **\<xsd:schema >** をグローバルに指定する要素のローカルの要素や属性の修飾に使用できる、**フォーム**個々 の要素と属性を個別に指定する属性。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-specifying-a-target-namespace"></a>A. 対象名前空間を指定する  
 次の XSD スキーマを使用して、対象名前空間を指定する、 **xsd:targetNamespace**属性。 また、スキーマ、設定、 **elementFormDefault**と**attributeFormDefault**属性の値 **"unqualified"** (これらの属性の既定値)。 これは、グローバル宣言であり、すべてのローカル要素に影響を与えます (**\<順序 >** スキーマ内) と属性 (**CustomerID**、 **ContactName**、および**OrderID**スキーマで)。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 このスキーマの内容は次のとおりです。  
  
-   **CustomerType**と**OrderType**型の宣言はグローバルであり、したがって、スキーマのターゲットの名前空間に含まれています。 宣言でこれらの型が参照されているときにその結果、 **\<顧客 >** 要素とその**\<順序 >** 子要素、関連付けられているプレフィックスが指定されてターゲット名前空間。  
  
-   **\<顧客 >** スキーマ内のグローバル要素になっているため、スキーマのターゲット名前空間に要素が含まれるもします。  
  
 このスキーマに対して次の XPath クエリを実行します。  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 この XPath クエリでは、次のインスタンス ドキュメントが生成されます。ここでは注文の一部のみを表示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 このインスタンス ドキュメントでは、urn: MyNamespace 名前空間を定義し、(y0) プレフィックスを付けることを関連付けます。 このプレフィックスにのみ適用、 **\<顧客 >** グローバル要素。 (の子として宣言されているために、要素がグローバル **\<xsd:schema >** スキーマ内の要素です)。  
  
 ローカルの要素と属性には、ため、プレフィックスは適用されませんの値**elementFormDefault**と**attributeFormDefault**属性に設定されている **"unqualified"** スキーマです。 なお、 **\<順序 >** の子としてその宣言が表示されるため、要素はローカル、  **\<complexType >** を定義する要素、  **\<CustomerType >** 要素。 同様に、属性 (**CustomerID**、 **OrderID**、および**ContactName**) は、ローカル、グローバルされません。  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>このスキーマの実際のサンプルを作成するには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 targetNameSpace.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 targetNamespace.xml を保存したディレクトリに targetNameSpaceT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     テンプレートの XPath クエリを返します、 **\<顧客 >** customerid が 1 の顧客の要素。 この XPath クエリでは、属性ではなく、クエリ内の要素の名前空間プレフィックスが指定されることに注意してください。 ローカル属性は、スキーマ内の指定と同様、修飾されません。  
  
     マッピング スキーマ (targetNamespace.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML クエリの実行に使用する ADO](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 スキーマを指定する場合**elementFormDefault**と**attributeFormDefault**値を持つ属性 **"qualified"**、すべてのローカル インスタンス ドキュメントには要素および属性を修飾します。 これらの属性を含めるには、前のスキーマを変更することができます、  **\<xsd:schema >** 要素とテンプレートをもう一度実行します。 この場合は、インスタンスで属性も修飾されるので、名前空間プレフィックスを含むよう XPath クエリを変更します。  
  
 次は変更した XPath クエリです。  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 次は返される XML ドキュメントです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  