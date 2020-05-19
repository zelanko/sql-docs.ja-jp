---
title: クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 50c6ff5327c8ee243cb6ba788d5c52f815b4aa2d
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702907"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0)
  注釈付きスキーマに対してクエリを指定し、XSD スキーマに対してテンプレートで XPath クエリを指定して、データベースからデータを取得することができます。  
  
 ** \< Sql: xpath クエリ>** 要素を使用すると、注釈付きスキーマで定義されている XML ビューに対して xpath クエリを指定できます。 XPath クエリの実行対象となる注釈付きスキーマは、 `mapping-schema` ** \< sql: xpath クエリ>** 要素の属性を使用して識別されます。  
  
 テンプレートは、1 つ以上のクエリを含む有効な XML ドキュメントです。 FOR XML クエリと XPath クエリでは、ドキュメント フラグメントが返されますが、 テンプレートは、ドキュメントフラグメントのコンテナーとして機能します。そのため、1つの最上位要素を指定する方法が用意されています。  
  
 このトピックの例では、テンプレートを使用して注釈付きスキーマに対する XPath クエリを指定し、データベースからデータを取得します。  
  
 たとえば、次の注釈付きスキーマを考えてみます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 わかりやすくするため、この XSD スキーマは Schema2.xml というファイルに格納されているものとします。 ここで、次のテンプレート ファイル (Schema2T.xml) で指定されている注釈付きスキーマに対し、XPath クエリを指定できます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 SQLXML 4.0 のテスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用すると、テンプレート ファイルの一部としてクエリを実行できます。 詳細については、「 [SQLXML 4.0&#41;で非推奨とされた注釈付き XDR スキーマ &#40;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)」を参照してください。  
  
## <a name="using-inline-mapping-schemas"></a>インライン マッピング スキーマの使用  
 注釈付きスキーマはテンプレートに直接含めることができます。このテンプレートで、インライン スキーマに対する XPath クエリを指定できます。 テンプレートはアップデートグラムとしても使用できます。  
  
 テンプレートには複数のインライン スキーマを含めることができます。 テンプレートに含まれているインラインスキーマを使用するには、 ** \< xsd: schema>** 要素で一意の値を持つ**id**属性を指定し、 **#idvalue**を使用してインラインスキーマを参照します。 **Id**属性は、XDR スキーマで使用される**sql: id** ({urn: schema-microsoft-com: xml} id) と同じ動作です。  
  
 たとえば、次のテンプレートでは、2 つのインライン注釈付きスキーマを指定しています。  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 このテンプレートでは 2 つの XPath クエリも指定しています。 ** \< Xpath クエリ>** の各要素は、属性を指定することによって、マッピングスキーマを一意に識別し `mapping-schema` ます。  
  
 テンプレートでインラインスキーマを指定する場合は、 `sql:is-mapping-schema` ** \< xsd: schema>** 要素で注釈も指定する必要があります。 `sql:is-mapping-schema` はブール値 (0 = false、1=true) をとります。 **Sql:-mapping-schema = "1"** のインラインスキーマは、インライン注釈が付けられたスキーマとして扱われ、XML ドキュメントでは返されません。  
  
 `sql:is-mapping-schema` 注釈は、テンプレートの名前空間 `urn:schemas-microsoft-com:xml-sql` に属しています。  
  
 この例をテストするには、テンプレート (InlineSchemaTemplate.xml) をローカルのディレクトリに保存した後、SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。 詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 `mapping-schema`テンプレート (xpath クエリがある場合) または** \< updg: sync>** 要素で** \<>** 属性を指定することに加えて、次の操作を行うことができます (xpath クエリが存在する場合)。  
  
-   テンプレートの `mapping-schema` ** \< ルート>** 要素 (グローバル宣言) で属性を指定します。 ここで指定したマッピング スキーマは、すべての XPath およびアップデートグラム ノードで、明示的に `mapping-schema` 注釈が指定されていない場合に既定のスキーマとして使用されます。  
  
-   `mapping schema`ADO オブジェクトを使用して属性を指定し `Command` ます。  
  
 `mapping-schema` ** \< Xpath クエリ>** または** \< updg: sync>** 要素で指定されている属性の優先順位は最も高くなります。 ADO `Command` オブジェクトの優先順位は最も低くなります。  
  
 テンプレートで XPath クエリを指定し、XPath クエリの実行対象となるマッピングスキーマを指定しない場合、XPath クエリは**dbobject**型クエリとして扱われることに注意してください。 たとえば、次のテンプレートを考えてみます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 このテンプレートでは、XPath クエリが指定されていますが、マッピング スキーマが指定されていません。 したがって、このクエリは**dbobject**型クエリとして扱われます。 productphoto はテーブル名、 @ProductPhotoID = ' 100 ' は、ID 値が100の製品写真を検索する述語です。 @LargePhoto値の取得元の列を指定します。  
  
  
