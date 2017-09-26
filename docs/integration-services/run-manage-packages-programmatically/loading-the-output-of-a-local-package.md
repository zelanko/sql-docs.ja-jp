---
title: "ローカル パッケージの出力を読み込む |Microsoft ドキュメント"
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
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 41de742c987d9f043f3dd247ee84af6a3eaf365b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="loading-the-output-of-a-local-package"></a>ローカル パッケージの出力の読み込み
  クライアント アプリケーションの出力を読み取ることができる[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に保存されると、出力をパッケージ化[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して変換先[!INCLUDE[vstecado](../../includes/vstecado-md.md)]、またはクラスを使用して、フラット ファイル変換先に出力が保存した場合、 **System.IO**名前空間。 ただし、メモリから直接、パッケージの出力を読み取ることもできます。その際、データを保持するための中間手段を必要としません。 このソリューションの鍵は、 **Microsoft.SqlServer.Dts.DtsClient**名前空間の特殊な実装が含まれていますが、 **IDbConnection**、 **IDbCommand**、および**IDbDataParameter**からのインターフェイスで、 **System.Data**名前空間。 Microsoft.SqlServer.Dts.DtsClient.dll が既定でインストールされているアセンブリ**%ProgramFiles%\Microsoft SQL server \100\dts\binn**です。  
  
> [!NOTE]  
>  このトピックで説明する手順は、データ フロー タスクおよび親オブジェクトの DelayValidation プロパティがの既定値に設定することが必要です**False**です。  
  
## <a name="description"></a>Description  
 この手順では、マネージ コードを使用して、DataReader 変換先でパッケージの出力をメモリから直接読み込むクライアント アプリケーションを開発する方法を示します。 ここにまとめた手順は、後のコード例で示します。  
  
#### <a name="to-load-data-package-output-into-a-client-application"></a>クライアント アプリケーションにパッケージ出力を読み込むには  
  
1.  パッケージで、クライアント アプリケーションに読み込む出力を受信するように DataReader 変換先を構成します。 DataReader 変換先にはわかりやすい名前を付けます。この名前は後からクライアント アプリケーションで使用します。 DataReader 変換先の名前はメモしておきます。  
  
2.  開発プロジェクトに参照を設定、 **Microsoft.SqlServer.Dts.DtsClient**アセンブリの検索では名前空間**Microsoft.SqlServer.Dts.DtsClient.dll**です。 既定では、このアセンブリがインストールされているで**C:\Program files \microsoft SQL server \100\dts\binn**です。 C# を使用して、コードに、名前空間をインポート**Using**または[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] **Imports**ステートメントです。  
  
3.  コードで型のオブジェクトを作成する**DtsClient.DtsConnection**で必要なコマンド ライン パラメーターを含む接続文字列と共に**dtexec.exe**パッケージを実行します。 詳しくは、「 [dtexec Utility](../../integration-services/packages/dtexec-utility.md)」をご覧ください。 次に、この接続文字列を使用して接続を開きます。 使用することも、 **dtexecui**ユーティリティは、必要な接続文字列を視覚的に作成します。  
  
    > [!NOTE]  
    >  このサンプル コードは、`/FILE <path and filename>` 構文を使用してファイル システムからパッケージを読み込む方法を示していますが、 `/SQL <package name>` 構文を使用して MSDB データベースからパッケージを読み込んだり、`/DTS \<folder name>\<package name>` 構文を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ストアからパッケージを読み込むこともできます。  
  
4.  型のオブジェクトを作成する**DtsClient.DtsCommand**を使用して、以前に作成した**DtsConnection**設定とその**CommandText**プロパティ、DataReader の名前をパッケージのコピー先です。 まず、 **ExecuteReader**にパッケージの結果を新しい DataReader に読み込むコマンド オブジェクトのメソッドです。  
  
5.  必要に応じて、することが間接的にパラメーター化、パッケージの出力のコレクションを使用して**DtsDataParameter**でオブジェクトを**DtsCommand**パッケージで定義された変数に値を渡すオブジェクト。 パッケージ内では、これらの変数をクエリ パラメーターとして、または式で使用して、DataReader 変換先に返される結果に影響を与えることができます。 パッケージ内でこれらの変数を定義する必要があります、 **DtsClient**名前空間でそれらを使用する前に、 **DtsDataParameter**クライアント アプリケーションからのオブジェクト。 (をクリックする必要があります、 **変数列の**ツール バー ボタン、**変数**ウィンドウに表示する、 **Namespace**列です)。クライアント コードで、追加するときに、 **DtsDataParameter**を**パラメーター**のコレクション、 **DtsCommand**、変数名からの DtsClient 名前空間の参照を省略. 例:  
  
    ```  
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));  
    ```  
  
6.  呼び出す、**読み取り**DataReader の行をループするために必要と繰り返しのメソッドは、データを出力します。 クライアント アプリケーションで、データを使用するか、または後で使用するために保存します。  
  
    > [!IMPORTANT]  
    >  **読み取り**、DataReader のこの実装のメソッドを返します**true**データの最後の行が読み取られた後に 1 つの時間。 いる間、DataReader をループする通常のコードを使用するが困難になります。**読み取り**返します**true**です。 DataReader またはせずに、追加の最後の呼び出しの行の数が読み取られた後、接続を終了しようとすると、コード、**読み取り**メソッド、コードでハンドルされない例外が発生します。 ただし、コードがループし、この最後の反復処理でデータの読み取りを試みると、ときに**読み取り**が返されます**true**最後の行が渡されましたが、未処理のコードが生成されます**ApplicationException**メッセージ「SSIS IDataReader は結果セットの末尾を越えた」。 この動作は、その他の DataReader 実装の動作とは異なります。 そのため、ループを使用している間、DataReader 内の行を読み取るときに**読み取り**返します**true**、する必要がありますをキャッチするコードを記述するテスト、および破棄予想されるこの**ApplicationException**に成功した前回の呼び出しで、**読み取り**メソッドです。 または、事前にわかって予想される行の数場合、行を処理して呼び出す、、**読み取り**メソッド、DataReader および接続を閉じる前にもう一度です。  
  
7.  呼び出す、 **Dispose**のメソッド、 **DtsCommand**オブジェクト。 これはいずれかを使用している場合に特に重要**DtsDataParameter**オブジェクト。  
  
8.  DataReader と接続オブジェクトを閉じます。  
  
## <a name="example"></a>例  
 次の例では、1 つの集計値を計算してその値を DataReader 変換先に保存するパッケージを実行します。次に、この値を DataReader から読み取って、Windows フォーム上のテキスト ボックスに表示します。  
  
 パッケージの出力をクライアント アプリケーションに読み込む場合は、パラメーターを使用する必要はありません。 パラメーターを使用しない場合は、内の変数の使用を省略できます、 **DtsClient**名前空間を使用するコードを省略し、 **DtsDataParameter**オブジェクト。  
  
#### <a name="to-create-the-test-package"></a>テスト パッケージを作成するには  
  
1.  新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成します。 サンプル コードでは、パッケージの名前として "DtsClientWParamPkg.dtsx" が使用されています。  
  
2.  DtsClient 名前空間に文字列型の変数を追加します。 サンプル コードでは、変数の名前として Country が使用されています  (をクリックする必要があります、 **変数列の**ツール バー ボタン、**変数**ウィンドウに表示する、 **Namespace**列です)。  
  
3.  [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベースに接続する OLE DB 接続マネージャーを追加します。  
  
4.  データ フロー タスクをパッケージに追加し、[データ フロー] デザイン画面に切り替えます。  
  
5.  OLE DB ソースをデータ フローに追加し、前に作成した OLE DB 接続マネージャーを使用するように構成して、次の SQL コマンドを実行します。  
  
    ```  
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?  
    ```  
  
6.  をクリックして**パラメーター**し、**クエリ パラメーターの設定** ダイアログ ボックスで、クエリで Parameter0、単一の入力パラメーターを dtsclient::country 変数にマップします。  
  
7.  データ フローに集計変換を追加し、OLE DB ソースの出力を変換に接続します。 集計変換エディターを開いて、すべての入力列 (*) で "すべてのカウント" 操作が実行され、集計された値が CustomerCount の別名で出力されるように構成します。  
  
8.  データ フローに DataReader 変換先を追加し、集計変換の出力を DataReader 変換先に接続します。 サンプル コードでは、DataReader の名前として "DataReaderDest" が使用されています。 変換先に対して使用可能な単一の入力列 CustomerCount を選択します。  
  
9. パッケージを保存します。 次に作成されたテスト アプリケーションではパッケージが実行され、その出力がメモリから直接取得されます。  
  
#### <a name="to-create-the-test-application"></a>テスト アプリケーションを作成するには  
  
1.  新しい Windows フォーム アプリケーションを作成します。  
  
2.  参照を追加、 **Microsoft.SqlServer.Dts.DtsClient**名前空間内の同じ名前のアセンブリを参照して**%ProgramFiles%\Microsoft SQL server \100\dts\binn**です。  
  
3.  次のサンプル コードをコピーし、フォームのコード モジュールに貼り付けます。  
  
4.  値を変更、 **dtexecArgs**必要に応じて変数格納するために必要なコマンド ライン パラメーター **dtexec.exe**パッケージを実行します。 サンプル コードは、ファイル システムからパッケージを読み込みます。  
  
5.  値を変更、 **dataReaderName**必要に応じて変数格納するため、パッケージ内の DataReader 変換先の名前。  
  
6.  ボタンとテキスト ボックスをフォームに追加します。 サンプル コードを使用して**btnRun** 、ボタンの名前としてと**txtResults**としてテキスト ボックスの名前。  
  
7.  アプリケーションを実行し、ボタンをクリックします。 パッケージの実行中に一時停止したら、パッケージによって計算された集計値 (Canada の顧客数) が、フォーム上のテキスト ボックスに表示されます。  
  
### <a name="sample-code"></a>サンプル コード  
  
```vb  
Imports System.Data  
Imports Microsoft.SqlServer.Dts.DtsClient  
  
Public Class Form1  
  
  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click  
  
    Dim dtexecArgs As String  
    Dim dataReaderName As String  
    Dim countryName As String  
  
    Dim dtsConnection As DtsConnection  
    Dim dtsCommand As DtsCommand  
    Dim dtsDataReader As IDataReader  
    Dim dtsParameter As DtsDataParameter  
  
    Windows.Forms.Cursor.Current = Cursors.WaitCursor  
  
    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""  
    dataReaderName = "DataReaderDest"  
    countryName = "Canada"  
  
    dtsConnection = New DtsConnection()  
    With dtsConnection  
      .ConnectionString = dtexecArgs  
      .Open()  
    End With  
  
    dtsCommand = New DtsCommand(dtsConnection)  
    dtsCommand.CommandText = dataReaderName  
  
    dtsParameter = New DtsDataParameter("Country", DbType.String)  
    dtsParameter.Direction = ParameterDirection.Input  
    dtsCommand.Parameters.Add(dtsParameter)  
  
    dtsParameter.Value = countryName  
  
    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)  
  
    With dtsDataReader  
      .Read()  
      txtResults.Text = .GetInt32(0).ToString("N0")  
    End With  
  
    'After reaching the end of data rows,  
    ' call the Read method one more time.  
    Try  
      dtsDataReader.Read()  
    Catch ex As Exception  
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception on final call to Read method", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    ' The following method is a best practice, and is  
    '  required when using DtsDataParameter objects.  
    dtsCommand.Dispose()  
  
    Try  
      dtsDataReader.Close()  
    Catch ex As Exception  
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception closing DataReader", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    Try  
      dtsConnection.Close()  
    Catch ex As Exception  
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception closing connection", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    Windows.Forms.Cursor.Current = Cursors.Default  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Data;  
using Microsoft.SqlServer.Dts.DtsClient;  
  
namespace DtsClientWParamCS  
{  
  public partial class Form1 : Form  
  {  
    public Form1()  
    {  
      InitializeComponent();  
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);  
    }  
  
    private void btnRun_Click(object sender, EventArgs e)  
    {  
      string dtexecArgs;  
      string dataReaderName;  
      string countryName;  
  
      DtsConnection dtsConnection;  
      DtsCommand dtsCommand;  
      IDataReader dtsDataReader;  
      DtsDataParameter dtsParameter;  
  
      Cursor.Current = Cursors.WaitCursor;  
  
      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";  
      dataReaderName = "DataReaderDest";  
      countryName = "Canada";  
  
      dtsConnection = new DtsConnection();  
      {  
        dtsConnection.ConnectionString = dtexecArgs;  
        dtsConnection.Open();  
      }  
  
      dtsCommand = new DtsCommand(dtsConnection);  
      dtsCommand.CommandText = dataReaderName;  
  
      dtsParameter = new DtsDataParameter("Country", DbType.String);  
      dtsParameter.Direction = ParameterDirection.Input;  
      dtsCommand.Parameters.Add(dtsParameter);  
  
      dtsParameter.Value = countryName;  
  
      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);  
  
      {  
        dtsDataReader.Read();  
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");  
      }  
  
      //After reaching the end of data rows,  
      // call the Read method one more time.  
      try  
      {  
        dtsDataReader.Read();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      // The following method is a best practice, and is  
      //  required when using DtsDataParameter objects.  
      dtsCommand.Dispose();  
  
      try  
      {  
        dtsDataReader.Close();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      try  
      {  
        dtsConnection.Close();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      Cursor.Current = Cursors.Default;  
  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>参照  
 [ローカルおよびリモート実行の相違点を理解します。](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [読み込みと、プログラムによるローカル パッケージの実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [プログラムによるリモート パッケージの読み込みと実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
  
