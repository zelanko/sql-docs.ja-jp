---
title: "スクリプト タスクによるパフォーマンス カウンターの監視 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: fd733f7d2fdf9c5d1181df6e7856d729e9a58026
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="monitoring-performance-counters-with-the-script-task"></a>スクリプト タスクによるパフォーマンス カウンターの監視
  システム管理者は、大容量のデータ上で複雑な変換を実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのパフォーマンスを監視する必要が生じる場合があります。 **System.Diagnostics**の名前空間、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を既存のパフォーマンス カウンターを使用して、独自のパフォーマンス カウンターを作成するためのクラスを提供します。  
  
 パフォーマンス カウンターはアプリケーションのパフォーマンス情報を格納するので、これを使用して、時間経過に伴うソフトウェアのパフォーマンスを分析できます。 パフォーマンス カウンター ローカルでもリモートでもを使用して監視する、**パフォーマンス モニター**ツールです。 パフォーマンス カウンターの値を変数に格納して、後でパッケージ内で制御フローを分岐するために使用できます。  
  
 パフォーマンス カウンターを使用する代わりに、上げることができます、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>を通じてイベントを<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>のプロパティ、 **Dts**オブジェクト。 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> イベントは、進捗状況および完了した割合に関する情報を、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムに返します。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>Description  
 次の例では、カスタム パフォーマンス カウンターを作成し、カウンターの値を増やします。 最初に、パフォーマンス カウンターが既に存在しているかどうかを判別します。 かどうか、パフォーマンス カウンターが作成されていない、スクリプトの呼び出し、**作成**のメソッド、 **PerformanceCounterCategory**オブジェクトを作成します。 パフォーマンス カウンターが作成されたら、スクリプトはそのカウンターの値を増やします。 最後に、次に例を呼び出し元のベスト プラクティス、**閉じる**不要になったときに、パフォーマンス カウンターのメソッドです。  
  
> [!NOTE]  
>  パフォーマンス カウンター カテゴリとパフォーマンス カウンターを新しく作成するには、管理権限が必要です。 また、新しいカテゴリとカウンターは、作成後もコンピューターに保存されます。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
-   使用して、 **Imports**をインポートするようにコード内のステートメント、 **System.Diagnostics**名前空間。  
  
### <a name="example-code"></a>コード例  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  

