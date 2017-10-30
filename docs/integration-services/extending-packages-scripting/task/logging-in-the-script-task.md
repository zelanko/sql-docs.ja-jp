---
title: "スクリプト タスクでログ記録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 98859dafe0b023954f10239fe11e8b76f36ab28b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-task"></a>スクリプト タスクでのログ記録
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのログ記録を使用すると、実行の進行状況、結果、問題点などに関する詳細な情報を、あらかじめ定義されたイベントまたはユーザー定義のメッセージとして記録し、後で分析することができます。 スクリプト タスクで使用できる、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>のメソッド、 **Dts**ユーザー定義データを記録するオブジェクト。 ログ記録が有効になっている場合、 **ScriptTaskLogEntry**のログオン イベントが選択されている、**詳細**のタブ、 **SSIS ログの構成**ダイアログ ボックスで、1 回の呼び出し、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>メソッドは、タスク用に構成されたすべてのログ プロバイダーに、イベント情報を格納します。  
  
> [!NOTE]  
>  ログ記録はスクリプト タスクから直接実行できますが、ログ記録ではなくイベントを実装することを検討する必要があります。 イベントを使用すると、イベント メッセージのログ記録を有効にできるだけでなく、既定またはユーザー定義のイベント ハンドラーによってイベントに応答することもできます。  
  
 ログ記録の詳細については、次を参照してください。 [Integration Services & #40 です。SSIS &#41;ログ記録](../../../integration-services/performance/integration-services-ssis-logging.md)です。  
  
## <a name="logging-example"></a>ログ記録の例  
 次の例は、処理された行数を表す値をログに記録する、スクリプト タスクのログ記録を示します。  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 }  
  
## <a name="external-resources"></a>外部リソース  
  
-   ブログ エントリ「 [Integration Services タスクのカスタム イベントをログ記録](http://go.microsoft.com/fwlink/?LinkId=165644)、dougbert.com  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;ログ記録](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  

