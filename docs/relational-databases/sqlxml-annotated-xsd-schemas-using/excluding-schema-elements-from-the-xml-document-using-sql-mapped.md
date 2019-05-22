---
title: 'Sql を使用して XML ドキュメントからスキーマ要素の除外: マップ |Microsoft Docs'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: MightyPen
ms.author: genemi
ms.reviewer: ''
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2962c4a15fa39827566accef7442b87c24bbf16c
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980943"
---
# <a name="excluding-schema-elements-from-the-xml-document-using-sqlmapped"></a>sql:mapped を使用した XML ドキュメントからのスキーマ要素の除外
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  既定のマッピングでは、XSD スキーマのすべての要素と属性が、データベースのテーブルまたはビューと列にマップされます。 XSD スキーマをデータベース テーブル (ビュー) または列にマップされないと、XML で表示しない要素を作成するかどうかを指定できます、 **sql: マップ**注釈。  
  
 **Sql: マップ**注釈は、スキーマを変更することはできません、またはその他のソースし、まだデータベースに格納されていないデータが含まれていますから XML を検証するスキーマを使用する場合に特に便利です。 **Sql: マップ**注釈とは異なります**sql: は定数**ことで、XML ドキュメントにマップされない要素と属性が表示されません。  
  
 **Sql: マップ**注釈はブール値 (0 = false、1 = true)。 指定できる値は 0、1、true、false です。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)します。  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. sql:mapped 注釈を指定する  
 他のソースからの XSD スキーマがあるとします。 この XSD スキーマから成る、  **\<Person.Contact >** を持つ要素**ContactID**、 **FirstName**、 **LastName**と**HomeAddress**属性。  
  
 この XSD スキーマを AdventureWorks データベースの Person.Contact テーブルにマッピング**sql: マップ**が指定されて、 **HomeAddress** Employees テーブルは、ホームを格納していないため、属性従業員の住所。 この結果、マッピング スキーマに対して Xpath クエリを指定すると、属性はデータベースにマップされず、結果の XML ドキュメント内に返されません。  
  
 スキーマの残りの部分に対しては、既定のマッピングが適用されます。 **\<Person.Contact >** 要素は Person.Contact テーブルにマップされ、すべての属性は Person.Contact テーブル内の同じ名前の列にマップします。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 sql-mapped.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 sql-mapped.xml を保存したディレクトリに sql-mappedT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (MySchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML クエリの実行に ADO を使用する](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
 これは、結果セットです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 ContactID、FirstName、LastName は存在するが、HomeAddress はマッピング スキーマの場合は 0 を指定するためではなく、 **sql: マップ**属性。  
  
## <a name="see-also"></a>参照  
 [XSD 要素および属性からテーブルと列の既定のマッピング&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
