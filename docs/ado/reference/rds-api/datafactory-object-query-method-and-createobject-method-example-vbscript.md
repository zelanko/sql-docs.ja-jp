---
title: CreateObject (VBScript) を使用して RDSServer.DataFactory オブジェクトを作成 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- DataFactory object [ADO], VBScript example
- CreateObject method [ADO], VBScript example
- Query method [ADO], VBScript example
ms.assetid: b4e2844a-120a-4513-860b-f1b6e4b5dda4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 68d525fd05162fe0b4136dc7e812f7788889bdf0
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="datafactory-object-query-method-and-createobject-method-example-vbscript"></a>DataFactory オブジェクト、クエリのメソッド、および CreateObject メソッドの例 (VBScript)
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 この例で作成、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクトを使用して、 [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md)のメソッド、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクト。 この例をテストするを切り取って貼り付ける次のコード間、\<本文 > と\</Body > で標準の HTML タグが文書化し、名前を付けます**DataFactoryVBS.asp**です。 ASP スクリプトは、サーバーで識別されます。  
  
```  
<!-- BeginDataFactoryVBS -->  
<HTML>  
<HEAD>  
<!--use the following META tag instead of adovbs.inc-->  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<META name="VI60_DefaultClientScript" Content="VBScript">  
  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<TITLE>DataFactory Object, Query Method, and   
CreateObject Method Example (VBScript)</TITLE>  
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
</HEAD>  
<BODY>  
<h1>DataFactory Object, Query Method, and   
CreateObject Method Example (VBScript)</h1>  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Using Query Method of RDSServer.DataFactory</H3>  
  
<!-- RDS.DataSpace  ID RDS1-->  
<OBJECT ID="RDS1" WIDTH=1 HEIGHT=1  
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
</OBJECT>  
  
<!-- RDS.DataControl with parameters   
set at run time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDS WIDTH=1 HEIGHT=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
    <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
  </TR>  
</TBODY>      
</TABLE>  
  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run">  
<BR>  
<H4>Click Run -    
The <i>CreateObject</i> Method of the RDS.DataSpace Object Creates   
an instance of the RDSServer.DataFactory;   
The <i>Query</i> Method of the RDSServer.DataFactory is used  
to bring back a Recordset. </H4>  
  
<Script Language="VBScript">  
  
    Dim rdsDF  
    Dim strServer  
    Dim strCnxn  
    Dim strSQL  
  
    strServer = "http://<%=Request.ServerVariables("SERVER_NAME")%>"  
    strCnxn = "Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';"  
    strSQL = "Select FirstName, LastName from Employees"  
  
    Sub Run_OnClick()  
  
        ' Create RDSServer.DataFactory Object  
        Dim rs  
        ' Get Recordset  
        Set DF = RDS1.CreateObject("RDSServer.DataFactory", strServer)  
        Set rs = DF.Query(strCnxn, strSQL)  
        ' Set parameters of RDS.DataControl at Run Time  
        RDS.Server = strServer  
        RDS.SQL = strSQL  
        RDS.Connect = strCnxn  
        RDS.Refresh  
  
    End Sub  
</Script>  
  
</BODY>  
</HTML>  
<!-- EndDataFactoryVBS -->  
```  
  
## <a name="see-also"></a>参照  
 [CreateObject メソッド (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)   
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [クエリ メソッド (RDS)](../../../ado/reference/rds-api/query-method-rds.md)


