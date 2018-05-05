---
title: '手順 6: 変更は、サーバー (RDS チュートリアル) に送信される |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0537d8d05553b4e50861bda664d2cdc53489cb82
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>手順 6: 変更は、サーバー (RDS チュートリアル) に送信されます。
場合、 **Recordset**オブジェクトを編集、変更 (つまり、追加、変更、または削除された行) をサーバーに送信できます。  
  
> [!NOTE]
>  RDS の既定の動作は、ADO オブジェクトと、Microsoft OLE DB リモート プロバイダーで暗黙的に呼び出すことをがします。 クエリが返すことができます**Recordset**秒、および編集された**レコード セット**s は、データ ソースを更新できます。 このチュートリアルでは、ADO オブジェクトでは、RDS は呼び出しませんが、これと同じ場合なります。  
  
```  
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=http://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **パート A**こののみに使用した場合に想定、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)ことと、 **Recordset**に関連付けられたオブジェクトが現在、 **.rds ですDataControl**です。 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)メソッドで変更されたデータ ソースを更新する、 **Recordset**オブジェクトの場合、[サーバー](../../../ado/reference/rds-api/server-property-rds.md)と[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティが設定されています。  
  
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
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="see-also"></a>参照  
 [Microsoft OLE DB リモート プロバイダー (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
