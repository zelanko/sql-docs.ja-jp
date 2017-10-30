---
title: "スクリプト コンポーネントを含むソースの作成 |Microsoft ドキュメント"
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
- Script component [Integration Services], source components
- output columns [Integration Services]
- sources [Integration Services], components
ms.assetid: 547c4179-ea82-4265-8c6f-04a2aa77a3c0
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4944c3d5752da21fed90f16a38a33b4fad41515
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-source-with-the-script-component"></a>スクリプト コンポーネントによる変換元の作成
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内で変換元コンポーネントを使用すると、データ ソースからデータを読み込み、下流にある変換や変換先に渡すことができます。 通常、データ ソースへの接続には、既存の接続マネージャーを使用します。  
  
 スクリプト コンポーネントの概要については、次を参照してください。[スクリプト コンポーネントによるデータ フローの拡張](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)です。  
  
 スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。 スクリプト コンポーネントの動作のしくみを理解するため、カスタム データ フロー コンポーネントの開発手順を理解しておくと役立つ場合があります。 セクションを参照して[カスタム データ フロー コンポーネントを開発](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)、トピックでは特に[カスタム変換元コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)です。  
  
## <a name="getting-started-with-a-source-component"></a>変換元コンポーネントの概要  
 [データ フロー] ペインにスクリプト コンポーネントを追加すると[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナー、**スクリプト コンポーネントの種類の選択** ダイアログ ボックスが開き、変換元、変換先、または変換のスクリプトを選択するように求められます。 このダイアログ ボックスで選択**ソース**です。  
  
## <a name="configuring-a-source-component-in-metadata-design-mode"></a>メタデータ デザイン モードでの変換元コンポーネントの構成  
 使用して、コンポーネントの構成を選択したら、変換元コンポーネントを作成した後、**スクリプト変換エディター**です。 詳細については、次を参照してください。[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)です。  
  
 データ フロー変換元コンポーネントに入力はありませんが、1 つ以上の出力を設定できます。 使用してメタデータ デザイン モードで完了する必要のある手順のいずれかのコンポーネントは、出力の構成、**スクリプト変換エディター**カスタム スクリプトを記述する前に、します。  
  
 設定して、スクリプト言語を指定することも、 **[scriptlanguage]**プロパティを**スクリプト**のページ、**スクリプト変換エディター**です。  
  
> [!NOTE]  
>  スクリプト コンポーネントとスクリプト タスクの既定のスクリプト言語を設定するには、使用、**スクリプト言語** オプションを選択、**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、「 [General Page](~/integration-services/control-flow/script-task-editor-general-page.md)」を参照してください。  
  
### <a name="adding-connection-managers"></a>接続マネージャーの追加  
 通常、変換元コンポーネントは既存の接続マネージャーを使用してデータ ソースに接続し、データをデータ フローに読み込みます。 **接続マネージャー**のページ、**スクリプト変換エディター**、 をクリックして**追加**適切な接続マネージャーを追加します。  
  
 ただし、接続マネージャーは、カプセル化して、特定の種類のデータ ソースに接続するために必要とする情報を格納する便利な単位のみです。 データの読み込みや保存、場合によってはデータ ソースとの接続や切断を行うためには、独自のカスタム コードを記述する必要もあります。  
  
 スクリプト コンポーネントによる接続マネージャーを使用する方法に関する一般情報は、次を参照してください。[スクリプト コンポーネントでデータ ソースに接続する](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)です。  
  
 詳細については、**接続マネージャー**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター & #40 です。接続マネージャー ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-outputs-and-output-columns"></a>出力および出力列の設定  
 変換元コンポーネントに入力はありませんが、1 つ以上の出力を設定できます。 **入力と出力**のページ、**スクリプト変換エディター**は既定では、1 つの出力が作成されましたが、出力列が作成されていません。 エディターのこのページで、必要に応じて以下の項目を設定します。  
  
-   各出力に対する出力列は、手動で追加して設定する必要があります。 各出力に対する出力列 フォルダーを選択し、使用、**列の追加**と**列の削除**変換元コンポーネントの各出力に対する出力列を管理するボタンです。 後でスクリプト内で出力列を参照する際には、ここで割り当てた名前、および自動生成されたコードによって作成された、型指定されたアクセサー プロパティを使用します。  
  
-   予期しない値を含む行に対するシミュレートされたエラー出力など、1 つ以上の出力を追加して作成できます。 使用して、**出力の追加**と**出力の削除**ボタン変換元コンポーネントの出力を管理します。 すべての入力行は使用可能なすべての出力に送られますの同一の 0 以外の値も指定しない限り、 **ExclusionGroup**同じを共有する出力の 1 つのみに各行をダイレクトする出力のプロパティ**ExclusionGroup**値。 識別する特定の整数値が選択されている、 **ExclusionGroup**大きな違いはありません。  
  
    > [!NOTE]  
    >  0 以外を使用することもできます。 **ExclusionGroup**すべての行を出力したくない場合に、1 つの出力を持つプロパティ値。 この場合、ただし、明示的に呼び出す必要があります、 **DirectRowTo\<outputbuffer >**行ごとに、出力に送信するメソッド。  
  
-   出力にはわかりやすい名前を付けておくことができます。 後で出力を参照する際には、スクリプト内での名前、および自動生成されたコードによって作成された、型指定されたアクセサー プロパティを使用します。  
  
-   複数の同じ出力に通常**ExclusionGroup**列は出力が同じです。 ただし、シミュレートされたエラー出力を作成している場合、エラー情報を格納するために列を追加します。 データ フロー エンジンの方法については、エラー行を処理するを参照してください。[データ フロー コンポーネントでエラー出力を使用して](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)です。 ただし、スクリプト コンポーネントでは、独自のコードを記述して、追加した列に該当するエラー情報を格納する必要があります。 詳細については、次を参照してください。[スクリプト コンポーネントのエラー出力のシミュレート](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)です。  
  
 詳細については、**入力と出力**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター (&) #40 です。 入力し、呼び出し力 ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)です。  
  
### <a name="adding-variables"></a>変数の追加  
 既存の変数の値をスクリプトで使用する場合は、それらを追加できます、 **ReadOnlyVariables**と**ReadWriteVariables**プロパティのフィールド、**スクリプト**のページ、**スクリプト変換エディター**です。  
  
 プロパティ フィールドに複数の変数を入力する場合は、変数名をコンマで区切ります。 省略記号ボタンをクリックして、複数の変数を入力することもできます (**.**) ボタンを**ReadOnlyVariables**と**ReadWriteVariables**プロパティ フィールドと変数を選択すると、**変数を選択** ダイアログ ボックス.  
  
 スクリプト コンポーネントで変数を使用する方法に関する一般情報は、次を参照してください。[スクリプト コンポーネントで変数を使用して](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)です。  
  
 詳細については、**スクリプト**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター & #40 です。[スクリプト] ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-source-component-in-code-design-mode"></a>コード デザイン モードでの変換元コンポーネントのスクリプト作成  
 コンポーネントのメタデータを構成した後で開く、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE、カスタム スクリプトを記述します。 VSTA を開くにはクリックして**スクリプトの編集**上、**スクリプト**のページ、**スクリプト変換エディター**です。 いずれかを使用して、スクリプトを記述できます[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Basic または[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual C# の場合、選択したスクリプト言語に応じて、 **[scriptlanguage]**プロパティです。  
  
 スクリプト コンポーネントを使用して作成されたコンポーネントのすべての種類に適用される重要な情報について、次を参照してください。[コーディングおよびスクリプト コンポーネントのデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)です。  
  
### <a name="understanding-the-auto-generated-code"></a>自動生成されたコードについて  
 作成と編集可能な変換元コンポーネントを構成した後で VSTA IDE を開くときに**ScriptMain**クラスがコード エディターで表示されます。 カスタム コードを記述する、 **ScriptMain**クラスです。  
  
 **ScriptMain**クラスにはスタブが含まれています、 **CreateNewOutputRows**メソッドです。 **CreateNewOutputRows**変換元コンポーネントで最も重要なメソッドです。  
  
 開く場合、**プロジェクト エクスプ ローラー** VSTA のウィンドウで、スクリプト コンポーネントが、読み取り専用生成も確認できます**BufferWrapper**と**ComponentWrapper**プロジェクト項目。 **ScriptMain**クラスから継承**UserComponent**クラス内で、 **ComponentWrapper**プロジェクト項目です。  
  
 データ フロー エンジンを起動、実行時に、 **PrimeOutput**メソッドで、 **UserComponent**クラスが優先、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>クラスの親です。 **PrimeOutput**メソッドがさらに次のメソッドを呼び出します。  
  
1.  **CreateNewOutputRows**メソッドのオーバーライドを**ScriptMain**最初に空は、バッファーに行を追加、データ ソースからの出力。  
  
2.  **FinishOutputs**メソッドで、既定では空です。 このメソッドでオーバーライド**ScriptMain**出力を完了するために必要な処理を実行します。  
  
3.  プライベート**MarkOutputsAsFinished**メソッドの呼び出し、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>をデータ フロー エンジンに出力が完了したことを示すクラスの親です。 呼び出していない**SetEndOfRowset**独自のコードで明示的にします。  
  
### <a name="writing-your-custom-code"></a>カスタム コードの記述  
 カスタム変換元コンポーネントの作成を終了する可能性があるスクリプトで使用できる次の方法で作成、 **ScriptMain**クラスです。  
  
1.  上書き、 **AcquireConnections**外部データ ソースに接続する方法です。 接続マネージャーから、接続オブジェクトまたは必要な接続情報を抽出します。  
  
2.  上書き、 **PreExecute**メソッド データを読み込む場合は、同時にすべてのソース データを読み込むことができます。 たとえば、実行することができます、 **SqlCommand**に対して、[!INCLUDE[vstecado](../../includes/vstecado-md.md)]への接続、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースし、同時にすべてのソース データを読み込み、 **SqlDataReader**です。 内の行をループするようにデータを読み込むことができます (たとえば、テキスト ファイルを読み取るときに) 時に、ソース データの 1 つの行を読み込む必要がある場合、 **CreateNewOutputRows**です。  
  
3.  使用して、オーバーライドされた**CreateNewOutputRows**メソッドが空の出力バッファーに新しい行を追加して、新しい出力行の各列の値を入力します。 使用して、 **AddRow**空の新しい行を追加し、各列の値を設定するには、各出力バッファーのメソッドです。 通常は、外部ソースから読み込まれた列から値をコピーします。  
  
4.  上書き、 **PostExecute**メソッドが、データの処理を完了します。 たとえば、閉じ、 **SqlDataReader**データを読み込むために使用することです。  
  
5.  上書き、 **ReleaseConnections**必要な場合、外部データ ソースから切断するメソッド。  
  
## <a name="examples"></a>使用例  
 次の例では、カスタム コードで必要な**ScriptMain**変換元コンポーネントを作成するクラス。  
  
> [!NOTE]  
>  これらの例を使用して、 **Person.Address**テーブルに、 **AdventureWorks**サンプル データベースと、最初と 4 番目の列を渡す、 **intAddressID**と**nvarchar (30) 市区町村**をデータ フローの列です。 このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。 他の前提条件および仮定条件については、それぞれの例で説明します。  
  
### <a name="adonet-source-example"></a>ADO.NET ソースの例  
 この例では、既存の変換元コンポーネント[!INCLUDE[vstecado](../../includes/vstecado-md.md)]からデータを読み込む接続マネージャー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ フローにテーブルです。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  作成、[!INCLUDE[vstecado](../../includes/vstecado-md.md)]を使用する接続マネージャー、 **SqlClient**プロバイダーに接続する、 **AdventureWorks**データベース。  
  
2.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換元として構成します。  
  
3.  開く、**スクリプト変換エディター**です。 **入力と出力** ページで、既定のわかりやすい名前を持つように出力の名前を変更**MyAddressOutput**、追加し、2 つの出力列の構成**AddressID**と**市区町村**です。  
  
    > [!NOTE]  
    >  データ型を変更してください、**市区町村**DT_WSTR に列を出力します。  
  
4.  **接続マネージャー**  ページで追加または作成、[!INCLUDE[vstecado](../../includes/vstecado-md.md)]接続マネージャーの名前を指定ようと**MyADONETConnection**です。  
  
5.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じると、**スクリプト変換エディター**です。  
  
6.  作成し、変換先コンポーネントを構成するように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、または変換先コンポーネントのサンプルに示されている[スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)、予想される、 **AddressID**と**市区町村**列です。 変換元のコンポーネントを変換先に接続します  (変換を介さずに変換元を直接変換先に接続することもできます)。コピー先のテーブルを作成するには、次を実行して[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンドを**AdventureWorks**データベース。  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
7.  サンプルを実行します。  
  
    ```vb  
    Imports System.Data.SqlClient  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim connMgr As IDTSConnectionManager100  
        Dim sqlConn As SqlConnection  
        Dim sqlReader As SqlDataReader  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            connMgr = Me.Connections.MyADONETConnection  
            sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            Dim cmd As New SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn)  
            sqlReader = cmd.ExecuteReader  
  
        End Sub  
  
        Public Overrides Sub CreateNewOutputRows()  
  
            Do While sqlReader.Read  
                With MyAddressOutputBuffer  
                    .AddRow()  
                    .AddressID = sqlReader.GetInt32(0)  
                    .City = sqlReader.GetString(1)  
                End With  
            Loop  
  
        End Sub  
  
        Public Overrides Sub PostExecute()  
  
            sqlReader.Close()  
  
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
        SqlDataReader sqlReader;  
  
        public override void AcquireConnections(object Transaction)  
        {  
            connMgr = this.Connections.MyADONETConnection;  
            sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
        }  
  
        public override void PreExecute()  
        {  
  
            SqlCommand cmd = new SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn);  
            sqlReader = cmd.ExecuteReader();  
  
        }  
  
        public override void CreateNewOutputRows()  
        {  
  
            while (sqlReader.Read())  
            {  
                {  
                    MyAddressOutputBuffer.AddRow();  
                    MyAddressOutputBuffer.AddressID = sqlReader.GetInt32(0);  
                    MyAddressOutputBuffer.City = sqlReader.GetString(1);  
                }  
            }  
  
        }  
  
        public override void PostExecute()  
        {  
  
            sqlReader.Close();  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            connMgr.ReleaseConnection(sqlConn);  
  
        }  
  
    }  
    ```  
  
### <a name="flat-file-source-example"></a>フラット ファイル ソースの例  
 この例では、既存のフラット ファイル接続マネージャーを使用して、フラット ファイルからデータを読み込み、データ フローに送る変換元コンポーネントを示します。 フラット ファイル ソースのデータは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からエクスポートすることにより作成されます。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をエクスポートするには、インポートおよびエクスポート ウィザード、 **Person.Address**からテーブル、 **AdventureWorks**をコンマで区切られたフラット ファイルのサンプル データベース。 この例では、ファイル名を ExportedAddresses.txt とします。  
  
2.  エクスポートされたデータ ファイルに接続するフラット ファイル接続マネージャーを作成します。  
  
3.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換元として構成します。  
  
4.  開く、**スクリプト変換エディター**です。 **入力と出力** ページで、既定のわかりやすい名前を持つように出力の名前を変更**MyAddressOutput**です。 追加して、2 つの出力列を構成する**AddressID**と**市区町村**です。  
  
5.  **接続マネージャー**ページで追加またはフラット ファイル接続マネージャーなどのわかりやすい名前を使用して作成**MyFlatFileSrcConnectionManager**です。  
  
6.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じると、**スクリプト変換エディター**です。  
  
7.  作成し、変換先コンポーネントを構成するように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、または変換先コンポーネントのサンプルに示されている[スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)です。 変換元のコンポーネントを変換先に接続します  (変換を介さずに変換元を直接変換先に接続することもできます)。コピー先のテーブルを作成するには、次を実行して[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンドを**AdventureWorks**データベース。  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  サンプルを実行します。  
  
    ```vb  
    Imports System.IO  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Private textReader As StreamReader  
        Private exportedAddressFile As String  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connMgr As IDTSConnectionManager100 = _  
                Me.Connections.MyFlatFileSrcConnectionManager  
            exportedAddressFile = _  
                CType(connMgr.AcquireConnection(Nothing), String)  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
            MyBase.PreExecute()  
            textReader = New StreamReader(exportedAddressFile)  
        End Sub  
  
        Public Overrides Sub CreateNewOutputRows()  
  
            Dim nextLine As String  
            Dim columns As String()  
  
            Dim delimiters As Char()  
            delimiters = ",".ToCharArray  
  
            nextLine = textReader.ReadLine  
            Do While nextLine IsNot Nothing  
                columns = nextLine.Split(delimiters)  
                With MyAddressOutputBuffer  
                    .AddRow()  
                    .AddressID = columns(0)  
                    .City = columns(3)  
                End With  
                nextLine = textReader.ReadLine  
            Loop  
  
        End Sub  
  
        Public Overrides Sub PostExecute()  
            MyBase.PostExecute()  
            textReader.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.IO;  
    public class ScriptMain:  
        UserComponent  
  
    {  
        private StreamReader textReader;  
        private string exportedAddressFile;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileSrcConnectionManager;  
            exportedAddressFile = (string)connMgr.AcquireConnection(null);  
  
        }  
  
        public override void PreExecute()  
        {  
            base.PreExecute();  
            textReader = new StreamReader(exportedAddressFile);  
        }  
  
        public override void CreateNewOutputRows()  
        {  
  
            string nextLine;  
            string[] columns;  
  
            char[] delimiters;  
            delimiters = ",".ToCharArray();  
  
            nextLine = textReader.ReadLine();  
            while (nextLine != null)  
            {  
                columns = nextLine.Split(delimiters);  
                {  
                    MyAddressOutputBuffer.AddRow();  
                    MyAddressOutputBuffer.AddressID = columns[0];  
                    MyAddressOutputBuffer.City = columns[3];  
                }  
                nextLine = textReader.ReadLine();  
            }  
  
        }  
  
        public override void PostExecute()  
        {  
  
            base.PostExecute();  
            textReader.Close();  
  
        }  
  
    }  
    ```  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)   
 [カスタム変換元コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
  
  

