---
title: XPath クエリを含むテンプレートの実行 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing template files
- Base Path property
- templates [SQLXML], XPath queries
- XPath queries [SQLXML], templates
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
- XML templates [SQLXML]
ms.assetid: 7368c188-607e-459e-8254-8f23352dfa01
author: rothja
ms.author: jroth
ms.openlocfilehash: 227c8a5b3222bdddab9632ec2e80f0bb4dd54250
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015599"
---
# <a name="executing-templates-that-contain-xpath-queries-sqlxmloledb-provider"></a>XPath クエリを含むテンプレートの実行 (SQLXMLOLEDB プロバイダー)
  この例では、次の SQLXMLOLEDB プロバイダー固有のプロパティについて、使用法を示します。  
  
-   ClientSideXML  
  
-   基本パス  
  
-   マッピング スキーマ  
  
 このサンプル ADO アプリケーションでは、XPath クエリ (ルート) で構成される XML テンプレートが XSD マッピングスキーマ (MySchema.xml) に対して指定されています。これについては、「 [Xpath クエリ &#40;SQLXMLOLEDB Provider&#41;を実行](executing-xpath-queries-sqlxmloledb-provider.md)する」を参照してください。  
  
 マッピングスキーマプロパティは、XPath クエリの実行対象となる XSD マッピングスキーマを提供します。 Base Path プロパティは、マッピングスキーマへのファイルパスを提供します。  
  
 ClientSideXML プロパティは True に設定されています。 つまり、XML ドキュメントはクライアントで生成されます。  
  
 このアプリケーションでは、XPath クエリを直接指定します。 したがって、言語 {5d531cb2-e6ed-11d2-b252-00c04f681b71} を含める必要があります。  
  
> [!NOTE]  
>  コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。 また、この例では、追加の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ネットワーククライアントソフトウェアをインストールする必要があるデータプロバイダーに対して Native Client (SQLNCLI11) を使用するように指定しています。 詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。  
  
```  
Option Explicit  
Sub Main()  
  
   Dim oTestStream As New ADODB.Stream  
   Dim oTestConnection As New ADODB.Connection  
   Dim oTestCommand As New ADODB.Command  
  
   oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
  
   oTestCommand.ActiveConnection = oTestConnection  
   oTestCommand.Properties("ClientSideXML") = "False"  
  
   oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:xpath-query mapping-schema='mySchema.xml' > " & _  
        "   root " & _  
        "   </sql:xpath-query> " & _  
        " </ROOT> "  
   oTestStream.Open  
   ' You need the dialect if you are executing a template.  
   oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
   oTestCommand.Properties("Output Stream").Value = oTestStream  
   oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\TemplateWithXPath\"  
   oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
   oTestCommand.Properties("Output Encoding") = "utf-8"  
   oTestCommand.Execute , , adExecuteStream  
   oTestStream.Position = 0  
   oTestStream.Charset = "utf-8"  
   Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
  
Sub Form_Load()  
   Main  
End Sub  
```  
  
 スキーマは次のようになります。  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contact'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  
  <xsd:element name='Contact' sql:relation='Person.Contact'>  
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
  
