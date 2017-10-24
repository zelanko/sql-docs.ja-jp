---
title: "ADO イベントのインスタンス化: Visual Basic |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56510bc99d0a6a7c20d18b93b22a60decdfcc2e2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="ado-event-instantiation-visual-basic"></a>Visual Basic の ADO イベントのインスタンス化します。
Microsoft® Visual Basic® で ADO イベントを処理するために、モジュール レベル変数を使用してを宣言する必要があります、 **WithEvents**キーワード。 変数は、クラス モジュールの一部としてのみ宣言することができ、モジュール レベルで宣言する必要があります。 これはないよう、ただし、として制限の厳しいため Visual Basic**フォーム**オブジェクトはクラスでもします。 使用して変数を宣言する ADO イベントを処理する最も簡単な方法は、 **WithEvents**です。 次の例のハンドル、 **ConnectComplete**イベントを**接続**オブジェクト。  
  
```  
' BeginEventExampleVB02  
Dim WithEvents connEvent As Connection  
Attribute connEvent.VB_VarHelpID = -1  
  
Private Sub Form_Load()  
Dim strConn As String  
  
   ' Create a new object with event  
   ' handling enabled.  
   strConn = "Provider=sqloledb;" & _  
      "Data Source=MyServer;" & _  
      "Initial Catalog=Northwind;" & _  
      "Integrated Security=SSPI;"  
   Set connEvent = New ADODB.Connection  
   connEvent.Open strConn  
End Sub  
  
Private Sub connEvent_ConnectComplete(ByVal pError As ADODB.Error, _  
    adStatus As ADODB.EventStatusEnum, _  
    ByVal pConnection As ADODB.Connection)  
Dim strMsg As String  
  
   If adStatus = adStatusErrorsOccurred Then  
      Select Case pError.Number  
         Case adErrOperationCancelled  
            ' The operation was cancelled in the  
            ' Will event. Notify the user and exit.  
            strMsg = "I'm sorry you can't connect right now." & vbCrLf  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
         Case Else  
            strMsg = "Error " & Format(pError.Number) & vbCrLf  
            strMsg = strMsg & pError.Description  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
      End Select  
   End If  
   frmWait.btnOK.Enabled = True  
End Sub  
' EndEventExampleVB02  
```  
  
 **接続**で宣言されているオブジェクト、**フォーム**レベルを使用して、 **WithEvents**イベント処理を有効にするキーワードです。 Form_Load イベント ハンドラーが新しいを割り当てることによって、オブジェクトを実際に作成**接続**オブジェクトを*connEvent*し、その接続を開きます。 もちろん、実際のアプリケーションでは、ここに表示されている Form_Load イベント ハンドラーでより多くの処理は実行します。

