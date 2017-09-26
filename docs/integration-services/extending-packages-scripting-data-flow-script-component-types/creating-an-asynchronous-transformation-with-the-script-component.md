---
title: "スクリプト コンポーネントによる非同期変換の作成 |Microsoft ドキュメント"
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
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4da61e00337430a3eaef84e40f9f732a572cc45b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a>スクリプト コンポーネントによる非同期変換の作成
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内で変換コンポーネントを使用することにより、変換元から変換先にデータが受け渡される過程で、データを修正または分析できます。 同期出力型の変換では、各入力列はコンポーネントを通過するたびに処理されます。 変換は、すべての入力行を受信しました。 受け取る前にすべての入力行に、変換が特定の行を出力可能性がありますかされるまで、その処理を完了する非同期出力型変換が待機状態にします。 このトピックでは、非同期変換について説明します。 処理は、同期変換を必要とする場合は、次を参照してください。[スクリプト コンポーネントによる同期変換を作成する](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)です。 同期および非同期のコンポーネント間の相違点の詳細については、次を参照してください。[について同期および非同期変換](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)です。  
  
 スクリプト コンポーネントの概要については、次を参照してください。[スクリプト コンポーネントによるデータ フローの拡張](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)です。  
  
 スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を簡略化できます。 ただし、スクリプト コンポーネントのしくみを理解する有用なことに目を通すでカスタム データ フロー コンポーネントの開発に従う必要がある手順、[カスタム データ フロー コンポーネントを開発](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)セクション、および特に[同期出力型のカスタム変換コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)です。  
  
## <a name="getting-started-with-an-asynchronous-transformation-component"></a>非同期変換コンポーネントの概要  
 [データ フロー] タブにスクリプト コンポーネントを追加すると[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナー、**スクリプト コンポーネントの種類の選択** ダイアログ ボックスが表示されたら、ソース、変換、または変換先として、コンポーネントを事前に構成するように求められます。 このダイアログ ボックスで選択**変換**です。  
  
## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a>メタデータ デザイン モードでの非同期変換コンポーネントの構成  
 使用して、コンポーネントを構成する変換コンポーネントを作成するオプションを選択した後、**スクリプト変換エディター**です。 詳細については、次を参照してください。[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)です。  
  
 スクリプト コンポーネントで使用するスクリプト言語を選択するを設定する、 **[scriptlanguage]**プロパティを**スクリプト**のページ、**スクリプト変換エディター**ダイアログボックスです。  
  
> [!NOTE]  
>  既定のスクリプト、スクリプト コンポーネントの言語を設定するには、使用、**スクリプト言語** オプションを選択、**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、「 [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)」を参照してください。  
  
 データ フロー変換コンポーネントには 1 つの入力があり、1 つ以上の出力を設定できます。 使用してメタデータ デザイン モードで完了する必要のある手順のいずれかの入力と、コンポーネントの出力の構成は、**スクリプト変換エディター**カスタム スクリプトを記述する前に、します。  
  
### <a name="configuring-input-columns"></a>入力列の設定  
 スクリプト コンポーネントを使用して作成した変換コンポーネントには、1 つの入力があります。  
  
 **入力列**のページ、**スクリプト変換エディター**列のリスト、データ フローの上流コンポーネントの出力から使用可能な列を示しています。 変換する列、またはそのまま出力する列を選択します。 変換するすべての列の適切な場所に、読み取り/書き込みのマークを付けます。  
  
 詳細については、**入力列**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター (&) #40";"の入力列 ページ"&"#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)です。  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>入力、出力、および出力列の設定  
 変換コンポーネントには、1 つ以上の出力を設定できます。  
  
 通常、非同期出力型の変換には、2 つの出力を設定します。 たとえば、特定の市内にある住所を数えたい場合、1 つの出力に住所データをそのまま送り、もう 1 つの出力に集計結果を送信します。 集計結果を出力するには、新しい出力列も 1 つ必要です。  
  
 **入力と出力**のページ、**スクリプト変換エディター**既定では、1 つの出力が作成されましたが、出力列が作成されていないことを参照してください。 エディターのこのページでは、次の項目を設定できます。  
  
-   集計結果の出力など、1 つ以上の出力を追加して作成する場合は、 使用して、**出力の追加**と**出力の削除**ボタン、非同期変換コンポーネントの出力を管理します。 設定、 **SynchronousInputID**を 0 にするか、出力はだけでなく通過データは、上流コンポーネントから既存の行や列内の場所に変換には、各出力のプロパティです。 この設定によって、出力が入力に対して非同期になります。  
  
-   入力や出力にはわかりやすい名前を付けておくことができます。 スクリプト コンポーネントはこの名前を使用して、型指定されたアクセサー プロパティを生成します。これは、スクリプト内で入力や出力を参照するために使用できます。  
  
-   通常、非同期変換は列をデータ フローに追加します。 ときに、 **SynchronousInputID**出力のプロパティが 0 で、単に上流コンポーネントからデータを通過または追加して構成する必要があります、既存の行と列の場所で変換を示す、出力では使用できません出力に明示的に列を出力します。 出力列の名前は、マップ先の入力列と同じ名前にする必要はありません。  
  
-   追加情報を格納するために列を追加する場合があります。 その場合、追加した列にデータを格納するには、独自のコードを記述する必要があります。 標準エラー出力の動作を再現する方法については、次を参照してください。[スクリプト コンポーネントのエラー出力のシミュレート](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)です。  
  
 詳細については、**入力と出力**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター (&) #40 です。 入力し、呼び出し力 ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)です。  
  
### <a name="adding-variables"></a>変数の追加  
 既存の変数の値をスクリプトで使用する場合は、することができますで追加 ReadOnlyVariables プロパティおよび ReadWriteVariables プロパティ フィールドに、**スクリプト**のページ、**スクリプト変換エディター**.  
  
 プロパティ フィールドに複数の変数を追加する場合は、各変数名をコンマで区切ります。 省略記号ボタンをクリックして、複数の変数を選択することもできます (**.**) ボタンを**ReadOnlyVariables**と**ReadWriteVariables**プロパティ フィールド内の変数をクリックして、**変数を選択**ダイアログ ボックス。  
  
 スクリプト コンポーネントで変数を使用する方法に関する一般情報は、次を参照してください。[スクリプト コンポーネントで変数を使用して](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)です。  
  
 詳細については、**スクリプト**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター & #40 です。[スクリプト] ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a>コード デザイン モードでの非同期変換コンポーネントのスクリプト作成  
 コンポーネントのメタデータをすべて構成した後、カスタム スクリプトを記述できます。 **スクリプト変換エディター**の**スクリプト**] ページで [**スクリプトの編集**を開くには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDEここで、カスタム スクリプトを追加することができます。 使用するスクリプト言語が選択されているかどうかに依存[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Basic または[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual c# のスクリプト言語として、 **[scriptlanguage]**プロパティを**スクリプト**ページです。  
  
 スクリプト コンポーネントを使用して作成されたコンポーネントのすべての種類に適用される重要な情報について、次を参照してください。[コーディングおよびスクリプト コンポーネントのデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)です。  
  
### <a name="understanding-the-auto-generated-code"></a>自動生成されたコードについて  
 作成と編集可能な変換コンポーネントを構成した後で VSTA IDE を開くときに**ScriptMain**クラスが、ProcessInputRow および CreateNewOutputRows メソッド スタブのコード エディターに表示されます。 ScriptMain クラスとは、ここでは、カスタム コードを記述、ProcessInputRow 変換コンポーネントの最重要メソッドです。 **CreateNewOutputRows**メソッドは、通常より両方のコンポーネントは、独自の出力行を作成する必要がありますが、非同期変換に似ている変換元コンポーネントで使用します。  
  
 VSTA を開く場合**プロジェクト エクスプ ローラー**ウィンドウで、スクリプト コンポーネントが、読み取り専用生成も確認できます**BufferWrapper**と**ComponentWrapper**プロジェクト項目. ScriptMain クラスで UserComponent クラスから継承、 **ComponentWrapper**プロジェクト項目です。  
  
 データ フロー エンジンがで PrimeOutput メソッドを呼び出し、実行時に、 **UserComponent**クラスが優先、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>クラスの親です。 PrimeOutput メソッドは、CreateNewOutputRows メソッドを呼び出します。  
  
 次に、データ フロー エンジンは、メソッドを呼び出し、ProcessInput を上書きする UserComponent クラスで、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>クラスの親です。 さらに、ProcessInput メソッドは、入力バッファー内の行をループし、行ごとに 1 回 ProcessInputRow メソッドを呼び出します。  
  
### <a name="writing-your-custom-code"></a>カスタム コードの記述  
 カスタムの非同期変換コンポーネントの作成を完了するには、入力バッファーの行ごとにデータを処理するのに、オーバーライドした ProcessInputRow メソッドを使用する必要があります。 出力は入力に同期しないため、データの行を明示的に出力に書き込む必要があります。  
  
 変換では、非同期、ProcessInputRow または ProcessInput メソッド内から適切な出力に行を追加するのに AddRow メソッドを使用できます。 CreateNewOutputRows メソッドを使用する必要はありません。 特定の出力に、集計結果など、結果の単一行を作成している場合は、CreateNewOutputRows メソッドを使用してあらかじめ出力行を作成し、すべての入力行を処理した後、その値を入力します。 ただし効果的ではなく CreateNewOutputRows メソッドで複数の行を作成するため、スクリプト コンポーネントのみを使用できますの入力または出力を現在の行。 CreateNewOutputRows メソッドの方が重要では、ソース コンポーネントを処理する入力行がないです。  
  
 することも、ProcessInput メソッドをオーバーライドする追加準備処理や終了処理前に、または後と、入力バッファーをループして各行に対して ProcessInputRow を呼び出すを実行できるようにします。 たとえば、行を ProcessInputRow ループとして特定の市区町村内のアドレスの数をカウントする ProcessInput をオーバーライドこのトピックのコード例のいずれかの**します。** 例では、すべての行が処理された後、概要の値を 2 番目の出力に書き込みます。 例は、PostExecute が呼び出されたときに、出力バッファーを使用できることが不要になったために、ProcessInput に出力を完了します。  
  
 要件に応じてすることも、準備処理や最終処理を行うには、ScriptMain クラスで使用できる PreExecute、PostExecute メソッドでスクリプトを記述します。  
  
> [!NOTE]  
>  最初からカスタム データ フロー コンポーネントを開発していた場合は、出力バッファーへの参照をキャッシュする PrimeOutput メソッドをオーバーライドして、バッファーに行のデータを後で追加することができるようにする必要があります。 スクリプト コンポーネントでは必要ありませんがある、自動的に生成されたクラス内の各出力バッファーを表すため、 **BufferWrapper**プロジェクト項目です。  
  
## <a name="example"></a>例  
 この例では、ScriptMain クラスで非同期変換コンポーネントを作成するために必要なカスタム コードを示します。  
  
> [!NOTE]  
>  これらの例を使用して、 **Person.Address**テーブルに、 **AdventureWorks**サンプル データベースと、最初と 4 番目の列を渡す、 **intAddressID**と**nvarchar (30) 市区町村**をデータ フローの列です。 このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。 他の前提条件および仮定条件については、それぞれの例で説明します。  
  
 次の例では、2 つの出力を持つ非同期変換コンポーネントを示します。 この変換は、 **AddressID**と**市区町村**列を特定の都市 (Redmond、米国ワシントン州)、内にある住所の数をカウント中に 1 つの出力呼び出し力し、2 番目の出力結果として得られる値。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。  
  
2.  デザイナーで、変換元または他の変換の出力を、新しい変換コンポーネントに接続します。 この出力はからデータを提供する必要があります、 **Person.Address**のテーブル、 **AdventureWorks**を含むサンプル データベースには、少なくとも、 **AddressID**と**市区町村**列です。  
  
3.  開く、**スクリプト変換エディター**です。 **入力列**] ページで、[、 **AddressID**と**市区町村**列です。  
  
4.  **入力と出力**ページの追加および構成、 **AddressID**と**市区町村**最初の出力に列を出力します。 2 番目の出力を追加し、集計値を格納する出力列をその出力に追加します。 この例により各入力行が最初の出力に明示的にコピーされるため、最初の出力の SynchronousInputID プロパティを 0 に設定します。 新しく作成された出力の SynchronousInputID プロパティは既に 0 に設定されています。  
  
5.  入力、出力、および新しい出力列をわかりやすい名前に変更します。 この例では**MyAddressInput** 、入力の名前として**MyAddressOutput**と**MySummaryOutput** 、出力の場合と**MyRedmondCount** 、2 番目の出力の出力列です。  
  
6.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じると、**スクリプト変換エディター**です。  
  
7.  作成および構成が必要ですが、最初の出力の変換先コンポーネント、 **AddressID**と**市区町村**列など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、または変換先コンポーネントのサンプル示されている[スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)、します。 変換の最初の出力を接続**MyAddressOutput**、変換先コンポーネントにします。 コピー先のテーブルを作成するには、次を実行して[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンドを**AdventureWorks**データベース。  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  2 番目の出力に接続する別の変換先コンポーネントを作成して構成します。 変換の 2 番目の出力を接続**MySummaryOutput**、変換先コンポーネントにします。 2 番目の出力からは 1 つの値を格納した行が 1 つ出力されるだけなので、フラット ファイル接続マネージャーを使用して、1 つの列を含む新しいファイルに接続する設定を簡単に行うことができます。 例では、この変換先列の名前は**MyRedmondCount**です。  
  
9. サンプルを実行します。  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Private myRedmondAddressCount As Integer  
  
    Public Overrides Sub CreateNewOutputRows()  
  
        MySummaryOutputBuffer.AddRow()  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)  
  
        While Buffer.NextRow()  
            MyAddressInput_ProcessInputRow(Buffer)  
        End While  
  
        If Buffer.EndOfRowset Then  
            MyAddressOutputBuffer.SetEndOfRowset()  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount  
            MySummaryOutputBuffer.SetEndOfRowset()  
        End If  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With MyAddressOutputBuffer  
            .AddRow()  
            .AddressID = Row.AddressID  
            .City = Row.City  
        End With  
  
        If Row.City.ToUpper = "REDMOND" Then  
            myRedmondAddressCount += 1  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    private int myRedmondAddressCount;  
  
    public override void CreateNewOutputRows()  
    {  
  
        MySummaryOutputBuffer.AddRow();  
  
    }  
  
    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)  
    {  
  
        while (Buffer.NextRow())  
        {  
            MyAddressInput_ProcessInputRow(Buffer);  
        }  
  
        if (Buffer.EndOfRowset())  
        {  
            MyAddressOutputBuffer.SetEndOfRowset();  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;  
            MySummaryOutputBuffer.SetEndOfRowset();  
        }  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            MyAddressOutputBuffer.AddRow();  
            MyAddressOutputBuffer.AddressID = Row.AddressID;  
            MyAddressOutputBuffer.City = Row.City;  
        }  
  
        if (Row.City.ToUpper() == "REDMOND")  
        {  
            myRedmondAddressCount += 1;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [同期および非同期変換を理解します。](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)   
 [スクリプト コンポーネントによる同期変換の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
 [非同期出力型のカスタム変換コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
  
  
