---
title: 注釈付き XSD スキーマ (SQLXML 4.0) の概要 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 55452bb5b7444acef6fb37f21d9d2c39d59daf7c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093224"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>注釈付き XSD スキーマの概要 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML スキーマ定義 (XSD) 言語を使用して、リレーショナル データの XML ビューを作成することができます。 作成したビューには、XML パス言語 (XPath) クエリを実行できます。 これは、CREATE VIEW ステートメントを使用し、そのビューに対して SQL クエリを指定してビューの作成に似ています。  
  
 XML スキーマでは、XML ドキュメントの構造とドキュメント内のデータに対するさまざまな制約が記述されます。 スキーマに対して XPath クエリを指定した場合、返される XML ドキュメントの構造は、XPath クエリの実行対象のスキーマによって決定されます。  
  
 XSD スキーマで、  **\<xsd:schema >** 要素はスキーマ全体を囲む; 内ですべての要素宣言を含める必要があります、  **\<xsd:schema >** 要素。 内の名前空間を定義する属性を記述するスキーマが配置されていると、スキーマ内のプロパティとして使用される名前空間、  **\<xsd:schema >** 要素。  
  
 有効な XSD スキーマを含める必要があります、  **\<xsd:schema >** 次のように定義されている要素。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 **\<Xsd:schema >** 要素は XML スキーマ名前空間の仕様にから派 生 http://www.w3.org/2001/XMLSchema します。  
  
## <a name="annotations-to-the-xsd-schema"></a>XSD スキーマへの注釈  
 データベースへのマッピングを記述する注釈付きの XSD スキーマを使用して、データベースにクエリを実行し、結果を XML ドキュメントの形式で返すことができます。 注釈は、データベースのテーブルと列に XSD スキーマをマップするために指定します。 XSD スキーマで作成した XML ビューに対して XPath クエリを指定すると、データベースにクエリが実行され、結果を XML として取得できます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 の XSD スキーマ言語では、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] の注釈付き XML-Data Reduced (XDR) スキーマ言語で挿入された注釈がサポートされます。 ただし、注釈付き XDR は、SQLXML 4.0 では非推奨とされます。  
  
 リレーショナル データベースの場合、任意の XSD スキーマをリレーショナル ストアにマップすると便利です。 これを実行する 1 つの方法は、XSD スキーマに注釈を付けることです。 注釈付き XSD スキーマとして参照されます、*マッピング スキーマ*、XML データのリレーショナル ストアにマップする方法に関連する情報を提供します。 マッピング スキーマは、実質的にはリレーショナル データの XML ビューです。 これらのマッピングを使用して、リレーショナル データを XML ドキュメントとして取得できます。  
  
## <a name="namespace-for-annotations"></a>注釈の名前空間  
 名前空間を使用して、XSD スキーマで注釈が指定されて**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:mapping-schema}-スキーマ**します。 指定する名前空間を指定する最も簡単な方法は、次の例に示すように、  **\<xsd:schema >** タグ。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 使用される名前空間プレフィックスは任意です。 このドキュメントで、 **sql**注釈の名前空間を示す注釈と区別するこの名前空間の他の名前空間プレフィックスが使用されます。  
  
## <a name="example-of-an-annotated-xsd-schema"></a>注釈付き XSD スキーマの例  
 XSD スキーマを構成する次の例では、  **\<Person.Contact >** 要素。 **\<従業員 >** 要素には、 **ContactID**属性と **\<FirstName >** と **\<LastName >** 子要素。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 この XSD スキーマに、要素と属性をデータベースのテーブルと列にマップするため、注釈を追加します。  
  
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
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 マッピング スキーマで、 **\<連絡先 >** 要素を使用してサンプル データベース AdventureWorks の Person.Contact テーブルにマップされます、 **sql:relation**注釈。 使用して属性 ConID、FName、LName が Person.Contact テーブル内の ContactID、FirstName、および LastName 列にマップされている、 **sql:field**注釈。  
  
 この注釈付きの XSD スキーマによって、リレーショナル データの XML ビューが提供されます。 この XML ビューには、XPath 言語を使用してクエリを実行できます。 XPath クエリを実行すると、SQL クエリによって返される行セットではなく、XML ドキュメントが返されます。  
  
> [!NOTE]  
>  マッピング スキーマに指定するリレーショナル値 (テーブル名や列名など) の大文字小文字の区別は、SQL Server で使用される照合順序の、大文字小文字の区別の設定によって変わります。 詳細については、「 [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="other-resources"></a>その他の参照情報  
 XML スキーマ定義言語 (XSD)、XML パス言語 (XPath)、Extensible Stylesheet Language Transformations (XSLT) の詳細については、次の Web サイトを参照してください。  
  
-   XML Schema Part 0:入門, W3C 推奨事項 (http://www.w3.org/TR/xmlschema-0/)  
  
-   XML Schema Part 1:構造体、W3C 勧告 (http://www.w3.org/TR/xmlschema-1/)  
  
-   XML Schema Part 2: datatypes,、W3C 勧告 (http://www.w3.org/TR/xmlschema-2/)  
  
-   XML Path Language (XPath) (http://www.w3.org/TR/xpath)  
  
-   XSL Transformations (XSLT) (http://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>関連項目  
 [スキーマのセキュリティに関する考慮事項を注釈が付けられた&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [注釈付き XDR スキーマ&#40;SQLXML 4.0 で非推奨とされます。&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
