---
title: "テーブルと列に明示的なマッピング XSD 要素および属性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a83de0653a25fa2bf055c003a13600a67e37bb9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns"></a>テーブルと列に明示的なマッピング XSD 要素および属性
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]XSD スキーマを使用して、リレーショナル データベースの XML ビューが提供する、要素とスキーマの属性は、データベースのテーブルと列にマップする必要があります。 データベースのテーブルおよびビューの行は、XML ドキュメントの要素にマップされます。 データベースの列値は属性または要素にマップされます。  
  
 注釈付き XSD スキーマに対して XPath クエリを指定する場合、スキーマ内の要素と属性のデータは、マップ先のテーブルと列から取得されます。 データベースから単一の値を取得するには、XSD スキーマに指定されているマッピングに、リレーションとフィールドの両方の指定が必要です。 要素または属性の名前が、マップ先のテーブル/ビューまたは列の名前と同じ名前ではない場合、 **sql:relation**と**sql:field**注釈要素の間のマッピングの指定を使用して、またはXML ドキュメントとテーブル (ビュー) またはデータベース内の列の属性です。  
  
## <a name="sql-relation"></a>sql-relation  
 **Sql:relation** XSD スキーマ内の XML ノードをデータベース テーブルにマップする注釈を追加します。 値として、テーブル (ビュー) の名前が指定されて、 **sql:relation**注釈。  
  
 ときに**sql:relation**が指定されて、要素に、この注釈のスコープは、すべての属性と書き込みにショートカットを提供するため、その要素の複合型の定義に記載されている子要素に適用されます注釈。  
  
 **Sql:relation**注釈は、識別子がで有効な場合にも役立ちます[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は XML では無効です。 たとえば、"Order Details" は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では有効なテーブル名ですが、XML では無効です。 このような場合、 **sql:relation**注釈は、たとえば、マッピングを指定に使用されることができます。  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 **Sql フィールド**注釈によって、要素または属性をデータベース列にマップします。 **Sql:field**注釈がスキーマ内の XML ノードをデータベース列にマップを追加します。 指定することはできません**sql:field**で空のコンテンツ要素。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. sql:relation 注釈と sql:field 注釈を指定する  
 この例では、XSD スキーマで構成されます、 **\<連絡先 >**複合型の要素 **\<FName >**と **\<LName >**子要素、および**ContactID**属性。  
  
 **Sql:relation**注釈マップ、 **\<連絡先 >**要素 AdventureWorks データベースの Person.Contact テーブルにします。 **Sql:field**注釈マップ、  **\<FName >**要素が FirstName 列に、  **\<LName >** LastName 要素列です。  
  
 注釈が指定されていない、 **ContactID**属性。 このため、既定のマッピングが使用され、属性が同じ名前の列にマップされます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 MySchema-annotated.xml として保存します。  
  
2.  以下の次のテンプレートをコピーし、テキスト ファイルに貼り付けます。 MySchema-annotated.xml を保存したディレクトリに MySchema-annotatedT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (MySchema-annotated.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML クエリの実行に使用する ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 次に結果セットの一部を示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
