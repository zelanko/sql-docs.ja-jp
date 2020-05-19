---
title: テーブルおよび列への XSD 要素と属性の明示的なマッピング (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 11144714addb50dc4c481512399228802390f2f3
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703612"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a>テーブルおよび列への XSD 要素および属性の明示的なマッピング (SQLXML 4.0)
  XSD スキーマを使用してリレーショナル データベースの XML ビューを作成するときには、スキーマの要素と属性をデータベースのテーブルと列にマップする必要があります。 データベースのテーブルおよびビューの行は、XML ドキュメントの要素にマップされます。 データベースの列値は属性または要素にマップされます。  
  
 注釈付き XSD スキーマに対して XPath クエリを指定する場合、スキーマ内の要素と属性のデータは、マップ先のテーブルと列から取得されます。 データベースから単一の値を取得するには、XSD スキーマに指定されているマッピングに、リレーションとフィールドの両方の指定が必要です。 要素または属性の名前が、マップ先のテーブル、ビューまたは列名と同じでない場合は、`sql:relation` 注釈と `sql:field` 注釈を使用して、XML ドキュメントの要素または属性から、データベースのテーブル、ビューまたは列へのマッピングを指定します。  
  
## <a name="sql-relation"></a>sql-relation  
 XSD スキーマ内の XML ノードをデータベース テーブルにマップするには、`sql:relation` 注釈を追加します。 ここではテーブルまたはビューの名前を `sql:relation` 注釈の値として指定します。  
  
 `sql:relation` を要素に指定した場合は、この注釈のスコープが、要素の複合型定義で指定されているすべての属性と子要素に適用されます。これによって、注釈の記述を簡素化できます。  
  
 注釈は、 `sql:relation` で有効な識別子 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が XML で有効でない場合にも便利です。 たとえば、"Order Details" は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では有効なテーブル名ですが、XML では無効です。 この場合、`sql:relation` 注釈を使用して、次のようなマッピングを指定できます。  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 `sql-field` 注釈では、要素または属性がデータベース列にマップされます。 スキーマ内の XML ノードをデータベース列にマップするには、`sql:field` 注釈を追加します。 空のコンテンツ要素に `sql:field` は指定できません。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. sql:relation 注釈と sql:field 注釈を指定する  
 この例では、XSD スキーマは、 ** \< FName>** と** \< LName>** 子要素および**ContactID**属性を持つ複合型の** \< Contact>** 要素で構成されています。  
  
 この `sql:relation` 注釈によっ** \< て、contact>** 要素が AdventureWorks データベースの Person. contact テーブルにマップされます。 注釈は、 `sql:field` ** \< FName>** 要素を FirstName 列に、 ** \< LName>** 要素を LastName 列にマップします。  
  
 **ContactID**属性に注釈が指定されていません。 このため、既定のマッピングが使用され、属性が同じ名前の列にマップされます。  
  
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
  
2.  次のテンプレートをコピーし、テキストファイルに貼り付けます。 MySchema-annotated.xml を保存したディレクトリに MySchema-annotatedT.xml として保存します。  
  
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
  
     詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
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
  
  
