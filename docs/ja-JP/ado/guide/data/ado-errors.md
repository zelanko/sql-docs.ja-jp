---
title: ADO エラー |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO]
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59e72fde07afa53b5cf3f4bf38e1227cfe316865
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-run-time-errors"></a>ADO の実行時エラー
ADO エラーは、プログラムを実行時エラーとして報告されます。 トラップして、それらの処理に使用するプログラミング言語のエラー トラップ メカニズムを使用できます。 たとえば、Visual Basic を使用して、 **On Error**ステートメントです。 Visual c で ADO ライブラリへのアクセスに使用するメソッドに依存します。 #Import を使用して、 **try catch**ブロックします。 それ以外の場合、C++ プログラマは、明示的に呼び出すことによって、エラー オブジェクトを取得する必要があります。 **GetErrorInfo**です。 次の Visual Basic sub プロシージャでは、ADO エラーをトラップを示しています。

```
' BeginErrorHandlingVB01
Private Sub Form_Load()
' Turn on error handling
On Error GoTo FormLoadError

'Open the database and the recordset for processing.
'
Dim strCnn As String
strCnn = "Provider=sqloledb;" & _
    "Data Source=a-iresmi2000;" & _
    "Initial Catalog=Northwind;Integrated Security=SSPI"

' cnn is a Public Connection Object because
' it was defined WithEvents
Set cnn = New ADODB.Connection
cnn.Open strCnn

' The next line of code intentionally causes
' an error by trying to open a connection
' that has already been opened.
cnn.Open strCnn

' rst is a Public Recordset because it
' was defined WithEvents
Set rst = New ADODB.Recordset
rst.Open "Customers", cnn

Exit Sub

' Error handler
FormLoadError:
    Dim strErr As String
    Select Case Err
        Case adErrObjectOpen
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            strErr = strErr & "Error reported by: " & Err.Source & vbCrLf
            strErr = strErr & "Help File: " & Err.HelpFile & vbCrLf
            strErr = strErr & "Topic ID: " & Err.HelpContext
            MsgBox strErr
            Debug.Print strErr
            Err.Clear
            Resume Next
        ' If some other error occurs that
        ' has nothing to do with ADO, show
        ' the number and description and exit.
        Case Else
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            MsgBox strErr
            Debug.Print strErr
            Unload Me
    End Select
End Sub
' EndErrorHandlingVB01
```

 これは、 **Form_Load**イベント プロシージャが同じを開こうとしてエラーを意図的に作成**接続**オブジェクトの 2 回クリックします。 2 番目の時間、**開く**メソッドが呼び出されると、エラー ハンドラーがアクティブにします。 ここでは、エラーは型**adErrObjectOpen**ので、エラー ハンドラーでは、プログラムの実行を再開する前に、次のメッセージが表示されます。

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 エラー メッセージには、Visual Basic によって提供される情報の各部分**Err**以外のオブジェクト、 **LastDLLError**値で、ここでは適用されません。 エラー番号は、エラーの種類を示します。 説明をたくないエラーを処理する場合に便利です。 単にユーザーに渡すことができます。 すべてのエラーが予想されることはできませんが、通常、アプリケーション用にカスタマイズされたメッセージを使用するが、何か不具合についてを説明します。 サンプル コードでエラーがによって報告された、**接続**オブジェクト。 オブジェクトの型またはプログラムの ID は、ここを参照してください: 変数名ではありません。

> [!NOTE]
>  Visual Basic **Err**オブジェクトには、最新のエラーに関する情報にはのみが含まれています。 ADO**エラー**のコレクション、**接続**オブジェクトは、1 つを含む**エラー** ADO の最新の操作によって発生したエラーごとにオブジェクト。 使用して、**エラー**コレクションではなく、 **Err**複数のエラーを処理するオブジェクト。 詳細については、**エラー** 、コレクションを参照してください[、プロバイダー エラー](../../../ado/guide/data/provider-errors.md)です。 ただし、有効ながある場合**接続**オブジェクト、 **Err**オブジェクトは ADO エラーに関する情報の唯一のソース。

 操作の種類は、ADO のエラーが発生する可能性がありますか。 ADO の一般的なエラーにはなどが含まれますなどのオブジェクトを開いて、**接続**または**Recordset**データを更新しようとしています。 または、メソッドや、プロバイダーでサポートされていないプロパティを呼び出すことです。

 OLE DB エラーは、実行時のエラーとしてアプリケーションに渡すこともできます、**エラー**コレクション。

 次のトピックでは、ADO のエラーの詳細についてを説明します。

-   [ADO エラー リファレンス](../../../ado/guide/data/ado-error-reference.md)
