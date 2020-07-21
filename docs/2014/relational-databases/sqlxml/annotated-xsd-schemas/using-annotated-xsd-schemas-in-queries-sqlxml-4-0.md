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
ms.openlocfilehash: caee73995b56e248a91872117a51e809c6eea976
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065678"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0)
  注釈付きスキーマに対してクエリを指定し、XSD スキーマに対してテンプレートで XPath クエリを指定して、データベースからデータを取得することができます。  
  
 **\<sql:xpath-query>** 要素を使用すると、注釈付きスキーマで定義されている XML ビューに対して XPath クエリを指定できます。 XPath クエリの実行対象となる注釈付きスキーマは、要素の属性を使用して識別され `mapping-schema` **\<sql:xpath-query>** ます。  
  
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
  
 テンプレートには複数のインライン スキーマを含めることができます。 テンプレートに含まれているインラインスキーマを使用するには、要素に一意の値を指定して**id**属性を指定 **\<xsd:schema>** し、 **#idvalue**を使用してインラインスキーマを参照します。 **Id**属性は、XDR スキーマで使用される**sql: id** ({urn: schema-microsoft-com: xml} id) と同じ動作です。  
  
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
  
 このテンプレートでは 2 つの XPath クエリも指定しています。 各要素は、 **\<xpath-query>** 属性を指定することによって、マッピングスキーマを一意に識別し `mapping-schema` ます。  
  
 テンプレートでインラインスキーマを指定する場合は、 `sql:is-mapping-schema` 要素で注釈も指定する必要があり **\<xsd:schema>** ます。 `sql:is-mapping-schema` はブール値 (0 = false、1=true) をとります。 **Sql:-mapping-schema = "1"** のインラインスキーマは、インライン注釈が付けられたスキーマとして扱われ、XML ドキュメントでは返されません。  
  
 `sql:is-mapping-schema` 注釈は、テンプレートの名前空間 `urn:schemas-microsoft-com:xml-sql` に属しています。  
  
 この例をテストするには、テンプレート (InlineSchemaTemplate.xml) をローカルのディレクトリに保存した後、SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。 詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 `mapping-schema` **\<sql:xpath-query>** テンプレート内の要素 (XPath クエリがある場合) またはアップデートグラムの要素に属性を指定することに加えて、 **\<updg:sync>** 次の操作を実行できます。  
  
-   テンプレートの `mapping-schema` **\<ROOT>** 要素 (グローバル宣言) に属性を指定します。 ここで指定したマッピング スキーマは、すべての XPath およびアップデートグラム ノードで、明示的に `mapping-schema` 注釈が指定されていない場合に既定のスキーマとして使用されます。  
  
-   `mapping schema`ADO オブジェクトを使用して属性を指定し `Command` ます。  
  
 `mapping-schema`要素または要素で指定された属性の **\<xpath-query>** **\<updg:sync>** 優先順位は最も高くなります。 ADO `Command` オブジェクトの優先順位は最も低くなります。  
  
 テンプレートで XPath クエリを指定し、XPath クエリの実行対象となるマッピングスキーマを指定しない場合、XPath クエリは**dbobject**型クエリとして扱われることに注意してください。 たとえば、次のテンプレートを考えてみます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 このテンプレートでは、XPath クエリが指定されていますが、マッピング スキーマが指定されていません。 したがって、このクエリは**dbobject**型クエリとして扱われます。 productphoto はテーブル名、 @ProductPhotoID = ' 100 ' は、ID 値が100の製品写真を検索する述語です。 @LargePhoto値の取得元の列を指定します。  
  
  
