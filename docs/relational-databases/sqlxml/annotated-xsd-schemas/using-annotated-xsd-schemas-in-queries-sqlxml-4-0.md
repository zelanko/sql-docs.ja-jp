---
title: クエリ (SQLXML 4.0) での XSD スキーマを使用して注釈が付けられた |Microsoft Docs
ms.custom: ''
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c9229f612c45c2163148b809d8a79de592f06b32
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041079"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  注釈付きスキーマに対してクエリを指定し、XSD スキーマに対してテンプレートで XPath クエリを指定して、データベースからデータを取得することができます。  
  
 **\<Sql:xpath-クエリ >** 要素では、注釈付きスキーマで定義されている XML ビューに対して XPath クエリを指定することができます。 使用して実行するのには、XPath クエリ対象となる注釈付きスキーマが識別される、**マッピング スキーマ**の属性、  **\<sql:xpath-クエリ >** 要素。  
  
 テンプレートは、1 つ以上のクエリを含む有効な XML ドキュメントです。 FOR XML クエリと XPath クエリでは、ドキュメント フラグメントが返されますが、 テンプレートは、ドキュメント フラグメントのコンテナーとして機能します。テンプレートは、そのため、1 つの最上位の要素を指定する方法を提供します。  
  
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
  
 SQLXML 4.0 のテスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用すると、テンプレート ファイルの一部としてクエリを実行できます。 詳細については、次を参照してください。[注釈付き XDR スキーマ&#40;SQLXML 4.0 では非推奨&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)します。  
  
## <a name="using-inline-mapping-schemas"></a>インライン マッピング スキーマの使用  
 注釈付きスキーマはテンプレートに直接含めることができます。このテンプレートで、インライン スキーマに対する XPath クエリを指定できます。 テンプレートはアップデートグラムとしても使用できます。  
  
 テンプレートには複数のインライン スキーマを含めることができます。 テンプレートに含まれているインライン スキーマを使用する指定、 **id**属性の一意の値に、  **\<xsd:schema >** 要素、およびしを使用して **#idvalue**インライン スキーマを参照します。 **Id**属性の動作と同じですが、 **sql:id** ({urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-sql} id) XDR スキーマで使用します。  
  
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
  
 このテンプレートでは 2 つの XPath クエリも指定しています。 各、  **\<xpath クエリ >** を指定して、マッピング スキーマを一意に識別する要素、**マッピング スキーマ**属性。  
  
 テンプレートでは、インライン スキーマを指定するときに、 **sql: はマッピング スキーマ**注釈はでも指定する必要があります、  **\<xsd:schema >** 要素。 **Sql: はマッピング スキーマ**はブール値 (0 = false、1 = true)。 インライン スキーマ**sql: はマッピング スキーマ =「1」** はインライン注釈付きスキーマとして扱われ、XML ドキュメントでは返されません。  
  
 **Sql: はマッピング スキーマ**注釈は、テンプレートの名前空間に属する **urn:schemas-microsoft-com:xml-sql** します。  
  
 この例をテストするには、テンプレート (InlineSchemaTemplate.xml) をローカルのディレクトリに保存した後、SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。 詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
 指定するだけでなく、**マッピング スキーマ**属性を **\<sql:xpath-クエリ >** 要素 (XPath クエリがある) 場合のテンプレート、または **\<updg:sync >** 要素、アップデート グラムで、次を行うことができます。  
  
-   指定、**マッピング スキーマ**属性を **\<ルート >** テンプレート内の要素 (グローバル宣言)。 このマッピング スキーマになりますが、明示的なすべての XPath およびアップデート グラムのノードで使用される既定のスキーマ**マッピング スキーマ**注釈。  
  
-   指定、**マッピング スキーマ**、ADO を使用して属性**コマンド**オブジェクト。  
  
 **マッピング スキーマ**属性で指定されている、  **\<xpath クエリ >** または **\<updg:sync >** 要素が一番多いも優先されます。ADO**コマンド**オブジェクトには最低の優先順位。  
  
 テンプレートの XPath クエリを指定し、XPath クエリの実行対象となるマッピング スキーマを指定しない場合、XPath クエリとして扱われます、 **dbobject**型のクエリ。 たとえば、次のテンプレートを考えてみます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 このテンプレートでは、XPath クエリが指定されていますが、マッピング スキーマが指定されていません。 したがって、このクエリとして扱う、 **dbobject**を Production.ProductPhoto はテーブル名の種類のクエリと@ProductPhotoID= '100' は ID 値 100 の製品の写真を検索する述語です。 @LargePhoto 元の値を取得する列です。  
  
  
