---
title: XML レコード セットを永続化シナリオ |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence scenario
ms.assetid: 353d569a-043a-4397-9ee6-564c4af8d5f6
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c16d37a0ded8b8a4a24666a426e123505eeff8f0
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273411"
---
# <a name="xml-recordset-persistence-scenario"></a>XML レコード セットを保存するシナリオ
このシナリオでは、ASP 応答オブジェクトに直接、レコード セット オブジェクトの内容を保存する Active Server Pages (ASP) アプリケーションを作成します。  
  
> [!NOTE]
>  このシナリオには、サーバーがインターネット インフォメーション サーバー 5.0 (iis) や、後でインストールされている必要があります。  
  
 返されるレコード セットが Internet Explorer で表示を使用して、 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)です。  
  
 次の手順は、このシナリオを作成する必要があります。  
  
-   アプリケーションを設定します。  
  
-   データを取得します。  
  
-   データを送信します。  
  
-   受信し、データの表示  
  
## <a name="step-1-set-up-the-application"></a>手順 1: アプリケーションを設定します。  
 スクリプトのアクセス許可を持つ"XMLPersist"をという名前の IIS 仮想ディレクトリを作成します。 仮想ディレクトリが指す、1 つ名前付き"XMLResponse.asp、"、その他の名前付き"Default.htm です"フォルダーに 2 つの新しいテキスト ファイルを作成します。  
  
## <a name="step-2-get-the-data"></a>手順 2: データを取得します。  
 このステップでは、ADO レコード セットを開くし、クライアントに送信する準備をするコードを記述します。 メモ帳などのテキスト エディターで XMLResponse.asp ファイルを開き、次のコードを挿入します。  
  
```  
<%@ language="VBScript" %>  
  
<!-- #include file='adovbs.inc' -->  
  
<%  
  Dim strSQL, strCon  
  Dim adoRec   
  Dim adoCon   
  Dim xmlDoc   
  
  ' You will need to change "MySQLServer" below to the name of the SQL   
  ' server machine to which you want to connect.  
  strCon = "Provider=sqloledb;Data Source=MySQLServer;Initial Catalog=Pubs;Integrated Security=SSPI;"  
  Set adoCon = server.createObject("ADODB.Connection")  
  adoCon.Open strCon  
  
  strSQL = "SELECT Title, Price FROM Titles ORDER BY Price"  
  Set adoRec = Server.CreateObject("ADODB.Recordset")  
  adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText  
```  
  
 値を変更してください、`Data Source`パラメーター `strCon` Microsoft SQL Server コンピューターの名前にします。  
  
 開いたままで、ファイル、次の手順に進んでください。  
  
## <a name="step-3-send-the-data"></a>手順 3: データを送信します。  
 レコード セットがある場合は、これでは、ASP 応答オブジェクトを XML として保存することによって、クライアントに送信する必要があります。 XMLResponse.asp の下部に次のコードを追加します。  
  
```  
  Response.ContentType = "text/xml"  
  Response.Expires = 0  
  Response.Buffer = False  
  
  Response.Write "<?xml version='1.0'?>" & vbNewLine  
  adoRec.save Response, adPersistXML  
  adoRec.Close  
  Set adoRec=Nothing  
%>  
```  
  
 レコード セットの送信先として ASP 応答オブジェクトが指定されていることを確認[Save メソッド](../../../ado/reference/ado-api/save-method.md)です。 Save メソッドの保存先は、ADO など、IStream インターフェイスをサポートする任意のオブジェクトを指定できます[ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)、またはレコード セットが保存される完全なパスを含むファイル名。  
  
 保存して、次の手順に進む前に XMLResponse.asp を閉じます。 また adovbs.inc ファイルを既定 ADO ライブラリのインストール フォルダーを XMLResponse.asp ファイルを保存したのと同じフォルダーにコピーします。  
  
## <a name="step-4-receive-and-display-the-data"></a>手順 4: 受信し、データを表示  
 この手順では、埋め込まれたを HTML ファイルを作成します[DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)レコード セットを取得する XMLResponse.asp ファイルをポイントするオブジェクト。 Default.htm をメモ帳などのテキスト エディターで開き、次のコードを追加します。 URL に"sqlserver"をサーバーの名前に置き換えます。  
  
```  
<HTML>  
<HEAD><TITLE>ADO Recordset Persistence Sample</TITLE></HEAD>  
<BODY>  
  
<TABLE DATASRC="#RDC1" border="1">  
  <TR>  
<TD><SPAN DATAFLD="title"></SPAN></TD>  
<TD><SPAN DATAFLD="price"></SPAN></TD>  
  </TR>  
</TABLE>  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1">  
   <PARAM NAME="URL" VALUE="XMLResponse.asp">  
</OBJECT>  
  
</BODY>  
</HTML>  
```  
  
 Default.htm ファイルを閉じて XMLResponse.asp が保存されている同じフォルダーに保存します。 Internet Explorer 4.0 を使用するか、後で、URL http:// を開いて*sqlserver*/XMLPersist/default.htm し、結果を確認します。 データは、バインドされた DHTML テーブルに表示されます。 これで開く URL http:// *sqlserver* /XMLPersist/XMLResponse.asp し、結果を確認します。 XML が表示されます。  
  
## <a name="see-also"></a>参照  
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)   
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
