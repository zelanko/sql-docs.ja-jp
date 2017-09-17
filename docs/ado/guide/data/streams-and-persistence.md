---
title: "ストリームおよび永続化 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisted streams [ADO]
- streams [ADO], persistence
ms.assetid: ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: af1ecf7ed9f4702d986d6f1881b3264ab8171c87
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="streams-and-persistence"></a>ストリームと永続性
[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト[保存](../../../ado/reference/ado-api/save-method.md)メソッド ストア、または*が引き続き発生する*、**レコード セット**ファイル、および[を開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッド復元、 **Recordset**そのファイルからです。  
  
 ADO 2.7 以降を**保存**と**開く**メソッドを永続化できる、**レコード セット**を[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトもします。 この機能は、リモート データ サービス (RDS) や Active Server Pages (ASP) を使用する場合に便利です。  
  
 ASP ページで永続化を単独で使用する方法の詳細については、現在の ASP のマニュアルを参照してください。  
  
 次に示すいくつかのシナリオ方法**ストリーム**オブジェクトおよび永続化を使用できます。  
  
## <a name="scenario-1"></a>シナリオ 1  
 このシナリオを単純に保存、 **Recordset** 、ファイルに、**ストリーム**です。 別に、永続化ストリームを開きます**Recordset**です。  
  
```  
Dim rs1 As ADODB.Recordset  
Dim rs2 As ADODB.Recordset  
Dim stm As ADODB.Stream  
  
Set rs1 = New ADODB.Recordset  
Set rs2 = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
rs1.Open   "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;""", adopenStatic, adLockReadOnly, adCmdText  
rs1.Save "c:\myfolder\mysubfolder\myrs.xml", adPersistXML  
rs1.Save stm, adPersistXML  
rs2.Open stm  
```  
  
## <a name="scenario-2"></a>シナリオ 2  
 このシナリオが引き続き発生する、 **Recordset**に、**ストリーム**XML 形式でします。 これは、後、読み取ります、**ストリーム**を調べて、操作、または表示できる文字列にします。  
  
```  
Dim rs As ADODB.Recordset  
Dim stm As ADODB.Stream  
Dim strRst As String  
  
Set rs = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
' Open, save, and close the recordset.   
rs.Open "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
rs.Save stm, adPersistXML  
rs.Close  
Set rs = nothing  
  
' Put saved Recordset into a string variable.  
strRst = stm.ReadText(adReadAll)  
  
' Examine, manipulate, or display the XML data.  
...  
```  
  
## <a name="scenario-3"></a>シナリオ 3  
 このコード例は、ASP コードの永続化を示しています、 **Recordset**に直接 XML として、**応答**オブジェクト。  
  
```  
...  
<%  
response.ContentType = "text/xml"  
  
' Create and open a Recordset.  
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select * from Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
  
' Save Recordset directly into output stream.  
rs.Save Response, adPersistXML   
  
' Close Recordset.  
rs.Close  
Set rs = nothing  
%>  
...  
```  
  
## <a name="scenario-4"></a>シナリオ 4  
 このシナリオでは、ASP コードの内容を書き込みます。、**レコード セット**では、クライアント adtg 形式形式です。 [OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)このデータを使用して、切断されている作成**Recordset**です。  
  
 新しいプロパティ、RDS を[DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)、 [URL](../../../ado/reference/rds-api/url-property-rds.md)、によって生成される「*.asp ページを指す、**レコード セット**です。 つまり、 **Recordset**オブジェクトを取得できる RDS せず、サーバー側を使用して[DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクトまたはビジネス オブジェクトの書き込みユーザー。 これにより、RDS プログラミング モデルが大幅に合理化されます。  
  
 サーバー側コード、http://server/directory/recordset.asp をという名前です。  
  
```  
<%  
Dim rs   
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select au_fname, au_lname, phone from Authors", ""& _  
        "Provider=sqloledb;Data Source=MyServer;" & _  
        "Initial Catalog=Pubs;Integrated Security=SSPI;"  
response.ContentType = "multipart/mixed"  
rs.Save response, adPersistADTG  
%>  
```  
  
 クライアント側コードに示します。  
  
```  
<HTML>  
<HEAD>  
<TITLE>RDS Query Page</TITLE>  
</HEAD>  
<body>  
<CENTER>  
<H1>Remote Data Service 2.5</H1>  
<TABLE DATASRC="#DC1">  
   <TR>   
      <TD><SPAN DATAFLD="au_fname"></SPAN></TD>  
      <TD><SPAN DATAFLD="au_lname"></SPAN></TD>  
      <TD><SPAN DATAFLD="phone"></SPAN></TD>  
   </TR>  
</TABLE>  
<BR>  
  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
    ID=DC1 HEIGHT=1 WIDTH = 1>  
    <PARAM NAME="URL" VALUE="http://server/directory/recordset.asp">  
</OBJECT>  
  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 開発者を使用するオプションもある、 **Recordset**クライアント上のオブジェクト。  
  
```  
...  
function GetRs()   
    {  
    rs = CreateObject("ADODB.Recordset");  
    rs.Open "http://server/directory/recordset.asp"  
    DC1.SourceRecordset = rs;  
    }  
...  
```  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
