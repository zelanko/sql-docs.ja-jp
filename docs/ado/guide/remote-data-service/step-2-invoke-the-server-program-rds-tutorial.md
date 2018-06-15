---
title: '手順 2: 呼び出すサーバー プログラム (RDS チュートリアル) |Microsoft ドキュメント'
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
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b736bb5e6cdb7f35d9cdcc5f39f060cbcf1b64b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274591"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>手順 2: 呼び出すサーバー プログラム (RDS チュートリアル)
クライアントでメソッドを呼び出すときに*プロキシ*サーバー上の実際のプログラムは、メソッドを実行します。 このステップでは、サーバーでクエリを実行します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 **パート A**を使用していない場合[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)でこのチュートリアルでは、この手順を実行する最も便利な方法は使用すること、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。 **.Rds ですDataControl**クエリを発行するこの手順により、プロキシの作成の前の手順を結合します。  
  
 設定、 **.rds ですDataControl**オブジェクト[サーバー](../../../ado/reference/rds-api/server-property-rds.md)ここでサーバーのプログラムをインスタンス化は; を使用するには、[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティをデータ ソースにアクセスする接続文字列を指定して[SQL](../../../ado/reference/rds-api/sql-property.md)プロパティ、クエリ コマンド テキストを指定します。 発行し、[更新](../../../ado/reference/rds-api/refresh-method-rds.md)が原因でデータ ソースへの接続、クエリで指定された行を取得するサーバーのプログラムを返すメソッド、**レコード セット**クライアント オブジェクトです。  
  
 このチュートリアルでは使用しません、 **.rds ですDataControl**が、これと同じ場合なります。  
  
```  
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "http://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 チュートリアルを呼び出す RDS ADO オブジェクトがどのなります場合は、これは。  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=http://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **パート B**この手順を実行した場合の一般的な方法では、呼び出し、 **RDSServer.DataFactory**オブジェクト[クエリ](../../../ado/reference/rds-api/query-method-rds.md)メソッドです。 そのメソッドでは、データ ソースへの接続に使用される、接続文字列と、データ ソースから返される行を指定するために使用されるコマンド テキストを使用します。  
  
 このチュートリアルでは、 **DataFactory**オブジェクト**クエリ**メソッド。  
  
```  
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>参照  
 [手順 3: サーバーの取得レコード セット (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
