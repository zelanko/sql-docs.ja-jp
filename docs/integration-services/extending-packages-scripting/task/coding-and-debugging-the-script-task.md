---
title: "コーディングおよびスクリプト タスクのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
caps.latest.revision: 81
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8c706fc1db3e31130a7754b9e4c3d16f9a13eaf4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-task"></a>スクリプト タスクのコーディングおよびデバッグ
  タスクのスクリプトを構成した後、**スクリプト タスク エディター**、スクリプト タスク開発環境で、カスタム コードを記述します。  
  
## <a name="script-task-development-environment"></a>スクリプト タスク開発環境  
 スクリプト タスクを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) スクリプト自体の開発環境として。  
  
 スクリプト コードは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# で記述されます。 スクリプト言語の設定を指定する、 **[scriptlanguage]**プロパティに、**スクリプト タスク エディター**です。 その他のプログラミング言語を使用する場合は、選択した言語でカスタム アセンブリを作成し、スクリプト タスク内のコードからその機能を呼び出すことができます。  
  
 スクリプト タスクで作成したスクリプトは、パッケージ定義に格納されます。 スクリプト ファイルが別途存在するわけではありません。 したがって、スクリプト タスクを使用してもパッケージの配置には影響しません。  
  
> [!NOTE]  
>  パッケージをデザインしてスクリプトをデバッグする際、スクリプト コードは一時的にプロジェクト ファイルに書き込まれます。 機密情報をファイルに保存することはセキュリティ上危険であるため、パスワードなどの重要な情報はスクリプト コードに書き込まないことをお勧めします。  
  
 既定では、 **Option Strict** IDE では無効です。  
  
## <a name="script-task-project-structure"></a>スクリプト タスク プロジェクトの構造  
 スクリプト タスクに格納されているスクリプトを作成または変更する場合、VSTA は空の新しいプロジェクトを開くか、または既存のプロジェクトを再度開きます。 この VSTA プロジェクトを作成しても、パッケージの配置に影響はありません。このプロジェクトはパッケージ ファイル内部に保存され、スクリプト タスクは追加ファイルを作成しないためです。  
  
### <a name="project-items-and-classes-in-the-script-task-project"></a>スクリプト タスク プロジェクトのプロジェクト アイテムおよびクラス  
 既定では、VSTA プロジェクト エクスプ ローラー ウィンドウに表示されるスクリプト タスク プロジェクトに 1 つの項目が含まれています**ScriptMain**です。 **ScriptMain**項目、さらもという名前の単一のクラスを含む**ScriptMain**です。 このクラスのコード要素は、スクリプト タスクに対して選択したプログラミング言語に応じて異なります。  
  
-   スクリプト タスクを構成するとき、[!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)]プログラミング言語、 **ScriptMain**クラスにパブリック サブルーチン**Main**です。 **ScriptMain.Main**サブルーチンは、スクリプト タスクを実行するときにランタイムによって呼び出されるメソッド。  
  
     既定では、コード内にのみ、 **Main**行である、新しいスクリプトのサブルーチン`Dts.TaskResult = ScriptResults.Success`です。 この行は、タスクの処理が正常に実行されたことをランタイムに通知します。 **Dts.TaskResult**プロパティは、後ほど[スクリプト タスクから結果を返す](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)です。  
  
-   スクリプト タスクが構成されている場合、Visual c# のプログラミング言語、 **ScriptMain**クラス、パブリック メソッドを持つ、 **Main**です。 このメソッドは、スクリプト タスク実行時に呼び出されます。  
  
     既定では、 **Main**メソッドには、行が含まれています。`Dts.TaskResult = (int)ScriptResults.Success`です。 この行は、タスクの処理が正常に実行されたことをランタイムに通知します。  
  
 **ScriptMain**項目が以外のクラスを含めることができます、 **ScriptMain**クラスです。 クラスは、そのクラスが含まれているスクリプト タスクでのみ使用できます。  
  
 既定では、 **ScriptMain**プロジェクト項目には、次の自動生成されたコードが含まれています。 コード テンプレートでも、スクリプト タスクの概要、および、変数、イベント、接続など、SSIS オブジェクトを取得および操作する方法に関する追加情報を提供します。  
  
```vb  
' Microsoft SQL Server Integration Services Script Task  
' Write scripts using Microsoft Visual Basic 2008.  
' The ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy  
  
<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _  
Partial Class ScriptMain  
  
Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup  
  
End Sub  
  
Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown  
Try  
' Unlock variables from the read-only and read-write variable collection properties  
If (Dts.Variables.Count <> 0) Then  
Dts.Variables.Unlock()  
End If  
Catch ex As Exception  
        End Try  
End Sub  
  
Enum ScriptResults  
Success = DTSExecResult.Success  
Failure = DTSExecResult.Failure  
End Enum  
  
' The execution engine calls this method when the task executes.  
' To access the object model, use the Dts property. Connections, variables, events,  
' and logging features are available as members of the Dts property as shown in the following examples.  
'  
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value  
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)  
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)  
'  
' To use the connections collection use something like the following:  
' ConnectionManager cm = Dts.Connections.Add("OLEDB")  
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"  
'  
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
'   
' To open Help, press F1.  
  
Public Sub Main()  
'  
' Add your code here  
'  
Dts.TaskResult = ScriptResults.Success  
End Sub  
  
End Class  
```  
  
```csharp  
/*  
   Microsoft SQL Server Integration Services Script Task  
   Write scripts using Microsoft Visual C# 2008.  
   The ScriptMain is the entry point class of the script.  
*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;  
using System.Windows.Forms;  
  
namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj  
{  
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]  
    public partial class ScriptMain  
    {  
        private void ScriptMain_Startup(object sender, EventArgs e)  
        {  
  
        }  
  
        private void ScriptMain_Shutdown(object sender, EventArgs e)  
        {  
            try  
            {  
                // Unlock variables from the read-only and read-write variable collection properties  
                if (Dts.Variables.Count != 0)  
                {  
                    Dts.Variables.Unlock();  
                }  
            }  
            catch  
            {  
            }  
        }  
  
        #region VSTA generated code  
        private void InternalStartup()  
        {  
            this.Startup += new System.EventHandler(ScriptMain_Startup);  
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);  
        }  
        enum ScriptResults  
        {  
            Success = DTSExecResult.Success,  
            Failure = DTSExecResult.Failure  
        };  
  
        #endregion  
  
        /*  
The execution engine calls this method when the task executes.  
To access the object model, use the Dts property. Connections, variables, events,  
and logging features are available as members of the Dts property as shown in the following examples.  
  
To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;  
To post a log entry, call Dts.Log("This is my log text", 999, null);  
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);  
  
To use the connections collection use something like the following:  
ConnectionManager cm = Dts.Connections.Add("OLEDB");  
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";  
  
Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
  
To open Help, press F1.  
*/  
  
        public void Main()  
        {  
            // TODO: Add your code here  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
    }  
```  
  
### <a name="additional-project-items-in-the-script-task-project"></a>スクリプト タスク プロジェクトのその他のプロジェクト アイテム  
 スクリプト タスク プロジェクトは、既定値以外のアイテムを含めることができます**ScriptMain**項目。 プロジェクトには、クラス、モジュール、およびコード ファイルを追加できます。 また、フォルダーを使用してアイテムのグループを整理できます。 追加したすべてのアイテムは、パッケージ内部に保存されます。  
  
### <a name="references-in-the-script-task-project"></a>スクリプト タスク プロジェクトの参照  
 マネージ アセンブリへの参照を追加するには、スクリプト タスクでプロジェクトを右クリックして**プロジェクト エクスプ ローラー**、クリックして**参照の追加**です。 詳細については、次を参照してください。[スクリプト ソリューションでその他のアセンブリを参照している](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)です。  
  
> [!NOTE]  
>  プロジェクト参照を表示するには、VSTA IDE 内で**クラス ビュー**または**プロジェクト エクスプ ローラー**です。 これらのウィンドウからのいずれかを開く、**ビュー**メニュー。 新しい参照を追加することができます、**プロジェクト** メニューから**プロジェクト エクスプ ローラー**、またはから**クラス ビュー**です。  
  
## <a name="interacting-with-the-package-in-the-script-task"></a>スクリプト タスク内でのパッケージとの対話  
 スクリプト タスクを使用して、グローバル**Dts**インスタンスであるオブジェクトの<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>クラス、およびそのメンバーを格納しているパッケージとの対話、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]ランタイム。  
  
 次の表に、プリンシパルのパブリック メンバーの<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>はグローバルで、スクリプト タスク コードに公開するクラス**Dts**オブジェクト。 このセクションのトピックでは、これらのメンバーを使用する方法についてさらに詳しく説明します。  
  
|メンバー|用途|  
|------------|-------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|パッケージで定義されている接続マネージャーへのアクセスを提供します。|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|スクリプト タスクでエラー、警告、および情報メッセージを発生させるためのイベント インターフェイスを提供します。|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|1 つのオブジェクトをランタイムに返す簡単な方法を示します (に加え、 **TaskResult**) ワークフローの分岐を使用できます。|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|タスクの進行状況や結果などの情報を、有効なログ プロバイダーに記録します。|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|タスクの成功または失敗をレポートします。|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|タスクのコンテナーを実行しているトランザクションが存在する場合、それを提供します。|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|含まれる変数にアクセスできるように、 **ReadOnlyVariables**と**ReadWriteVariables**タスク、スクリプト内で使用するためのプロパティです。|  
  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> クラスには、使用しない可能性のあるパブリック メンバーも含まれています。  
  
|メンバー|Description|  
|------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|変数にアクセスするには、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティの方が便利です。 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> も使用できますが、読み書きする変数をロックおよびロック解除するためのメソッドを明示的に呼び出す必要があります。 スクリプト タスクは、使用する場合のロック セマンティクスを処理、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>プロパティです。|  
  
## <a name="debugging-the-script-task"></a>スクリプト タスクのデバッグ  
 スクリプト タスクのコードをデバッグするには、コードに少なくとも 1 つのブレークポイントを設定し、VSTA IDE を閉じて [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。 パッケージが実行されてスクリプト タスクが開始されると、VSTA IDE が再度開き、読み取り専用モードでコードが表示されます。 実行によりブレークポイントに到達したら、変数の値の検証や、残りのコードのステップ スルーができます。  
  
> [!WARNING]  
>  64 ビット モードでパッケージを実行すると、スクリプト タスクをデバッグすることができます。  
  
> [!NOTE]  
>  スクリプト タスクをデバッグするには、パッケージを実行する必要があります。 個別のタスクのみを実行する場合、スクリプト タスク コードのブレークポイントは無視されます。  
  
> [!NOTE]  
>  パッケージ実行タスクから実行されている子パッケージの一部としてスクリプト タスクを実行する場合は、スクリプト タスクをデバッグできません。 このような状況では、子パッケージにスクリプト タスクで設定したブレークポイントが無視されます。 子パッケージを単独で実行することにより、通常どおりパッケージをデバッグできます。  
  
> [!NOTE]  
>  複数のスクリプト タスクが含まれるパッケージをデバッグする場合、デバッガーによってデバッグされるスクリプト タスクは 1 つです。 Foreach ループまたは For ループ コンテナーの場合と同様に、デバッガーが完了した場合、システムは別のスクリプト タスクをデバッグできます。  
  
## <a name="external-resources"></a>外部リソース  
  
-   ブログ エントリ「 [VSTA のセットアップと構成に関する問題の SSIS 2008 および R2 インストール](http://go.microsoft.com/fwlink/?LinkId=215661)、blogs.msdn.com です。  
  
## <a name="see-also"></a>参照  
 [スクリプティング ソリューションの他のアセンブリを参照します。](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)   
 [スクリプト タスク エディターで、スクリプト タスクを構成します。](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
  
  

