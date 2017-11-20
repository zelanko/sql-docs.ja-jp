---
title: "スクリプト タスクを持つ Excel ファイルの操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 46bf53c35663393ad600f02600961cf0295386bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-excel-files-with-the-script-task"></a>スクリプト タスクを使用した Excel ファイルの操作
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には Excel 接続マネージャー、Excel ソース、Excel 変換先が用意されており、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ファイル形式のスプレッドシートに保存されているデータを操作できます。 このトピックで説明する方法では、スクリプト タスクを使用して、使用可能な Excel のデータベース (ワークブック ファイル) およびテーブル (ワークシートおよび名前付き範囲) に関する情報を取得します。 これらのサンプルに簡単な変更を加えて、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB プロバイダーによってサポートされる他のすべてのファイルベース データ ソースを操作することができます。  
  
 [サンプルをテストするためのパッケージを構成します。](#configuring)  
  
 [例 1: Excel ファイルが存在するかどうかを確認します。](#example1)  
  
 [例 2: Excel のテーブルが存在するかどうかを確認します。](#example2)  
  
 [例 3: フォルダー内の Excel ファイルの一覧を取得します。](#example3)  
  
 [例 4: Excel ファイル内のテーブルの一覧を取得します。](#example4)  
  
 [サンプルの結果を表示します。](#testing)  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
##  <a name="configuring"></a>サンプルをテストするためのパッケージを構成します。  
 このトピックのすべてのサンプルをテストする単一のパッケージを構成することができます。 これらのサンプルでは、同じパッケージ変数と同じ [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスを数多く使用します。  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a>このトピックの例で使用するパッケージを構成するには  
  
1.  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で新しい [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトを作成し、編集のために既定のパッケージを開きます。  
  
2.  **変数**です。 開く、**変数**ウィンドウし、次の変数を定義します。  
  
    -   `ExcelFile`、型の**文字列**です。 既存の Excel ワークブックの完全なパスとファイル名を入力します。  
  
    -   `ExcelTable`、型の**文字列**です。 `ExcelFile` 変数の値で指定されたワークブック内の既存のワークシートまたは名前付き範囲の名前を入力します。 この値は、大文字と小文字が区別されます。  
  
    -   `ExcelFileExists`、型の**ブール**です。  
  
    -   `ExcelTableExists`、型の**ブール**です。  
  
    -   `ExcelFolder`、型の**文字列**です。 少なくとも 1 つの Excel ワークブックを含むフォルダーの完全なパスを入力します。  
  
    -   `ExcelFiles`、型の**オブジェクト**です。  
  
    -   `ExcelTables`、型の**オブジェクト**です。  
  
3.  **Imports ステートメント**です。 ほとんどのコード サンプルでは、スクリプト ファイルの先頭で次の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 名前空間のいずれかまたは両方をインポートする必要があります。  
  
    -   **System.IO**、ファイル システム操作にします。  
  
    -   **System.Data.OleDb**をデータ ソースとして Excel ファイルを開きます。  
  
4.  **参照**です。 Excel ファイルからスキーマ情報を読み込むコード サンプルは、スクリプト プロジェクトに追加の参照が必要、 **System.Xml**名前空間。  
  
5.  使用して、スクリプト コンポーネントの既定のスクリプト言語を設定、**スクリプト言語** オプションを選択、**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、「 [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)」を参照してください。  
  
##  <a name="example1"></a>例 1 の説明: Excel ファイルが存在するかどうかを確認します。  
 この例では、`ExcelFile` 変数で指定された Excel ワークブック ファイルが存在するかどうかを判断し、その結果を `ExcelFileExists` 変数のブール値に設定します。 このブール値は、パッケージのワークフローを分岐させるために使用することができます。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  パッケージに新しいスクリプト タスクを追加し、名前に変更**ExcelFileExists**です。  
  
2.  **スクリプト タスク エディター**の**スクリプト** タブで、をクリックして**ReadOnlyVariables**を使用して次のいずれかのプロパティ値を入力します。  
  
    -   型**ExcelFile**です。  
  
         -または-  
  
    -   省略記号ボタン (**.**) プロパティ フィールドにし、[次へ] ボタン、**変数を選択**ダイアログ ボックスで、選択、 **ExcelFile**変数。  
  
3.  をクリックして**ReadWriteVariables**し、次のメソッドのいずれかを使用してプロパティ値を入力します。  
  
    -   型**ExcelFileExists**です。  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、、**変数を選択**ダイアログ ボックスで、選択、 **ExcelFileExists**変数。  
  
4.  をクリックして**スクリプトの編集**スクリプト エディターを開きます。  
  
5.  追加、 **Imports**のステートメント、 **System.IO**スクリプト ファイルの上部にある名前空間。  
  
6.  次のコードを追加します。  
  
### <a name="example-1-code"></a>コード例 1  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example2"></a>例 2 の説明: Excel のテーブルが存在するかどうかを確認します。  
 この例では、`ExcelTable` 変数で指定された Excel ワークシートまたは名前付き範囲が `ExcelFile` 変数で指定された Excel ワークブック ファイル内に存在するかどうかを判断し、その結果を `ExcelTableExists` 変数のブール値に設定します。 このブール値は、パッケージのワークフローを分岐させるために使用することができます。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  パッケージに新しいスクリプト タスクを追加し、名前に変更**ExcelTableExists**です。  
  
2.  **スクリプト タスク エディター**の**スクリプト** タブで、をクリックして**ReadOnlyVariables**を使用して次のいずれかのプロパティ値を入力します。  
  
    -   型**ExcelTable**と**ExcelFile**コンマで区切って**です。**  
  
         -または-  
  
    -   省略記号ボタン (**.**) プロパティ フィールドにし、[次へ] ボタン、**変数を選択**ダイアログ ボックスで、選択、 **ExcelTable**と**ExcelFile**変数。  
  
3.  をクリックして**ReadWriteVariables**し、次のメソッドのいずれかを使用してプロパティ値を入力します。  
  
    -   型**ExcelTableExists**です。  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、、**変数を選択**ダイアログ ボックスで、選択、 **ExcelTableExists**変数。  
  
4.  をクリックして**スクリプトの編集**スクリプト エディターを開きます。  
  
5.  参照を追加、 **System.Xml**スクリプト プロジェクト内のアセンブリ。  
  
6.  追加**Imports**のステートメント、 **System.IO**と**System.Data.OleDb**スクリプト ファイルの上部にある名前空間。  
  
7.  次のコードを追加します。  
  
### <a name="example-2-code"></a>コード例 2  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example3"></a>例 3 の説明: フォルダー内の Excel ファイルの一覧を取得します。  
 この例では、`ExcelFolder` 変数の値で指定されたフォルダー内で検索された Excel ファイルの一覧を配列に代入し、その配列を `ExcelFiles` 変数にコピーします。 Foreach from Variable 列挙子を使用して、配列内のファイルを繰り返し処理することができます。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  パッケージに新しいスクリプト タスクを追加し、名前に変更**GetExcelFiles**です。  
  
2.  開く、**スクリプト タスク エディター**の**スクリプト** タブで、をクリックして**ReadOnlyVariables**を使用して次のいずれかのプロパティ値を入力します。  
  
    -   型**ExcelFolder**  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、、**変数を選択** ダイアログ ボックスで、ExcelFolder 変数を選択します。  
  
3.  をクリックして**ReadWriteVariables**し、次のメソッドのいずれかを使用してプロパティ値を入力します。  
  
    -   型**ExcelFiles**です。  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、、**変数を選択** ダイアログ ボックスで、ExcelFiles 変数を選択します。  
  
4.  をクリックして**スクリプトの編集**スクリプト エディターを開きます。  
  
5.  追加、 **Imports**のステートメント、 **System.IO**スクリプト ファイルの上部にある名前空間。  
  
6.  次のコードを追加します。  
  
### <a name="example-3-code"></a>コード例 3  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a>代替ソリューション  
 スクリプト タスクを使用して Excel ファイルの一覧を配列に集める代わりに、ForEach File 列挙子を使用してフォルダー内のすべての Excel ファイルを繰り返し処理することもできます。 詳細については、次を参照してください。 [Excel ファイルおよび Foreach ループ コンテナーを使用してテーブルをループ](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)です。  
  
##  <a name="example4"></a>例 4 の説明: Excel ファイル内のテーブルの一覧を取得します。  
 この例では、`ExcelFile` 変数の値で指定された Excel ワークブック ファイル内で検索されたワークシートまたは名前付き範囲の一覧を配列に代入し、その配列を `ExcelTables` 変数にコピーします。 Foreach from Variable 列挙子を使用して、配列内のテーブルを繰り返し処理することができます。  
  
> [!NOTE]  
>  Excel ブック内のテーブルの一覧には、ワークシート ($ サフィックスが付きます) と名前付き範囲が含まれます。 ワークシートまたは名前付き範囲のみを一覧からフィルター選択する必要がある場合は、そのためのコードを追加する必要があります。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  パッケージに新しいスクリプト タスクを追加し、名前に変更**GetExcelTables**です。  
  
2.  開く、**スクリプト タスク エディター**の**スクリプト** タブで、をクリックして**ReadOnlyVariables**を使用して次のいずれかのプロパティ値を入力します。  
  
    -   型**ExcelFile**です。  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、[、**変数を選択**] ダイアログ ボックスで、[excelfile] 変数を選択します。  
  
3.  をクリックして**ReadWriteVariables**し、次のメソッドのいずれかを使用してプロパティ値を入力します。  
  
    -   型**ExcelTables**です。  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、[、**変数を選択**] ダイアログ ボックスで、ExcelTablesvariable を選択します。  
  
4.  をクリックして**スクリプトの編集**スクリプト エディターを開きます。  
  
5.  参照を追加、 **System.Xml**スクリプト プロジェクトの名前空間。  
  
6.  追加、 **Imports**のステートメント、 **System.Data.OleDb**スクリプト ファイルの上部にある名前空間。  
  
7.  次のコードを追加します。  
  
### <a name="example-4-code"></a>例 4 のコード  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a>代替ソリューション  
 スクリプト タスクを使用して Excel テーブルの一覧を配列に集める代わりに、ForEach ADO.NET Schema Rowset 列挙子を使用して Excel ワークブック ファイル内のすべてのテーブル (つまり、ワークシートと名前付き範囲) を繰り返し処理することもできます。 詳細については、次を参照してください。 [Excel ファイルおよび Foreach ループ コンテナーを使用してテーブルをループ](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)です。  
  
##  <a name="testing"></a>サンプルの結果を表示します。  
 このトピックの各例を同じパッケージで構成した場合は、すべてのスクリプト タスクを、すべての例の出力を表示する追加のスクリプト タスクに接続することができます。  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a>このトピックの例の出力を表示するスクリプト タスクを構成するには  
  
1.  パッケージに新しいスクリプト タスクを追加し、名前に変更**DisplayResults**です。  
  
2.  各タスクは、前のタスクが完了したらが実行されるように、相互接続の各例を次の 4 つのスクリプト タスクと接続する 4 番目のタスクの例、 **DisplayResults**タスク。  
  
3.  開く、 **DisplayResults**内のタスク、**スクリプト タスク エディター**です。  
  
4.  **スクリプト** タブで、をクリックして**ReadOnlyVariables**し、次のメソッドのいずれかに含まれるすべての 7 つの変数を追加する[サンプルをテストするためのパッケージを構成する](#configuring):  
  
    -   各変数の名前をコンマで区切って入力します。  
  
         -または-  
  
    -   省略記号ボタン (**.**) ボタンをクリックし、プロパティ フィールドに、、**変数を選択**ダイアログ ボックスで、変数を選択します。  
  
5.  をクリックして**スクリプトの編集**スクリプト エディターを開きます。  
  
6.  追加**Imports**のステートメント、 **Microsoft.VisualBasic**と**System.Windows.Forms**スクリプト ファイルの上部にある名前空間。  
  
7.  次のコードを追加します。  
  
8.  パッケージを実行し、メッセージ ボックスに表示される結果を調べます。  
  
### <a name="code-to-display-the-results"></a>結果を表示するコード  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
## <a name="see-also"></a>参照  
 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  

