---
title: "RDS のチュートリアル (VBScript) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords: RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a571546fe81ce0b49efa41ad5b09a7b71b1bad3d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="rds-tutorial-vbscript"></a>RDS のチュートリアル (VBScript)
これは、Microsoft Visual Basic Scripting Edition で記述された、RDS チュートリアルです。 このチュートリアルの目的の説明は、次を参照してください。、 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 このチュートリアルでは[.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)と[.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)デザイン時に作成されます: は、次のように、オブジェクトのタグで定義される:`<OBJECT>...</OBJECT>`です。 代わりに、実行時に作成する可能性があります、 [CreateObject メソッド (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)メソッドです。 たとえば、 **.rds ですDataControl**オブジェクトは、次のように作成できませんでした。  
  
```  
Set DC = Server.CreateObject("RDS.DataControl")  
   <!-- RDS.DataControl -->  
   <OBJECT   
      ID="DC1" CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E33">  
   </OBJECT>  
  
   <!-- RDS.DataSpace -->  
   <OBJECT   
      ID="DS1" WIDTH=1 HEIGHT=1  
      CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
   </OBJECT>  
  
   <SCRIPT LANGUAGE="VBScript">  
  
   Sub RDSTutorial()  
   Dim DF1   
```  
  
## <a name="step-1--specify-a-server-program"></a>手順 1-サーバー プログラムを指定します。  
 VBScript は、VBScript をアクセスすることによってで実行されている IIS Web サーバーの名前を検出できる**Request.ServerVariables**メソッド Active Server Pages を使用できます。  
  
```  
"http://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 ただし、このチュートリアルでは、虚数部のサーバーでは、「通常」を使用します。  
  
> [!NOTE]
>  データ型に注意を払う**ByRef**引数。 VBScript では常に渡す必要がありますので、変数の型を指定することはできません、**バリアント**です。 HTTP を使用して、RDS されることができますでを起動する場合は、バリアント以外の型を必要とするメソッドに代入するバリアント型を渡す、 **.rds ですDataSpace**オブジェクト[CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md)メソッドです。 DCOM またはインプロセス サーバーを使用する場合、クライアントとサーバー側でのパラメーター型が一致する必要がありますか「の種類が一致しません」エラーが表示されます。  
  
```  
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "http://yourServer")  
```  
  
## <a name="step-2a--invoke-the-server-program-with-rdsdatacontrol"></a>手順 2 a — RDS に関するサーバーのプログラムの実行DataControl  
 この例を示すコメントだけでは、既定の動作、 **.rds ですDataControl**指定されたクエリを実行することです。  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="http://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial2A()  
   Dim RS  
   DC1.Refresh  
   Set RS = DC1.Recordset  
...  
```  
  
## <a name="step-2b--invoke-the-server-program-with-rdsserverdatafactory"></a>手順 2 b: RDSServer.DataFactory で、サーバーのプログラムの実行  
  
## <a name="step-3--server-obtains-a-recordset"></a>手順 3-サーバーは、レコード セットを取得します。  
  
## <a name="step-4--server-returns-the-recordset"></a>手順 4: サーバーは、レコード セットを返す  
  
```  
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5--datacontrol-is-made-usable-by-visual-controls"></a>手順 5-DataControl がによって行われた使用可能なビジュアル コントロール  
  
```  
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a--changes-are-sent-to-the-server-with-rdsdatacontrol"></a>手順 6: 変更 rds. を使用してサーバーに送信されますDataControl  
 この例は、コメントだけを示す方法、 **.rds ですDataControl**更新を実行します。  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="http://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial6A()  
Dim RS  
DC1.Refresh  
...  
Set RS = DC1.Recordset  
' Edit the Recordset object...  
' The SERVER and CONNECT properties are already set from Step 2A.  
Set DC1.SourceRecordset = RS  
...  
DC1.SubmitChanges  
```  
  
## <a name="step-6b--changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>手順 6: 変更 RDSServer.DataFactory を使用してサーバーに送信されます  
  
```  
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **これは、チュートリアルの最後です。**  
  
## <a name="see-also"></a>参照  
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
