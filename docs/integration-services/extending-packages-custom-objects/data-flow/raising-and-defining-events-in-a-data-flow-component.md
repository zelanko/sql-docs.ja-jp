---
title: "発生して、イベントを定義するデータ フロー コンポーネント |Microsoft ドキュメント"
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
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a900b27c9056d95fb2284d8ba9d6b09d9c6635b5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>データ フロー コンポーネントのイベントの発生と定義
  コンポーネント開発者は、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> プロパティで公開されているメソッドを呼び出して、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> インターフェイスで定義されているイベントのサブセットを発生させることができます。 また、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> コレクションを使用してカスタム イベントを定義し、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> メソッドを使用して、実行時にこのイベントを発生させることもできます。 このセクションでは、イベントを作成、発生させる方法について説明し、デザイン時にイベントを発生させるタイミングに関するガイドラインを示します。  
  
## <a name="raising-events"></a>イベントを発生させる  
 コンポーネントを使用してイベントを発生させる、**火災\<X >**のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>インターフェイスです。 イベントは、コンポーネントのデザイン時および実行時のどちらでも発生させることができます。 通常、コンポーネントのデザイン時には、検証中に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> メソッドや <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> メソッドが呼び出されます。 これらのイベント内のメッセージを表示する、**エラー一覧**のウィンドウ[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]し、コンポーネントが正しく構成されていない場合、コンポーネントのユーザーにフィードバックを提供します。  
  
 コンポーネントは、実行時の任意のタイミングでもイベントを発生させることができます。 イベントを使用すると、コンポーネント開発者はユーザーに対して、コンポーネントの実行に伴うフィードバックを返すことができます。 実行時に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> メソッドが呼び出された場合、パッケージが失敗したと考えられます。  
  
## <a name="defining-and-raising-custom-events"></a>カスタム イベントの定義と発生  
  
### <a name="defining-a-custom-event"></a>カスタム イベントの定義  
 カスタム イベントを作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> コレクションの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> メソッドを呼び出します。 このコレクションはデータ フロー タスクによって設定され、コンポーネント開発者には、基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> を介したプロパティとして提供されます。 このクラスには、データ フロー タスクによって定義されたカスタム イベントと、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> メソッド内でコンポーネントによって定義されたカスタム イベントが含まれています。  
  
 コンポーネントのカスタム イベントは、パッケージ XML には保存されません。 したがって、コンポーネントのデザイン時および実行時の両方で <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> メソッドが呼び出され、発生するイベントが定義されます。  
  
 *AllowEventHandlers*のパラメーター、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A>メソッドでは、コンポーネントができるかどうかを示す<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>イベントに対して作成されるオブジェクト。 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> は同期型であることに注意してください。 このため、カスタム イベントにアタッチされた <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> の実行が終了するまで、コンポーネントは実行を再開しません。 場合、 *allowEventHandlers*パラメーターは**true**、イベントの各パラメーターが自動的に使用可能に<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>作成され、によって自動的に設定されている変数を使用したオブジェクト、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]ランタイム。  
  
### <a name="raising-a-custom-event"></a>カスタム イベントの発生  
 コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> メソッドを呼び出し、イベントの名前、テキスト、パラメーターを渡して、カスタム イベントを発生させます。 場合、 *allowEventHandlers*パラメーターは**true**、any<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers>カスタム イベントがによって実行される作成される、[!INCLUDE[ssIS](../../../includes/ssis-md.md)]ランタイム エンジンです。  
  
### <a name="custom-event-sample"></a>カスタム イベントのサンプル  
 次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> メソッドの実行中にカスタム イベントを定義し、実行時に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> メソッドを呼び出してこのイベントを発生させるコンポーネントを示します。  
  
```csharp  
public override void RegisterEvents()  
{  
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};  
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};  
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};  
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref paramterTypes, ref parameterDescriptions);  
}  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
    while (buffer.NextRow())  
    {  
       // Process buffer rows.  
    }  
  
    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];  
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };  
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);  
}  
```  
  
```vb  
Public  Overrides Sub RegisterEvents()   
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"}   
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)}   
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."}   
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, paramterTypes, parameterDescriptions)   
End Sub   
  
Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
  While buffer.NextRow   
  End While   
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort")   
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now}   
  ComponentMetaData.FireCustomEvent("StartingSort", _  
    "Beginning sort operation.", arguments, _  
    ComponentMetaData.Name, FireSortEventAgain)   
End Sub  
```  

## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;イベント ハンドラー](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [イベント ハンドラーをパッケージに追加します。](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  
