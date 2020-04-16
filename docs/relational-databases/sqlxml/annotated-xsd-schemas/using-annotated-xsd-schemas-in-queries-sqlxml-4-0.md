---
title: クエリでのコメント付き XSD スキーマの使用 (SQLXML)
description: SQLXML 4.0 で、コメント付き XSD スキーマに対して XPath クエリを指定して、データベースからデータを取得する方法について説明します。
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e9ecd9d65d0f70f7c25328c15bb886ca52122de2
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388689"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  注釈付きスキーマに対してクエリを指定し、XSD スキーマに対してテンプレートで XPath クエリを指定して、データベースからデータを取得することができます。  
  
 sql:xpath-query>要素を使用すると、アノテーション付きスキーマによって定義される XML ビューに対して XPath クエリを指定できます。 ** \<** XPath クエリを実行するアノテーション付きスキーマは、 ** \<sql:xpath クエリ>** 要素の**マッピング スキーマ**属性を使用して識別されます。  
  
 テンプレートは、1 つ以上のクエリを含む有効な XML ドキュメントです。 FOR XML クエリと XPath クエリでは、ドキュメント フラグメントが返されますが、 テンプレートはドキュメント フラグメントのコンテナとして機能します。したがって、テンプレートは、単一の最上位要素を指定する方法を提供します。  
  
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
  
 SQLXML 4.0 のテスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用すると、テンプレート ファイルの一部としてクエリを実行できます。 詳細については、「 [SQLXML 4.0&#41;で非推奨&#40;XDR スキーマのコメント付け](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)」を参照してください。  
  
## <a name="using-inline-mapping-schemas"></a>インライン マッピング スキーマの使用  
 注釈付きスキーマはテンプレートに直接含めることができます。このテンプレートで、インライン スキーマに対する XPath クエリを指定できます。 テンプレートはアップデートグラムとしても使用できます。  
  
 テンプレートには複数のインライン スキーマを含めることができます。 テンプレートに含まれるインライン スキーマを使用するには**\<、xsd:schema>** 要素に一意の値を持つ**id** **属性を指定**し、#idvalueを使用してインライン スキーマを参照します。 **id**属性は、XDR スキーマで使用される**sql:id** ({urn:スキーマ-マイクロソフト-com:xml-sql}id) と動作が同じです。  
  
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
  
 このテンプレートでは 2 つの XPath クエリも指定しています。 xpath-query>要素のそれぞれは、**マッピング**スキーマ属性を指定することによって、マッピングスキーマを一意に識別します。 ** \<**  
  
 テンプレートでインライン スキーマを指定する場合は**\<、xsd:schema>** 要素にも**sql:is-mapping-schema**アノテーションを指定する必要があります。 **sql:is-mapping-schema**はブール値 (0=false,1=true) を受け取ります。 **sql:is-mapping-schema="1" を**持つインライン スキーマは、インラインのアポイントナ付きスキーマとして扱われ、XML ドキュメントでは返されません。  
  
 **sql:is-mapping-schema**アノテーションはテンプレート名前空間**urn:スキーマ-microsoft-com:xml-sql**に属しています。  
  
 この例をテストするには、テンプレート (InlineSchemaTemplate.xml) をローカルのディレクトリに保存した後、SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。 詳細については、「 [ADO を使用した SQLXML 4.0 クエリの実行](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 テンプレート内の**\<sql:xpath-query>要素(XPath クエリ**がある場合)、または更新グラムの**\<updg:sync>** 要素に**マッピング スキーマ**属性を指定する以外に、次の操作を行うことができます。  
  
-   テンプレートの**\<ROOT>** 要素 (グローバル宣言) に**マッピング スキーマ**属性を指定します。 このマッピング スキーマは、明示的なマッピング スキーマ アノテーションを持たないすべての XPath ノードおよびアップデートグラム ノードで使用される既定**のスキーマ**になります。  
  
-   ADO**コマンド**オブジェクトを使用して **、マッピング スキーマ**属性を指定します。  
  
 xpath**クエリ**>または**\<updg:sync>** 要素で指定されているマッピング スキーマ属性は、優先順位が最も高くなります。 ** \<** ADO**コマンド**オブジェクトの優先順位は最も低くなります。  
  
 テンプレートで XPath クエリを指定し、XPath クエリを実行するマッピング スキーマを指定しない場合、XPath クエリは**dbobject**型クエリとして扱われます。 たとえば、次のテンプレートを考えてみます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 このテンプレートでは、XPath クエリが指定されていますが、マッピング スキーマが指定されていません。 したがって、このクエリは、テーブル名が Production.ProductPhoto、ID@ProductPhotoID値が 100 の商品写真を検索する述語である**dbobject**型クエリとして扱われます。 @LargePhotoは、値の取得元となる列です。  
  
  
