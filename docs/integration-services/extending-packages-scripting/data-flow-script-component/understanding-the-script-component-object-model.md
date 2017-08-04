---
title: "スクリプト コンポーネント オブジェクト モデルについて |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 09de00344fe94087b6287b07c4b1ffe933d27b7c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="understanding-the-script-component-object-model"></a>スクリプト コンポーネントのオブジェクト モデルについて
  説明したよう[コーディングおよびスクリプト コンポーネントのデバッグ](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)、スクリプト コンポーネント プロジェクトには、次の 3 つのプロジェクト項目が含まれています。  
  
1.  **ScriptMain**を含む項目が、 **ScriptMain**コードを記述するクラス。 **ScriptMain**クラスから継承、 **UserComponent**クラスです。  
  
2.  **ComponentWrapper**を含む項目が、 **UserComponent**クラスのインスタンス<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>メソッドとデータを処理して、パッケージとのやり取りに使用するプロパティを格納しています。 **ComponentWrapper**項目も含まれている**接続**と**変数**コレクション クラスです。  
  
3.  **BufferWrapper**から継承するクラスが含まれている項目<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>の各列の各入力と出力、呼び出しに型指定されたプロパティ。  
  
 コードを記述する際、 **ScriptMain**項目、オブジェクト、メソッド、およびこのトピックで説明するプロパティを使用します。 ここで一覧されているすべてのメソッドを各コンポーネントが使用するわけではありませんが、使用される場合は、ここで示した順序で使用されます。  
  
 基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> には、ここで説明しているメソッドのコードは実装されていません。 したがって、メソッド独自の実装に基本クラスの実装の呼び出しを追加する必要はありませんが、追加した場合でも問題は生じません。  
  
 スクリプト コンポーネントの特定の種類でこれらのクラスのプロパティとメソッドを使用する方法については、セクションを参照して[スクリプト コンポーネントの他の例](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)です。 サンプルについてのトピックでは、完全なコード例も示します。  
  
## <a name="acquireconnections-method"></a>AcquireConnections メソッド  
 通常、変換元および変換先は外部データ ソースに接続する必要があります。 基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドして、適切な接続マネージャーから、接続または接続情報を取得します。  
  
 次の例を返します、 **System.Data.SqlClient.SqlConnection** ADO.NET 接続マネージャーからです。  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 次の例は、フラット ファイル接続マネージャーから、完全なパスとファイル名を返し、使用して、ファイルを開きます、 **System.IO.StreamReader**です。  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>PreExecute メソッド  
 データの行の処理を開始する前に 1 回だけ実行する必要のある処理がある場合は、基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。 たとえば、データの各行をデータ ソースに挿入するために変換先が使用するパラメーター化コマンドを、変換先に設定することができます。  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>入力および出力の処理  
  
### <a name="processing-inputs"></a>入力の処理  
 変換または変換先として構成されたスクリプト コンポーネントには、1 つの入力があります。  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>プロジェクト アイテム BufferWrapper が提供する機能  
 構成したこと、各入力の**BufferWrapper**プロジェクト アイテムにはから派生するクラスが含まれています<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>の入力として、同じ名前を持ちます。 各入力バッファー クラスには、次のプロパティ、関数、およびメソッドが含まれています。  
  
-   選択された各入力列の、型指定された名前付きのアクセサー プロパティ。 これらのプロパティは読み取り専用または読み取り/書き込みによって、**使用法の種類**列に指定された、**入力列**のページ、**スクリプト変換エディター**です。  
  
-   A **\<列 > _IsNull**プロパティを選択した各入力列です。 このプロパティも読み取り専用または読み取り/書き込みによって、**使用法の種類**列に指定されています。  
  
-   A **DirectRowTo\<outputbuffer >**ごとにメソッドが出力を構成します。 いくつかの出力を同じのいずれかに行をフィルター処理するときにこれらのメソッドを使用する**ExclusionGroup**です。  
  
-   A **nextrow を指定**を次の入力行を取得する関数と**EndOfRowset**データの最後のバッファーが処理されているかどうかを判断する関数。 通常必要はありませんこれらの関数入力処理メソッドの実装を使用すると、 **UserComponent**基本クラスです。 次のセクションについて詳細に説明、 **UserComponent**基本クラスです。  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>プロジェクト アイテム ComponentWrapper が提供する機能  
 ComponentWrapper プロジェクト項目には、という名前のクラスが含まれています。 **UserComponent**から派生した<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>です。 **ScriptMain** 、カスタム コードを記述するクラスから派生**UserComponent**です。 **UserComponent**クラスには、次のメソッドが含まれています。  
  
-   オーバーライドして実装、 **ProcessInput**メソッドです。 これは、データ フロー エンジン呼び出し次の後に実行時に、メソッド、 **PreExecute**メソッド、およびそれが複数回呼び出します。 **ProcessInput**に処理を渡します、  **\<inputbuffer > _ProcessInput**メソッドです。 続いて、 **ProcessInput**メソッドは、入力バッファーの末尾をチェックし、バッファーの末尾に達している場合は、オーバーライド可能な呼び出し**FinishOutputs**メソッドと private **MarkOutputsAsFinished**メソッドです。 **MarkOutputsAsFinished**メソッドを呼び出します**SetEndOfRowset**最後の出力バッファーにします。  
  
-   オーバーライド可能な実装、  **\<inputbuffer > _ProcessInput**メソッドです。 この既定の実装は、各入力行と呼び出しを単にループ **\<inputbuffer > _ProcessInputRow**です。  
  
-   オーバーライド可能な実装、  **\<inputbuffer > _ProcessInputRow**メソッドです。 既定の実装では、空のままです。 このメソッドは、カスタム データ処理コードを記述するために、通常はオーバーライドして使用します。  
  
#### <a name="what-your-custom-code-should-do"></a>カスタム コードとして組み込むべき機能  
 入力を処理する、次のメソッドを使用することができます、 **ScriptMain**クラス。  
  
-   オーバーライド **\<inputbuffer > _ProcessInputRow**を通過する間に各入力行のデータを処理します。  
  
-   オーバーライド **\<inputbuffer > _ProcessInput**入力行をループ処理中に追加の処理を実行する必要がある場合にのみです。 (たとえばのテストする必要があります**EndOfRowset**アクションを実行するいくつか他のすべての行が処理されている)。呼び出す **\<inputbuffer > _ProcessInputRow**を行の処理を実行します。  
  
-   オーバーライド**FinishOutputs**には何の出力を閉じる前にする必要がある場合。  
  
 **ProcessInput**メソッドは適切な時点でこれらのメソッドを呼び出すことを確認します。  
  
### <a name="processing-outputs"></a>出力の処理  
 変換元または変換として構成されたスクリプト コンポーネントには、1 つ以上の出力があります。  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>プロジェクト アイテム BufferWrapper が提供する機能  
 構成したコンポーネントの出力ごとに、プロジェクト アイテム BufferWrapper には、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> から派生した、出力と同じ名前のクラスがあります。 各出力バッファー クラスには、次のプロパティおよびメソッドが含まれています。  
  
-   各出力列の、名前付きで型指定された、書き込み専用のアクセサー プロパティ。  
  
-   書き込み専用**\<列 > _IsNull**列値に設定を使用できる各選択されている出力列のプロパティを**null**です。  
  
-   **AddRow**出力バッファーに空の新しい行を追加します。  
  
-   A **SetEndOfRowset**データ フロー エンジンがデータのバッファーが必要になっていることを確認できるようにするメソッド。 **EndOfRowset**関数を現在のバッファーがデータの最後のバッファーであるかどうかを確認します。 通常必要はありませんこれらの関数入力処理メソッドの実装を使用すると、 **UserComponent**基本クラスです。  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>プロジェクト アイテム ComponentWrapper が提供する機能  
 ComponentWrapper プロジェクト項目には、という名前のクラスが含まれています。 **UserComponent**から派生した<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>です。 **ScriptMain** 、カスタム コードを記述するクラスから派生**UserComponent**です。 **UserComponent**クラスには、次のメソッドが含まれています。  
  
-   オーバーライドして実装、 **PrimeOutput**メソッドです。 データ フロー エンジンは、前にこのメソッドを呼び出す**ProcessInput** 、実行時に 1 回はのみ呼び出されるとします。 **PrimeOutput**に処理を渡します、 **CreateNewOutputRows**メソッドです。 その後、コンポーネントが、ソースである場合 (つまり、コンポーネントを持たない入力)、 **PrimeOutput** 、オーバーライド可能な呼び出し**FinishOutputs**メソッドと private **MarkOutputsAsFinished**メソッドです。 **MarkOutputsAsFinished**メソッド呼び出し**SetEndOfRowset**最後の出力バッファーにします。  
  
-   オーバーライド可能な実装、 **CreateNewOutputRows**メソッドです。 既定の実装では、空のままです。 このメソッドは、カスタム データ処理コードを記述するために、通常はオーバーライドして使用します。  
  
#### <a name="what-your-custom-code-should-do"></a>カスタム コードとして組み込むべき機能  
 出力を処理する、次のメソッドを使用することができます、 **ScriptMain**クラス。  
  
-   オーバーライド**CreateNewOutputRows**だけで追加して、設定した場合は、入力行を処理する前に行を出力します。 たとえば、使用することができます**CreateNewOutputRows** 、ソースでは、非同期出力型変換を呼び出す必要があります**AddRow**中または入力データの処理後にします。  
  
-   オーバーライド**FinishOutputs**には何の出力を閉じる前にする必要がある場合。  
  
 **PrimeOutput**メソッドは適切な時点でこれらのメソッドを呼び出すことを確認します。  
  
## <a name="postexecute-method"></a>PostExecute メソッド  
 データの行を処理した後に 1 回だけ実行する必要のある処理がある場合は、基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。 たとえば、ソースの可能性があります終了する、 **System.Data.SqlClient.SqlDataReader**するを使用しているデータ フローにデータを読み込みます。  
  
> [!IMPORTANT]  
>  コレクション**ReadWriteVariables**でのみ使用できますが、 **PostExecute**メソッドです。 したがって、データ行を処理するたびにパッケージ変数の値を直接増やすことはできません。 代わりに、ローカル変数の値をインクリメントし、内のローカル変数の値をパッケージ変数の値を設定、 **PostExecute**メソッドのすべてのデータの処理が完了します。  
  
## <a name="releaseconnections-method"></a>ReleaseConnections メソッド  
 元および変換先通常必要があります、外部データ ソースに接続します。 基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドして、以前に <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> メソッドで開いた接続を閉じ、解放します。  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成します。](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)   
 [コーディングおよびスクリプト コンポーネントのデバッグ](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
