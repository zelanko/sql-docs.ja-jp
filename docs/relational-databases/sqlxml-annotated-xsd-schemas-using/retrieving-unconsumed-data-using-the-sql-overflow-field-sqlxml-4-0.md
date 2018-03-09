---
title: "未使用データを使用して、sql:overflow の取得のフィールド (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e1801fcd260dd674489a851361044ff6c9110c63
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a>sql:overflow-field を使用した、未使用データの取得 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
[!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML 関数を使用して XML ドキュメントからデータベースにレコードを挿入するときに、ソース XML ドキュメントのすべての未使用データを 1 つの列に格納することができます。 注釈付きスキーマを使用して、データベースからデータを取得するときに指定できます、 **sql:overflow-フィールド**オーバーフロー データが格納されているテーブル内の列を識別する属性。 **Sql:overflow-フィールド**に属性を指定できます**\<要素 >**です。  
  
 データは次のように取得されます。  
  
-   オーバーフロー列に格納されている属性を含む要素に追加されます、 **sql:overflow-フィールド**注釈。  
  
-   データベースのオーバーフロー列に格納された子要素とその子孫が、スキーマで明示的に指定されたコンテンツの後に子要素として追加されます。 このとき、順序は維持されません。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a>A. 要素に sql:overflow-field を指定する  
 この例では、次のスクリプトを実行して tempdb データベースにテーブル Customers2 が作成済みであることを前提としています。  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 さらに、tempdb データベース用の仮想ディレクトリを作成する必要があります: およびのテンプレート仮想名**テンプレート**"template"という名前の型。  
  
 次の例では、マッピング スキーマで、Customers2 テーブルの AddressOverflow 列に格納されている未使用データを取得します。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 Overflow.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 Overflow.xml を保存したディレクトリに OverflowT.xml として保存します。 このテンプレートのクエリでは、Customers2 テーブル内のレコードが選択されます。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (Overflow.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 Here is the result set:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
