---
title: "検出して、競合を解決する |Microsoft ドキュメント"
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
- conflicts [ADO], detecting and resolving
- ADO, detecting and resolving conflicts
ms.assetid: b28fdd26-c1a4-40ce-a700-2b0c9d201514
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00a768c70b1945bc573aaca6c48841e665780081
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="detecting-and-resolving-conflicts"></a>競合の検出および解決
イミディ エイト モードで、レコード セットを処理する場合は、同時実行の問題が発生する可能性は大幅に小さくします。 その一方で、アプリケーションでは、バッチ モードの更新を使用する場合は、ある可能性があります良い機会同じレコードを編集する別のユーザーによって行われた変更が保存される前にあるユーザーが、レコードを変更します。 競合を適切に処理するアプリケーションは、このような場合でします。 最後に更新プログラムをサーバーに送信した人物「優先します」の方がある可能性があります。 または、更新プログラムの優先順位が 2 つの競合する値のいずれかで彼を提供することで決定する、最新のユーザーを許可することができます。  
  
 どのような場合は、ADO では、これらの種類の競合を処理するフィールド オブジェクトの UnderlyingValue および OriginalValue プロパティを提供します。 組み合わせでこれらのプロパティを使用して、再同期メソッドと、レコード セットのフィルター プロパティを使用します。  
  
## <a name="remarks"></a>解説  
 ADO では、バッチ更新中に競合が検出されると、警告をエラー コレクションに追加されます。 そのため、常に確認してくださいエラー BatchUpdate を呼び出すし、それらが見つかった場合は、競合が発生していることを前提をテストを開始した後にすぐに。 最初の手順では、競合するレコード セット等しいかどうかのフィルター プロパティを設定します。 これは制限が競合するレコードだけをレコード セットに表示されます。 RecordCount プロパティがこの手順の後に 0 に等しい場合は、競合以外のものによってエラーが発生しましたがわかります。  
  
 BatchUpdate を呼び出すと、ADO とプロバイダーは、データ ソースで更新プログラムを実行する SQL ステートメントを生成します。 特定のデータ ソースに制限する WHERE 句で列の型を使用できますがあることに注意してください。  
  
 次に、adAffectGroup と処理に設定して ResyncValues 引数に設定して AffectRecords 引数を持つ、レコード セットで再同期メソッドを呼び出します。 再同期メソッドでは、基になるデータベースから現在のレコード セット オブジェクト内のデータを更新します。 AdAffectGroup を使用すると、現在のフィルターを設定すると、つまり、競合するレコードのみで表示されているレコードだけが、データベースと再同期するようにします。 大きなレコード セットを扱う場合は、パフォーマンスに大きな違いでしたください。 ResyncValues 引数を処理に設定して、再同期を呼び出すときで UnderlyingValue プロパティがデータベースから (競合) の値に含まれる、Value プロパティが、ユーザーが入力した値を維持できるようにしてOriginalValue プロパティは、フィールド (最後の正常な UpdateBatch 呼び出しが行われた前に、の値) の元の値を保持します。 これらの値を使用して、競合を解決するには、プログラムによって、ユーザーが使用される値を選択する必要をできます。  
  
 この手法は、次のコード例に示します。 例は、意図的 UpdateBatch が呼び出される前に、基になるテーブル内の値を変更する別のレコード セットを使用して競合を作成します。  
  
```  
'BeginConflicts  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT * FROM Shippers WHERE ShipperID = 2"  
  
    'Open Rs and change a value  
    Set objRs1 = New ADODB.Recordset  
    Set objRs2 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Introduce a conflict at the db...  
    objRs2.Open strSQL, strConn, adOpenKeyset, adLockOptimistic, adCmdText  
    objRs2("Phone") = "(999) 555-9999"  
    objRs2.Update  
    objRs2.Close  
    Set objRs2 = Nothing  
  
    On Error Resume Next  
    objRs1.UpdateBatch  
  
    If objRs1.ActiveConnection.Errors.Count <> 0 Then  
        Dim intConflicts As Integer  
  
        intConflicts = 0  
  
        objRs1.Filter = adFilterConflictingRecords  
  
        intConflicts = objRs1.RecordCount  
  
        'Resync so we can see the UnderlyingValue and offer user a choice.  
        'This sample only displays all three values and resets to original.  
        objRs1.Resync adAffectGroup, adResyncUnderlyingValues  
  
        If intConflicts > 0 Then  
            strMsg = "A conflict occurred with updates for " & intConflicts & _  
                     " record(s)." & vbCrLf & "The values will be restored" & _  
                     " to their original values." & vbCrLf & vbCrLf  
  
            objRs1.MoveFirst  
            While Not objRs1.EOF  
              strMsg = strMsg & "SHIPPER = " & objRs1("CompanyName") & vbCrLf  
              strMsg = strMsg & "Value = " & objRs1("Phone").Value & vbCrLf  
              strMsg = strMsg & "UnderlyingValue = " & _  
                                 objRs1("Phone").UnderlyingValue & vbCrLf  
              strMsg = strMsg & "OriginalValue = " & _  
                                 objRs1("Phone").OriginalValue & vbCrLf  
              strMsg = strMsg & vbCrLf & "Original value has been restored."  
  
              MsgBox strMsg, vbOKOnly, _  
                    "Conflict " & objRs1.AbsolutePosition & _  
                    " of " & intConflicts  
  
              objRs1("Phone").Value = objRs1("Phone").OriginalValue  
              objRs1.MoveNext  
            Wend  
  
            objRs1.UpdateBatch adAffectGroup  
        Else  
            'Other error occurred. Minimal handling in this example.  
             strMsg = "Errors occurred during the update. " & _  
                        objRs1.ActiveConnection.Errors(0).Number & " " & _  
                        objRs1.ActiveConnection.Errors(0).Description  
        End If  
  
        On Error GoTo 0  
    End If  
  
    objRs1.MoveFirst  
    objRs1.Close  
    Set objRs1 = Nothing  
'EndConflicts  
```  
  
 競合の種類が発生したを確認または特定のフィールドの現在のレコードの Status プロパティを使用できます。  
  
 エラー処理の詳細については、次を参照してください。 [Error Handling](../../../ado/guide/data/error-handling.md)です。  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
