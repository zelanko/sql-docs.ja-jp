---
title: '手順 6: 変更は、サーバー (RDS チュートリアル) に送信されます |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d79fb88ba9371d1767561c7190818c135fd0a03
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680270"
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>手順 6: 変更がサーバーに送信される (RDS チュートリアル)
場合、 **Recordset**オブジェクトが編集、変更 (つまり、追加、変更、または削除された行) をサーバーに送信できます。  
  
> [!NOTE]
>  RDS の既定の動作は、ADO オブジェクトと Microsoft OLE DB リモート プロバイダーに暗黙的に起動できます。 クエリが返すことができます**レコード セット**秒、および編集された**レコード セット**s は、データ ソースを更新できます。 このチュートリアルでは、ADO のオブジェクトでは、RDS は呼び出しませんがどのようにした場合の外観になります。  
  
```  
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=http://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **パート A**こののみに使用した場合の想定、 [rds.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)ことと、 **Recordset**オブジェクトが関連付けられているようになりました、 **rds.DataControl**します。 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)メソッドが変更されたデータ ソースを更新、 **Recordset**オブジェクトの場合、 [Server](../../../ado/reference/rds-api/server-property-rds.md)と[Connect](../../../ado/reference/rds-api/connect-property-rds.md)プロパティが設定されています。  
  
```  
Sub RDSTutorial6A()  
Dim DC as New RDS.DataControl  
Dim RS as ADODB.Recordset  
DC. = "http://yourServer"  
DC. = "DSN=Pubs"  
DC. = "SELECT * FROM Authors"  
DC.  
...  
Set RS = DC.  
   ' Edit the Recordset.  
...  
DC.  
...  
```  
  
 **パート B**代わりに、使用して、サーバーを更新することが、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト、接続を指定して、**レコード セット**オブジェクト。  
  
```  
Sub RDSTutorial6B()  
Dim DS As New RDS.DataSpace  
Dim RS As ADODB.Recordset  
Dim DC As New RDS.DataControl  
Dim DF As Object  
Dim blnStatus As Boolean  
Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")  
DC. = RS    ' Visual controls can now bind to DC.  
    ' Edit the Recordset.  
blnStatus = DF."DSN=Pubs", RS  
End Sub  
```  
  
 **これは、チュートリアルの最後です。**  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="see-also"></a>参照  
 [Microsoft OLE DB のリモート処理 Provider (サービス プロバイダーの ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
