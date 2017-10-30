---
title: "スクリプト コンポーネントによる変換先の作成 |Microsoft ドキュメント"
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
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7680aac73590f92eadd615b9d164967e61877664
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-destination-with-the-script-component"></a>スクリプト コンポーネントによる変換先の作成
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内では、変換先コンポーネントを使用して、上流の変換元や変換から受け取ったデータをデータ ソースに保存します。 通常、変換先コンポーネントをデータ ソースに接続するには、既存の接続マネージャーを使用します。  
  
 スクリプト コンポーネントの概要については、次を参照してください。[スクリプト コンポーネントによるデータ フローの拡張](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)です。  
  
 スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。 ただし、スクリプト コンポーネントのしくみを理解する有用なことに目を通すでカスタム データ フロー コンポーネントを開発するための手順、[カスタム データ フロー コンポーネントを開発](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)セクション、特に[カスタム変換先コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)です。  
  
## <a name="getting-started-with-a-destination-component"></a>変換先コンポーネントの概要  
 [データ フロー] タブにスクリプト コンポーネントを追加すると[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナー、**スクリプト コンポーネントの種類の選択** ダイアログ ボックスが開き、選択を求められ、**ソース**、**変換先**、または**変換**スクリプト。 このダイアログ ボックスで選択**先**です。  
  
 次に、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、変換の出力を変換先コンポーネントに接続します。 テスト目的の場合、変換を介さずに変換元を直接変換先に接続することもできます。  
  
## <a name="configuring-a-destination-component-in-metadata-design-mode"></a>メタデータ デザイン モードでの変換先コンポーネントの構成  
 使用して、コンポーネントを構成する、変換先コンポーネントを作成するオプションを選択した後、**スクリプト変換エディター**です。 詳細については、次を参照してください。[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)です。  
  
 設定するスクリプトの保存先を使用するスクリプト言語を選択する、 **[scriptlanguage]**プロパティを**スクリプト**のページ、**スクリプト変換エディター**ダイアログ ボックス。  
  
> [!NOTE]  
>  既定のスクリプト、スクリプト コンポーネントの言語を設定するには、使用、**スクリプト言語** オプションを選択、**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、「 [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)」を参照してください。  
  
 データ フローの変換先コンポーネントには、1 つの入力があり、出力はありません。 使用してメタデータ デザイン モードで完了する必要のある手順のいずれかのコンポーネントは、入力の構成、**スクリプト変換エディター**カスタム スクリプトを記述する前に、します。  
  
### <a name="adding-connection-managers"></a>接続マネージャーの追加  
 通常、変換先コンポーネントは既存の接続マネージャーを使用してデータ ソースに接続し、データ フローからのデータを保存します。 **接続マネージャー**のページ、**スクリプト変換エディター**、 をクリックして**追加**適切な接続マネージャーを追加します。  
  
 ただし、接続マネージャーは、便宜上、特定の種類のデータ ソースに接続するために必要な情報をカプセル化して格納するユニットにすぎません。 データの読み込みや保存、場合によってはデータ ソースとの接続や切断を行うためには、独自のカスタム コードを記述する必要があります。  
  
 スクリプト コンポーネントによる接続マネージャーを使用する方法に関する一般情報は、次を参照してください。[スクリプト コンポーネントでデータ ソースに接続する](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)です。  
  
 詳細については、**接続マネージャー**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター &#40;です。接続マネージャー ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-inputs-and-input-columns"></a>入力および入力列の設定  
 変換先コンポーネントには、1 つの入力があり、出力はありません。  
  
 **入力列**のページ、**スクリプト変換エディター**、列リスト データ フローの上流コンポーネントの出力から使用可能な列を示しています。 保存する列を選択します。  
  
 詳細については、**入力列**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター &#40;の入力列 ページ"&"#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)です。  
  
 **入力と出力**のページ、**スクリプト変換エディター**名前を変更する 1 つの入力を示しています。 スクリプト内ではこの名前で入力を参照しますが、参照には自動生成されたコードによって作成されたアクセサー プロパティが使用されます。  
  
 詳細については、**入力と出力**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター (&) #40 です。 入力し、呼び出し力 ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)です。  
  
### <a name="adding-variables"></a>変数の追加  
 スクリプトで既存の変数を使用する場合でそれらを追加、 **ReadOnlyVariables**と**ReadWriteVariables**プロパティのフィールド、**スクリプト**のページ、**スクリプト変換エディター**です。  
  
 プロパティ フィールドに複数の変数を追加する場合は、各変数名をコンマで区切ります。 省略記号ボタンをクリックして、複数の変数を選択することもできます (**.**) ボタンを**ReadOnlyVariables**と**ReadWriteVariables**プロパティ フィールド内の変数をクリックして、**変数を選択**ダイアログ ボックス。  
  
 スクリプト コンポーネントで変数を使用する方法に関する一般情報は、次を参照してください。[スクリプト コンポーネントで変数を使用して](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)です。  
  
 詳細については、**スクリプト**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター &#40;です。[スクリプト] ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-destination-component-in-code-design-mode"></a>コード デザイン モードでの変換先コンポーネントのスクリプト作成  
 コンポーネントのメタデータを構成した後、カスタム スクリプトを記述できます。 **スクリプト変換エディター**の**スクリプト**] ページで [**スクリプトの編集**を開くには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDEここで、カスタム スクリプトを追加することができます。 使用するスクリプト言語が選択されているかどうかに依存[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Basic または[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual c# のスクリプト言語として、 **[scriptlanguage]**プロパティを**スクリプト**ページです。  
  
 スクリプト コンポーネントを使用して作成されたコンポーネントのすべての種類に適用される重要な情報について、次を参照してください。[コーディングおよびスクリプト コンポーネントのデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)です。  
  
### <a name="understanding-the-auto-generated-code"></a>自動生成されたコードについて  
 開くと、VSTA IDE を作成した後、編集可能な変換先コンポーネントを構成する**ScriptMain**のスタブをコード エディターでクラスが表示されます、 **ProcessInputRow**メソッドです。 **ScriptMain**クラスは、カスタム コードを記述して**ProcessInputRow**変換先コンポーネントで最も重要なメソッドです。  
  
 開く場合、**プロジェクト エクスプ ローラー** VSTA のウィンドウで、スクリプト コンポーネントが、読み取り専用生成も確認できます**BufferWrapper**と**ComponentWrapper**プロジェクト項目。 **ScriptMain**クラスから継承**UserComponent**クラス内で、 **ComponentWrapper**プロジェクト項目です。  
  
 データ フロー エンジンを起動、実行時に、 **ProcessInput**メソッドで、 **UserComponent**クラスが優先、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>クラスの親です。 **ProcessInput**メソッドがさらに、入力バッファーと呼び出し内の行をループ処理、 **ProcessInputRow**メソッドを行ごとに 1 回です。  
  
### <a name="writing-your-custom-code"></a>カスタム コードの記述  
 カスタム変換先コンポーネントの作成を完了することがあるスクリプトで使用できる次の方法で作成、 **ScriptMain**クラスです。  
  
1.  上書き、 **AcquireConnections**外部データ ソースに接続する方法です。 接続マネージャーから、接続オブジェクトまたは必要な接続情報を抽出します。  
  
2.  上書き、 **PreExecute**メソッド データを保存する準備をします。 などを作成および構成することがあります、 **SqlCommand**そのパラメーターは、このメソッドであるとします。  
  
3.  使用して、オーバーライドされた**ProcessInputRow**に外部データ ソースに各入力行をコピーする方法です。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエクスポート先のパラメーターに、列の値をコピーすることができます、 **SqlCommand**行ごとに 1 回のコマンドを実行します。 フラット ファイル変換先の各列の値を記述することができます、 **StreamWriter**、列区切り記号で区切っています。  
  
4.  上書き、 **PostExecute** 、必要な場合は、外部データ ソースから切断し、必要なその他のクリーンアップを実行するメソッド。  
  
## <a name="examples"></a>使用例  
 次の例で必要なコードのデモンストレーション、 **ScriptMain**変換先コンポーネントを作成するクラス。  
  
> [!NOTE]  
>  これらの例を使用して、 **Person.Address**テーブルに、 **AdventureWorks**サンプル データベースと、最初と 4 番目の列を渡す、  **int*AddressID** * と**nvarchar (30) 市区町村**をデータ フローの列です。 このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。 他の前提条件および仮定条件については、それぞれの例で説明します。  
  
### <a name="adonet-destination-example"></a>ADO.NET 変換先の例  
 この例では、既存の変換先コンポーネント[!INCLUDE[vstecado](../../includes/vstecado-md.md)]へのデータ フローのデータを保存する接続マネージャー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  作成、[!INCLUDE[vstecado](../../includes/vstecado-md.md)]を使用する接続マネージャー、 **SqlClient**プロバイダーに接続する、 **AdventureWorks**データベース。  
  
2.  以下を実行して、変換先テーブルを作成する[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンドを**AdventureWorks**データベース。  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。  
  
4.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します  (変換を介さずに変換元を直接変換先に接続することもできます)。この出力はからデータを提供する必要があります、 **Person.Address**のテーブル、 **AdventureWorks**を含むサンプル データベースには、少なくとも、 **AddressID**と**市区町村**列です。  
  
5.  開く、**スクリプト変換エディター**です。 **入力列**] ページで、[、 **AddressID**と**市区町村**列を入力します。  
  
6.  **入力と出力**などわかりやすい名前を持つ、入力の名前を変更 ページで、 **MyAddressInput**です。  
  
7.  **接続マネージャー**  ページで追加または作成、[!INCLUDE[vstecado](../../includes/vstecado-md.md)]などの名前を持つ接続マネージャー **MyADONETConnectionManager**です。  
  
8.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じます。  
  
9. 閉じる、**スクリプト変換エディター**およびサンプルを実行します。  
  
```vb  
Imports System.Data.SqlClient  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim connMgr As IDTSConnectionManager100  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        connMgr = Me.Connections.MyADONETConnectionManager  
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
        With sqlCmd  
            .Parameters("@addressid").Value = Row.AddressID  
            .Parameters("@city").Value = Row.City  
            .ExecuteNonQuery()  
        End With  
    End Sub  
  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.Data.SqlClient;  
public class ScriptMain:  
    UserComponent  
  
{  
    IDTSConnectionManager100 connMgr;  
    SqlConnection sqlConn;  
    SqlCommand sqlCmd;  
    SqlParameter sqlParam;  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        connMgr = this.Connections.MyADONETConnectionManager;  
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +  
            "VALUES(@addressid, @city)", sqlConn);  
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);  
        sqlCmd.Parameters.Add(sqlParam);  
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);  
        sqlCmd.Parameters.Add(sqlParam);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
        {  
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;  
            sqlCmd.Parameters["@city"].Value = Row.City;  
            sqlCmd.ExecuteNonQuery();  
        }  
    }  
  
    public override void ReleaseConnections()  
    {  
  
        connMgr.ReleaseConnection(sqlConn);  
  
    }  
  
}  
```  
  
### <a name="flat-file-destination-example"></a>フラット ファイル変換先の例  
 この例では、既存のフラット ファイル接続マネージャーを使用して、データ フローのデータをフラット ファイルに保存する変換先コンポーネントを示します。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  変換先ファイルに接続するフラット ファイル接続マネージャーを作成します。 ファイルが存在しない場合は、変換先コンポーネントによって作成されます。 含むコンマ区切りファイルとしてリンク先のファイルを構成、 **AddressID**と**市区町村**列です。  
  
2.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。  
  
3.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します  (変換を介さずに変換元を直接変換先に接続することもできます)。この出力はからデータを提供する必要があります、 **Person.Address**のテーブル、 **AdventureWorks**サンプル データベース、および含める必要がありますが、少なくとも**AddressID**と**市区町村**列です。  
  
4.  開く、**スクリプト変換エディター**です。 **入力列**] ページで、[、 **AddressID**と**市区町村**列です。  
  
5.  **入力と出力**など、わかりやすい名前を入力の名前を変更 ページで、 **MyAddressInput**です。  
  
6.  **接続マネージャー**ページで追加するか、フラット ファイル接続マネージャーを作成、わかりやすい名前を持つなど**MyFlatFileDestConnectionManager**です。  
  
7.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じます。  
  
8.  閉じる、**スクリプト変換エディター**およびサンプルを実行します。  
  
```vb  
Imports System.IO  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim copiedAddressFile As String  
    Private textWriter As StreamWriter  
    Private columnDelimiter As String = ","  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        Dim connMgr As IDTSConnectionManager100 = _  
            Me.Connections.MyFlatFileDestConnectionManager  
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        textWriter = New StreamWriter(copiedAddressFile, False)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With textWriter  
            If Not Row.AddressID_IsNull Then  
                .Write(Row.AddressID)  
            End If  
            .Write(columnDelimiter)  
            If Not Row.City_IsNull Then  
                .Write(Row.City)  
            End If  
            .WriteLine()  
        End With  
  
    End Sub  
  
    Public Overrides Sub PostExecute()  
  
        textWriter.Close()  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.IO;  
public class ScriptMain:  
    UserComponent  
  
{  
    string copiedAddressFile;  
    private StreamWriter textWriter;  
    private string columnDelimiter = ",";  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;  
        copiedAddressFile = (string) connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        textWriter = new StreamWriter(copiedAddressFile, false);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            if (!Row.AddressID_IsNull)  
            {  
                textWriter.Write(Row.AddressID);  
            }  
            textWriter.Write(columnDelimiter);  
            if (!Row.City_IsNull)  
            {  
                textWriter.Write(Row.City);  
            }  
            textWriter.WriteLine();  
        }  
  
    }  
  
    public override void PostExecute()  
    {  
  
        textWriter.Close();  
  
    }  
  
}  
```  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネントによるソースを作成します。](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)   
 [カスタム変換先コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
  
  

