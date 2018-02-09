---
title: "プロバイダー エラー |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors collection [ADO]
- provider errors [ADO]
- event-related errors [ADO]
- errors [ADO], provider
- Error object [ADO], provider errors
ms.assetid: cc7d6ff9-2034-45c6-9d61-90b177010054
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ce82243dda984375bef3a1630650ff27c68dd09
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="provider-errors"></a>プロバイダー エラー
プロバイダー エラーが発生したときに-2147467259 の実行時エラーが返されます。 このエラーが表示されたら、確認、**エラー**のアクティブなコレクション**接続**問題の概要を説明する 1 つ以上のエラーを含むオブジェクト。  
  
## <a name="the-ado-errors-collection"></a>ADO Errors コレクション  
 ADO が経由でエラー オブジェクトのコレクションを公開する ADO の特定の操作が複数のプロバイダー エラーを生成できるため、**接続**オブジェクト。 このコレクションが含まれていないオブジェクトには操作が正常に完了した、1 つ以上含まれている場合**エラー**問題が発生したかどうか、およびプロバイダーには、1 つまたは複数のエラーが発生したオブジェクトします。 エラーの原因を特定するには、各エラー オブジェクトを確認します。  
  
 発生したエラーの処理が完了したら、すぐを呼び出してコレクションをクリアすることができます、**オフ**メソッドです。 明示的にオフに特に重要である、**エラー**コレクションを呼び出す前に、**再同期**、 **UpdateBatch**、または**CancelBatch**メソッドを**レコード セット**オブジェクト、**開く**メソッドを**接続**オブジェクト、または設定、**フィルター**プロパティを**Recordset**オブジェクト。 コレクションを明示的にオフにすることを確認することができます、**エラー**コレクション内のオブジェクトが残っていない以前の操作です。  
  
 一部の操作は、エラーだけでなく警告を生成できます。 警告がによっても表されます**エラー**内のオブジェクト、**エラー**コレクション。 プロバイダーが、警告をコレクションに追加すると、実行時エラーは生成されません。 チェック、**カウント**のプロパティ、**エラー**警告が特定の操作によって生成されたかどうかを確認します。 カウントが 1 つである場合、以上、**エラー**オブジェクトがコレクションに追加されました。 あることを確認するようになったら、**エラー**コレクションには、エラーまたは警告が含まれています、コレクションを反復処理およびそれぞれに関する情報を取得できます**エラー**含まれているオブジェクト。 次の短い Visual Basic の例では、これを示しています。  
  
```  
' BeginErrorHandlingVB02  
Private Function DeleteCustomer(ByVal CompanyName As String) As Long  
    On Error GoTo DeleteCustomerError  
  
    rst.Find "CompanyName='" & CompanyName & "'"  
DeleteCustomerError:  
Dim objError As ADODB.Error  
Dim strError As String  
  
    If cnn.Errors.Count > 0 Then  
        For Each objError In cnn.Errors  
            strError = strError & "Error #" & objError.Number & _  
                " " & objError.Description & vbCrLf & _  
                "NativeError: " & objError.NativeError & vbCrLf & _  
                "SQLState: " & objError.SQLState & vbCrLf & _  
                "Reported by: " & objError.Source & vbCrLf & _  
                "Help file: " & objError.HelpFile & vbCrLf & _  
                "Help Context ID: " & objError.HelpContext  
        Next  
        MsgBox strError  
    End If  
End Function  
' EndErrorHandlingVB02  
```  
  
 エラー処理ルーチンでは、**各**ループ内の各オブジェクトを検査する、**エラー**コレクション。 この例では、表示用のメッセージを累積します。 、各エラーに対して適切なタスクを実行するコードを記述する作業用のプログラムでは、すべてを閉じるなどのファイルを開くし、所定の手順で、プログラムをシャット ダウンします。  
  
## <a name="the-error-object"></a>Error オブジェクト  
 確認するには、**エラー**オブジェクトのどのようなエラーが発生したかを判断できより重要なアプリケーションまたはオブジェクト エラーが発生します。 **エラー**オブジェクトには、次のプロパティ。  
  
|プロパティ名|Description|  
|-------------------|-----------------|  
|**Description**|発生したエラーの説明文です。|  
|**HelpContext、ヘルプ ファイル**|発生したエラーの説明が含まれているヘルプ トピックとヘルプ ファイルを参照します。|  
|**NativeError**|プロバイダー固有のエラー番号。|  
|**Number**|数を表す長整数 (に一覧表示、 **ErrorValueEnum**) のエラーが発生します。|  
|**ソース**|オブジェクトまたはエラーが発生したアプリケーションの名前を示します。|  
|**SQLState**|プロバイダーを返す SQL ステートメントの処理中に 5 文字のエラー コード。|  
  
 ADO**エラー**オブジェクトは、標準の Visual Basic によく似た**Err**オブジェクト。 そのプロパティでは、発生したエラーについて説明します。 エラーの数、2 つの関連する種類の情報が表示されます。 **以下**プロパティには、エラー番号が含まれています。 プロバイダーを使用しています。 前の例では、プロバイダーは、Microsoft OLE DB Provider for SQL Server, ので**以下**は SQL Server に固有のエラーが含まれます。 **SQLState**プロパティは、SQL ステートメントでエラーを説明する 5 文字コード。  
  
## <a name="event-related-errors"></a>イベントに関連するエラー  
 **エラー**イベントに関連するエラーが発生したときにも、オブジェクトが使用されます。 チェックして、ADO イベントを発生させたプロセスでエラーが発生するかどうかを決定できます、**エラー**イベント パラメーターとして渡されるオブジェクト。  
  
 イベントの原因となる操作が正常に行われる場合、 *adStatus*イベント ハンドラーのパラメーターに設定されます*adStatusOK*です。 その一方で、イベントを発生させた操作が成功しなかった場合、 *adStatus*にパラメーターが設定されている*adStatusErrorsOccurred*です。 その場合は、 *pError*パラメーターが含まれます、**エラー**エラーを説明するオブジェクト。
