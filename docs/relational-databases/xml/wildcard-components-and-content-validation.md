---
title: "ワイルドカード コンポーネントと内容検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ワイルドカード コンポーネント [XML]"
  - "内容の検証 [XML]"
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# ワイルドカード コンポーネントと内容検証
  ワイルドカード コンポーネントは、コンテンツ モデルで使用できる表現の柔軟性を高めるために使用されます。 ワイルドカード コンポーネントは、次のように XSD 言語でサポートされています。  
  
-   要素ワイルドカード コンポーネント。 これらは **\<xsd:any>** 要素で表現されます。  
  
-   属性ワイルドカード コンポーネント。 これらは **\<xsd:anyAttribute>** 要素で表現されます。  
  
 両方のワイルドカード文字要素 (**\<xsd:any>** および **\<xsd:anyAttribute>**) で **processContents** 属性を使用できます。 この属性を使用して、ワイルドカード文字要素で関連付けられるドキュメントの内容の違反を、XML アプリケーションで検証する方法を示す値を指定できます。 検証方法を示す値には、次のようにそれぞれ異なる効果があります。  
  
-   **strict** 値は、内容を完全に検証することを指定します。  
  
-   **skip** 値は、内容を検証しないことを指定します。  
  
-   **lax** 値は、スキーマ定義が有効な要素と属性だけを検証することを指定します。  
  
## lax 検証と xs:anyType 要素  
 XML スキーマの仕様では、 **anyType** 型の要素には **lax** 検証が使用されています。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では lax 検証をサポートしていなかったので、 **anyType**型の要素にも strict 検証が適用されていました。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]からは lax 検証がサポートされるようになったため、 **anyType** 型の要素の内容は lax 検証を使用して検証されます。  
  
 次の例は、lax 検証を示しています。 スキーマ要素 `e` は **anyType** 型です。 この例では、型指定された **xml** 変数を作成し、 **anyType** 型の要素の lax 検証を示します。  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 `<e>` の検証が成功するので、次の例は成功します。  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 次の例は成功します。 要素 `<c>` はスキーマで定義されていませんが、インスタンスは受け入れられます。  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 次の例の XML インスタンスは拒否されます。これは、`<a>` 要素の定義で文字列値が許可されていないためです。  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## 参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  