---
title: SQL クエリを含むテンプレートの実行 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- templates [SQLXML]
- SQLXMLOLEDB Provider, executing template files
- templates [SQLXML], SQL queries
- XML templates [SQLXML]
- SQL queries [SQLXML]
ms.assetid: ff2bc36f-e3fb-4d8f-8e3a-2680a39eda11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdf149720e853725a7f2fc9d0c03b24ea2caf9f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013123"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a>SQL クエリを含むテンプレートの実行 (SQLXMLOLEDB プロバイダー)
  この例は、SQLXMLOLEDB プロバイダー固有のプロパティ ClientSideXML の使用方法を示しています。 このクライアント側の ADO サンプル アプリケーションでは、SQL クエリで構成される XML テンプレートがサーバーで実行されます。  
  
 ClientSideXML プロパティが True に設定されているため、FOR XML 句を指定せずに SELECT ステートメントがサーバーに送信されます。 サーバーではクエリが実行され、クライアントに行セットが返されます。 次にクライアントではその行セットに FOR XML 変換が適用され、XML ドキュメントが作成されます。  
  
 XML テンプレートでは、生成される XML ドキュメントの最\<上位レベルのルート要素 (ルート>) が1つ提供されます。そのため、xml ルートプロパティが指定されていません。  
  
 XML テンプレートを実行するには、言語 {5d531cb2-e6ed-11d2-b252-00c04f681b71} を指定する必要があります。  
  
> [!NOTE]  
>  コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。 また、この例では、追加の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネットワーククライアントソフトウェアをインストールする必要があるデータプロバイダーに対して Native CLIENT (SQLNCLI11) を使用するように指定しています。 詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。  
  
```  
Option Explicit  
  
Sub Main()  
  Dim oTestStream As New ADODB.Stream  
  Dim oTestConnection As New ADODB.Connection  
  Dim oTestCommand As New ADODB.Command  
  oTestConnection.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
  
  Set oTestCommand.ActiveConnection = oTestConnection  
  oTestCommand.Properties("ClientSideXML") = True  
  oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:query> " & _  
        "   SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
  oTestStream.Open  
  ' You need the dialect if you are executing   
  ' XML templates (not for SQL queries).  
  oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  oTestCommand.Properties("Output Stream").Value = oTestStream  
  oTestCommand.Execute , , adExecuteStream  
  
  oTestStream.Position = 0  
  oTestStream.Charset = "utf-8"  
  Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
  
Sub Form_Load()  
  Main  
End Sub  
```  
  
  
