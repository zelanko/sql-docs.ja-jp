---
title: 'Sql を使用した CDATA セクションの作成: Using-cdata (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8f1442011ddbdb010e5f498dbf3b42fa9ba333ea
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703650"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>sql:use-cdata を使用した、CDATA セクションの作成 (SQLXML 4.0)
  XML では、文字がマークアップ文字として処理されないよう、文字を含むテキスト ブロックをエスケープするときに CDATA セクションを使用します。  
  
 Microsoft のデータベースには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML パーサーによってマークアップ文字として扱われる文字を含めることができます。たとえば、山かっこ ( \< と >)、小なり記号 (<=)、アンパサンド (&) は、マークアップ文字として扱われます。 この種類の特殊文字は、CDATA セクションで囲むことでマークアップ文字として扱われないようにできます。 CDATA セクション内の文字は、XML パーサーでプレーン テキストとして扱われます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で返されるデータを CDATA セクションで囲むには、`sql:use-cdata` 注釈を使用します。この注釈では、`sql:field` で指定される列の値を CDATA セクションで囲むかどうかを指定できます。 `sql:use-cdata` 注釈は、データベース列にマップされる要素だけに指定できます。  
  
 `sql:use-cdata` 注釈はブール値 (0 = false、1 = true) をとります。 指定できる値は 0、1、true、false です。  
  
 この注釈は、`sql:url-encode` と共に使用したり、ID、IDREF、IDREFS、NMTOKEN、NMTOKENS 属性型に使用することはできません。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>A. 要素に対して sql:use-cdata を指定する  
 次のスキーマで `sql:use-cdata` は、 ** \< Address>** 要素内の** \< AddressLine1>** に対してが 1 (True) に設定されています。 この結果、データは CDATA セクション内に返されます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 UseCData.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 UseCData.xml を保存したディレクトリに UseCDataT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (UseCData.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 結果セットの一部を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
