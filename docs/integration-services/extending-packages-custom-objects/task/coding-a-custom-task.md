---
title: "カスタム タスクのコーディング |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- CSharp
helpviewer_keywords:
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c4fd06d10d2ecd2796d0b12707c5e34168941c7c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="coding-a-custom-task"></a>カスタム タスクのコーディング
  <xref:Microsoft.SqlServer.Dts.Runtime.Task> 基本クラスを継承するクラスを作成し、<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性をそのクラスに適用したら、基本クラスのプロパティとメソッドの実装をオーバーライドして、カスタム機能を提供する必要があります。  
  
## <a name="configuring-the-task"></a>タスクの構成  
  
### <a name="validating-the-task"></a>タスクの検証  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのデザイン中に検証機能を使用して各タスクの設定を確認できるため、すべてのエラーを実行時にのみ見つけるのではなく、無効または不適切な設定が行われた場合、すぐにその問題を確認できます。 検証の目的は、タスクの正常な実行を妨げる無効な設定または接続が、タスクに含まれているかどうかを判別することです。 これによって、パッケージに含まれるタスクは、初回から正しく実行される可能性が高くなります。  
  
 使用して検証を実装することができます、**検証**カスタム コード内のメソッドです。 ランタイム エンジンが呼び出すことによって、タスクを検証、**検証**タスクのメソッドです。 タスクの開発者は、タスクの検証が成功または失敗する条件を定義し、評価の結果をランタイム エンジンに通知する必要があります。  
  
#### <a name="task-abstract-base-class"></a>タスクの抽象基本クラス  
 <xref:Microsoft.SqlServer.Dts.Runtime.Task>抽象基本クラスを提供、**検証**その検証条件を定義する各タスクをオーバーライドするメソッド。 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]デザイナーが自動的に呼び出します、**検証**パッケージのデザイン時に複数回のメソッドに役立つタスクの構成に関する問題を特定の警告またはエラーが発生したときに、視覚的な手掛かりをユーザーに提供します。 タスクは、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 列挙から値を返し、警告およびエラー イベントを発生させることにより、検証結果を返します。 これらのイベントには、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでユーザーに表示される情報が含まれています。  
  
 次に、いくつかの検証の例を挙げます。  
  
-   接続マネージャーは、特定のファイル名を検証します。  
  
-   接続マネージャーは、入力の種類が XML ファイルなどの必要な種類であることを検証します。  
  
-   データベースの入力が必要なタスクは、データベース以外の接続からデータを受け取れないことを確認します。  
  
-   タスクは、タスクのどのプロパティも、同じタスクに設定された他のプロパティと矛盾していないことを保証します。  
  
-   タスクは、タスクが使用する必要なすべてのリソースが実行時に使用できることを保証します。  
  
 検証する項目としない項目を決定する際には、パフォーマンスを考慮する必要があります。 たとえば、タスクへの入力で、低帯域またはトラフィックが混雑しているネットワーク経由の接続が使用されている場合があります。 その場合、リソースが使用可能かを検証する処理には、数秒かかる可能性があります。 別の検証では要求処理量が多いサーバーへのラウンド トリップが発生し、検証ルーチンの速度が遅くなる可能性があります。 検証可能なプロパティや設定は多数ありますが、すべてを検証するべきではありません。  
  
-   内のコード、**検証**、メソッドを呼び出しても、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>タスクの実行前に、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>検証が失敗した場合は、実行をキャンセルします。  
  
#### <a name="user-interface-considerations-during-validation"></a>検証時のユーザー インターフェイスについての検討事項  
 <xref:Microsoft.SqlServer.Dts.Runtime.Task>が含まれています、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>インターフェイスへのパラメーターとして、**検証**メソッドです。 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> インターフェイスには、イベントをランタイム エンジンに送るためにタスクが呼び出すメソッドが含まれています。 検証中に警告またはエラー条件が発生すると、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> および <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> メソッドが呼び出されます。 どちらの警告メソッドにも、エラー コード、ソース コンポーネント、説明、ヘルプ ファイル、ヘルプ コンテキスト情報などの同じパラメーターが必要です。 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはこの情報に基づいて、エラーの発生をデザイン画面上で視覚的に通知します。 デザイナーによって提供される視覚的な通知には、デザイン画面上のタスクの横に表示される感嘆符のアイコンがあります。 この視覚的通知は、実行を続けるにはタスクの構成を追加する必要があることを示します。  
  
 感嘆符のアイコンによって、エラー メッセージを含むツールヒントも表示されます。 エラー メッセージは、タスクによってイベントの説明パラメーターに提供されます。 エラー メッセージに表示されます、**タスク一覧**のウィンドウ[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]、すべての検証エラーを表示するための中央の場所をユーザーに提供します。  
  
#### <a name="validation-example"></a>検証例  
 次のコード例でタスクを示しています、 **UserName**プロパティです。 このプロパティは、検証に必要なものとして指定されています。 このプロパティが設定されていない場合、タスクはエラーを通知し、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> 列挙から <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> を返します。 **検証**メソッドは、try ブロックと catch ブロックにラップされ、検証に失敗した場合は、例外が発生します。  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class SampleTask : Task  
{  
  private string userName = "";  
  
  public override DTSExecResult Validate(Connections connections,  
     VariableDispenser variableDispenser, IDTSComponentEvents events,  
     IDTSLogging log)  
  {  
    try  
    {  
      if (this.userName == "")  
      {  
        //   Raise an OnError event.  
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);  
        //   Fail validation.  
        return DTSExecResult.Failure;  
      }  
      //   Return success.  
      return DTSExecResult.Success;  
    }  
    catch (System.Exception exception)  
    {  
      //   Capture exceptions, post an error, and fail validation.  
      events.FireError(0, "Sampletask", exception.Message, "", 0);  
      return DTSExecResult.Failure;  
    }  
  }  
  public string UserName  
  {  
    get  
    {  
      return this.userName;  
    }  
    set  
    {  
      this.userName = value;  
    }  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Public Class SampleTask  
  Inherits Task  
  
  Private _userName As String = ""  
  
  Public Overrides Function Validate(ByVal connections As Connections, _  
     ByVal variableDispenser As VariableDispenser, _  
     ByVal events As IDTSComponentEvents, _  
     ByVal log As IDTSLogging) As DTSExecResult  
  
    Try  
      If Me._userName = "" Then  
        '   Raise an OnError event.  
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)  
        '   Fail validation.  
        Return DTSExecResult.Failure  
      End If  
      '   Return success.  
      Return DTSExecResult.Success  
    Catch exception As System.Exception  
      '   Capture exceptions, post an error, and fail validation.  
      events.FireError(0, "Sampletask", exception.Message, "", 0)  
      Return DTSExecResult.Failure  
    End Try  
  
  End Function  
  
  Public Property UserName() As String  
    Get  
      Return Me._userName  
    End Get  
    Set(ByVal Value As String)  
      Me._userName = Value  
    End Set  
  End Property  
  
End Class  
```  
  
### <a name="persisting-the-task"></a>タスクの保存  
 通常、タスクに対して、カスタムの永続性を実装する必要はありません。 カスタムの永続性は、オブジェクトのプロパティで複合データ型が使用されている場合にのみ必要です。 詳細については、次を参照してください。 [Integration Services 用のカスタム オブジェクトの開発](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)です。  
  
## <a name="executing-the-task"></a>タスクの実行  
 このセクションを使用する方法について説明、 **Execute**継承され、タスクでオーバーライドされるメソッド。 また、タスクの実行結果についての情報を提供するさまざまな方法についても説明します。  
  
### <a name="execute-method"></a>Execute メソッド  
 パッケージに含まれているタスクは実行時に、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]ランタイムが呼び出す、 **Execute**メソッドです。 タスクは、このメソッドで、主要なビジネス ロジックや機能を実装してからの戻り値、メッセージを送信することによって実行の結果を提供、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>列挙型、およびプロパティをオーバーライドする**取得**の**ExecutionValue**プロパティです。  
  
 基本クラス <xref:Microsoft.SqlServer.Dts.Runtime.Task> には、既定で <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッドが実装されています。 カスタム タスクは、実行時の機能を定義するために、このメソッドをオーバーライドします。 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトはタスクをラップし、ランタイム エンジンやパッケージ内の他のオブジェクトと分離します。 そのため、タスクはパッケージ内での実行順序に関する位置を認識しているわけではなく、ランタイムによって呼び出されたときにのみ実行されます。 このアーキテクチャにより、実行中にタスクがパッケージを変更したときに発生する問題が回避されます。 タスクがパッケージ内の他のオブジェクトにアクセスするには、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッド内のパラメーターとして用意されているオブジェクトを使用する必要があります。 これらのパラメーターを使用すると、パッケージの安定度と信頼性を保証するために必要な分離性を保ちながら、イベントの発生、イベント ログへのエントリの記録、変数コレクションへのアクセス、およびトランザクション内のデータ ソースへの接続の登録を、タスクに実行させることができます。  
  
 次の表は、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッド内のタスクに対して提供されるパラメーターの一覧です。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|タスクで使用できる <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトのコレクションを含みます。|  
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|タスクで使用できる変数を含みます。 タスクは、VariableDispenser を介して変数を使用します。変数を直接使用することはありません。 変数ディスペンサーには、変数をロックまたはロック解除したり、デッドロックや上書きを防ぐ機能があります。|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|イベントを生成してランタイム エンジンに送るためにタスクが呼び出すメソッドを含みます。|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|イベント ログにエントリを記録するためにタスクが使用するメソッドおよびプロパティを含みます。|  
|オブジェクト|トランザクション オブジェクトの一部がコンテナーである場合、そのオブジェクトを含みます。 この値はパラメーターとして、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> メソッドに渡されます。|  
  
### <a name="providing-execution-feedback"></a>実行結果のフィードバックの送信  
 タスクでのコードをラップする**try ブロックと catch**から、ランタイム エンジンに発生する例外を防ぐためにブロックします。 これにより、パッケージは予期せず停止することなく、実行を完了します。 ランタイム エンジンには、タスクの実行中に発生する可能性のあるエラー条件を処理するメカニズムが他にも用意されています。 このメカニズムには、エラー メッセージや警告メッセージの通知、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 構造からの戻り値、メッセージの通知、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> の戻り値、<xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> プロパティによるタスクの実行結果に関する情報の公開などが含まれています。  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> インターフェイスには、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> メソッドがあり、タスクはこれらを呼び出して、エラー メッセージや警告メッセージをランタイム エンジンに通知できます。 どちらのメソッドにも、エラー コード、ソース コンポーネント、説明、ヘルプ ファイル、ヘルプ コンテキスト情報などのパラメーターが必要です。 タスクの構成に応じて、ランタイムは、イベントやブレークポイントを発生させたり、イベント ログに情報を記録したりする方法で、これらのメッセージに応答します。  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> は、実行結果に関する追加情報を提供するために使用可能な <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> プロパティも提供します。 たとえば、次のタスクは、の一部としてテーブルから行を削除、 **Execute**メソッドを削除された行数の値として返されます、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A>プロパティです。 また、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> は <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> プロパティを提供します。 ユーザーはこのプロパティを使用して、タスクから返された <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> を、タスクで認識可能な任意の変数にマップすることができます。 指定した変数を使用して、タスク間の優先順位制約を確立できます。  
  
### <a name="execution-example"></a>実行例  
 実装を次のコード例に示します、 **Execute**メソッドを示し、オーバーライドされた**ExecutionValue**プロパティです。 タスクで指定されているファイルの削除、 **fileName**タスクのプロパティです。 ファイルが存在しない場合、または場合に、タスクが、警告を送信、 **fileName**プロパティは、空の文字列。 タスクを返します、**ブール**値で、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A>ファイルが削除されたかどうかを示すプロパティです。  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class SampleTask : Task  
{  
  private string fileName = "";  
  private bool fileDeleted = false;  
  
  public override DTSExecResult Execute(Connections cons,  
     VariableDispenser vars, IDTSComponentEvents events,  
     IDTSLogging log, Object txn)  
  {  
    try  
    {  
      if (this.fileName == "")  
      {  
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);  
        this.fileDeleted = false;  
      }  
      else  
      {  
        if (System.IO.File.Exists(this.fileName))  
        {  
          System.IO.File.Delete(this.fileName);  
          this.fileDeleted = true;  
        }  
        else  
          this.fileDeleted = false;  
      }  
      return DTSExecResult.Success;  
    }  
    catch (System.Exception exception)  
    {  
      //   Capture the exception and post an error.  
      events.FireError(0, "Sampletask", exception.Message, "", 0);  
      return DTSExecResult.Failure;  
    }  
  }  
  public string FileName  
  {  
    get { return this.fileName; }  
    set { this.fileName = value; }  
  }  
  public override object ExecutionValue  
  {  
    get { return this.fileDeleted; }  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Public Class SampleTask  
  Inherits Task  
  
  Private _fileName As String = ""  
  Private _fileDeleted As Boolean = False  
  
  Public Overrides Function Execute(ByVal cons As Connections, _  
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _  
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult  
  
    Try  
      If Me._fileName = "" Then  
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)  
        Me._fileDeleted = False  
      Else  
        If System.IO.File.Exists(Me._fileName) Then  
          System.IO.File.Delete(Me._fileName)  
          Me._fileDeleted = True  
        Else  
          Me._fileDeleted = False  
        End If  
      End If  
      Return DTSExecResult.Success  
    Catch exception As System.Exception  
      '   Capture the exception and post an error.  
      events.FireError(0, "Sampletask", exception.Message, "", 0)  
      Return DTSExecResult.Failure  
    End Try  
  
  End Function  
  
  Public Property FileName() As String  
    Get  
      Return Me._fileName  
    End Get  
    Set(ByVal Value As String)  
      Me._fileName = Value  
    End Set  
  End Property  
  
  Public Overrides ReadOnly Property ExecutionValue() As Object  
    Get  
      Return Me._fileDeleted  
    End Get  
  End Property  
  
End Class  
```  
  
## <a name="see-also"></a>参照  
 [カスタム タスクを作成します。](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)   
 [カスタム タスクのコーディング](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)   
 [カスタム タスクのユーザー インターフェイスの開発](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
  
  

