---
title: レコード セットと SourceRecordset プロパティの例 (VBScript) |Microsoft ドキュメント
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Source property [ADO], VBScript example
- Recordset property [ADO], VBScript example
ms.assetid: 95175316-cd10-4cf7-96ba-2a226fd97701
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa0515e50e00632299012913303ebc5fbfc3a397
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-and-sourcerecordset-properties-example-vbscript"></a>レコード セットと SourceRecordset プロパティの例 (VBScript)
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 次の例のために必要なパラメーターを設定する方法を示しています、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)実行時に既定のビジネス オブジェクト。  
  
 この例をテストするを切り取って貼り付ける次のコード間、\<本文 > と\</Body > で標準の HTML タグが文書化し、名前を付けます**RecordsetVBS.asp**です。 ASP スクリプトは、サーバーで識別されます。  
  
```  
<!-- BeginRecordSetVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>Recordset and SourceRecordset Properties Example (VBScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>Recordset and SourceRecordset Properties Example (VBScript)</h1>  
  
<Center>  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Using SourceRecordset and Recordset with RDSServer.DataFactory</H3>  
<!-- RDS.DataSpace ID RDS1 -->  
<OBJECT ID="RDS1" WIDTH=1 HEIGHT=1   
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
</OBJECT>  
  
<!-- RDS.DataControl with parameters set at Run Time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDC WIDTH=1 HEIGHT=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDC>  
   <TR>  
      <TD> <INPUT DATAFLD="FirstName" SIZE=15> </TD>  
      <TD> <INPUT DATAFLD="LastName" SIZE=15></TD>  
   </TR>  
</TABLE>  
<HR>  
<Input Size=70 Name="txtServer" Value="http://<%=Request.ServerVariables("SERVER_NAME")%>"><BR>  
<Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"><BR>  
<Input Size=70 Name="txtSQL" Value="SELECT FirstName, LastName FROM Employees">  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run"><BR>  
  
</Center>  
<Script Language="VBScript">  
  
   Dim rdsDF  
   Dim strServer  
   strServer = "http://<%=Request.ServerVariables("SERVER_NAME")%>"  
  
   Sub Run_OnClick()  
  
      Dim rs           
      ' Create RDSServer.DataFactory Object  
      Set rdsDF = RDS1.CreateObject("RDSServer.DataFactory", strServer)                 
      ' Get Recordset  
      Set rs = rdsDF.Query(txtConnect.Value,txtSQL.Value)  
  
      ' Set parameters of RDS.DataControl at run time  
      RDC.Server = txtServer.Value  
      RDC.SQL = txtSQL.Value  
      RDC.Connect = txtConnect.Value  
      RDC.Refresh  
  
   End Sub  
  
</Script>  
  
</body>  
</html>  
<!-- EndRecordsetVBS -->  
```  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Recordset、SourceRecordset プロパティ (RDS)](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)



