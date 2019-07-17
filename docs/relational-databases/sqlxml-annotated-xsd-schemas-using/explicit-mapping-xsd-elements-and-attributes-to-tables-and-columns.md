---
title: テーブルと列に明示的なマッピングの XSD 要素および属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4edb639a56e195bf57d4b34f8c1d399e1218b72f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067117"
---
# <a name="explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns"></a>テーブルおよび列への XSD 要素と属性の明示的なマッピング
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XSD スキーマを使用してリレーショナル データベースの XML ビューを作成するときには、スキーマの要素と属性をデータベースのテーブルと列にマップする必要があります。 データベースのテーブルおよびビューの行は、XML ドキュメントの要素にマップされます。 データベースの列値は属性または要素にマップされます。  
  
 注釈付き XSD スキーマに対して XPath クエリを指定する場合、スキーマ内の要素と属性のデータは、マップ先のテーブルと列から取得されます。 データベースから単一の値を取得するには、XSD スキーマに指定されているマッピングに、リレーションとフィールドの両方の指定が必要です。 要素または属性の名前が、マップ先テーブル/ビューまたは列の名前と同じ名前ではない場合、 **sql:relation**と**sql:field**要素間のマッピングを指定するための注釈またはXML ドキュメントとテーブル (ビュー) またはデータベース内の列の属性です。  
  
## <a name="sql-relation"></a>sql-relation  
 **Sql:relation** XSD スキーマ内の XML ノードをデータベース テーブルにマップする注釈を追加します。 値として、テーブル (ビュー) の名前が指定されて、 **sql:relation**注釈。  
  
 ときに**sql:relation**この注釈のスコープは、すべての属性と書き込みのショートカットを提供するため、その要素の複合型定義で説明されている子要素に適用される、要素に指定されます注釈。  
  
 **Sql:relation**注釈は、識別子がで有効な場合にも役立ちます[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML では無効にします。 たとえば、"Order Details" は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では有効なテーブル名ですが、XML では無効です。 このような場合、 **sql:relation**注釈を使用して、たとえば、マッピングを指定することができます。  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 **Sql フィールド**注釈要素または属性をデータベース列にマップします。 **Sql:field**スキーマ内の XML ノードをデータベース列にマップする注釈を追加します。 指定することはできません**sql:field**で空のコンテンツ要素。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)します。  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. sql:relation 注釈と sql:field 注釈を指定する  
 XSD スキーマから成る、この例では、 **\<連絡先 >** 複合型の要素 **\<FName >** と **\<LName >** 子要素および**ContactID**属性。  
  
 **Sql:relation**注釈のマップ、 **\<連絡先 >** 要素が AdventureWorks データベースの Person.Contact テーブルにします。 **Sql:field**注釈のマップ、  **\<FName >** 要素が FirstName 列に、  **\<LName >** LastName 要素列です。  
  
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
  
2.  次の次のテンプレートをコピーしてテキスト ファイルに貼り付けます。 MySchema-annotated.xml を保存したディレクトリに MySchema-annotatedT.xml として保存します。  
  
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
  
     詳細については、次を参照してください。 [SQLXML クエリの実行に ADO を使用する](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
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
  
  
