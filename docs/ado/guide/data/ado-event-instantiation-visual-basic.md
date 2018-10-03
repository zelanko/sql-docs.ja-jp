---
title: 'ADO イベントのインスタンス化: Visual Basic |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0223d4d4346f26ff9339fce3cbc43be9bfcbe82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772480"
---
# <a name="ado-event-instantiation-visual-basic"></a>ADO イベントのインスタンス化: Visual Basic
Microsoft® Visual Basic® での ADO のイベントを処理するために、モジュール レベル変数を使用してを宣言する必要があります、 **WithEvents**キーワード。 変数は、クラス モジュールの一部としてのみ宣言することができます、モジュール レベルで宣言する必要があります。 ようですが、制限はありません Visual Basic**フォーム**オブジェクトはクラスでも。 ADO イベントを処理する最も簡単な方法は、使用して変数を宣言する**WithEvents**します。 次の例のハンドル、 **ConnectComplete**イベントを**接続**オブジェクト。  
  
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
  
 **接続**で宣言されているオブジェクト、**フォーム**レベルを使用して、 **WithEvents**イベント処理を有効にするキーワード。 実際には、Form_Load イベント ハンドラーは新しいを割り当てることでオブジェクトを作成**接続**オブジェクトを*connEvent*してから、接続を開きます。 もちろん、実際のアプリケーションは、次に示しますよりも Form_Load イベント ハンドラーでより多くの処理を行います。
