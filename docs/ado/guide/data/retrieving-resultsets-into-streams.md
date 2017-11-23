---
title: "ストリームへの結果セットの取得 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streams [ADO], retrieving query results
- query results into stream [ADO]
- retrieving results into stream [ADO]
ms.assetid: 996c1321-c926-4f57-8297-85c8c20de974
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed2d2412cf8314875f9469689677c22ae4e60e7e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="retrieving-resultsets-into-streams"></a>ストリームへの結果セットの取得
従来の結果を受信するのではなく**Recordset**オブジェクト、ADO がストリームにクエリの結果を代わりに取得できます。 ADO**ストリーム**オブジェクト (またはその他のオブジェクト、COM をサポートする**IStream** ASP などのインターフェイス**要求**と**応答**オブジェクト) これらの結果を含めるために使用できます。 この機能の 1 つの用途は、XML 形式で結果を取得です。 SQL server などの XML 結果は返されません SQL SELECT クエリを使用した FOR XML 句を使用して、XPath クエリを使用するなど、複数の方法でします。  
  
 はなくストリーム形式でクエリの結果を受信する、 **Recordset**を指定する必要があります、 **adExecuteStream**から定数**ExecuteOptionEnum**のパラメーターとして、**Execute**のメソッド、**コマンド**オブジェクト。 プロバイダーは、この機能をサポートする場合は、実行時にストリームの結果が返されます。 コードが実行される前に、追加のプロバイダー固有のプロパティを指定する必要があります。 など、Microsoft OLE DB Provider for SQL Server などのプロパティと**出力ストリーム**で、**プロパティ**のコレクション、**コマンド**オブジェクトでなければなりません指定します。 SQL Server に固有の詳細については、この機能に関連する動的なプロパティでは、SQL Server オンライン ブックで XML-Related プロパティを参照してください。  
  
## <a name="for-xml-query-example"></a>XML クエリの例について  
 次の例は、Northwind データベースを VBScript に書き込まれます。  
  
```  
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<%  Option Explicit      %>  
  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=" & _  
      Request.ServerVariables("SERVER_NAME") & ";" & _  
      Initial Catalog=Northwind;Integrated Security=SSPI;"  
  
   Response.write "Connect String = " & sConn & "<BR/>"  
  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
  
   adoConn.Open  
  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT * FROM PRODUCTS WHERE ProductName='Gumbr Gummibrchen' FOR XML AUTO</sql:query></ROOT>"  
  
   Response.write "Query String = " & sQuery & "<BR/>"  
  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
  
%>  
  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   xmlDoc.resolveExternals=false  
   xmlDoc.async=false  
  
   If xmlDoc.parseError.Reason <> "" then  
      Msgbox "parseError.Reason = " & xmlDoc.parseError.Reason  
   End If  
  
   Dim root, child  
   Set root = xmlDoc.documentElement  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI>" & child.getAttribute("ProductName") & "</LI>"  
   Next  
</SCRIPT>  
  
</HEAD>  
  
<BODY>  
  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
  
```  
  
 FOR XML 句では、SQL Server の XML ドキュメントの形式でデータを返すように指示します。  
  
### <a name="for-xml-syntax"></a>XML 構文の  
  
```  
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 生の XML 属性として列の値を持つジェネリックの行要素が生成されます。 FOR XML AUTO には、ヒューリスティックを使用して、テーブル名に基づく要素の名前の階層ツリーを生成します。 FOR XML EXPLICIT には、メタデータで完全に記述されるリレーションシップを持つユニバーサル テーブルを生成します。  
  
 SQL SELECT FOR XML ステートメントの例を次に示します。  
  
```  
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 コマンドに指定できます文字列ように、前に割り当てられている**CommandText**、またはに割り当てられている XML テンプレートのクエリの形式で**CommandStream**です。 XML テンプレートのクエリの詳細については、次を参照してください。[コマンド ストリーム](../../../ado/guide/data/command-streams.md)ADO または、SQL Server オンライン ブックでのコマンドの入力を使用するストリーム。  
  
 XML テンプレート クエリとして、FOR XML クエリは次のとおりです。  
  
```  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 この例で指定、ASP**応答**オブジェクトに対して、**出力ストリーム**プロパティ。  
  
```  
adoCmd.Properties("Output Stream") = Response  
```  
  
 次に、指定**adExecuteStream**のパラメーター **Execute**です。 この例では、XML データ アイランドを作成する XML タグ内のストリームをラップします。  
  
```  
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>解説  
 この時点では、クライアントのブラウザーにストリーミングされた XML とを表示する準備ができた。 これは、XML ドキュメントを html 形式での製品の一覧を作成する DOM とそれぞれの子ノードのループのインスタンスにバインドするクライアント側の VBScript を使用して行います。
