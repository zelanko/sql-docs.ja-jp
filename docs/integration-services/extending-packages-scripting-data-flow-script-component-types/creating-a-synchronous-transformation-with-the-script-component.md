---
title: "スクリプト コンポーネントによる同期変換の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-data-flow-script-component-types
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
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
caps.latest.revision: 64
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3d4a507c31f77449aba7eb884c39bf68c7c78581
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a>スクリプト コンポーネントによる同期変換の作成
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内で変換コンポーネントを使用することにより、変換元から変換先にデータが受け渡される過程で、データを修正または分析できます。 同期出力型の変換では、各入力列はコンポーネントを通過するたびに処理されます。 非同期出力型の変換では、処理を完了するための入力列をすべて受け取ってから、処理が行われます。 このトピックでは、同期変換について説明します。 非同期変換の詳細については、次を参照してください。[スクリプト コンポーネントによる非同期変換の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)です。 同期および非同期のコンポーネント間の違いの詳細については、次を参照してください。[について同期および非同期変換](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)です。  
  
 スクリプト コンポーネントの概要については、次を参照してください。[スクリプト コンポーネントによるデータ フローの拡張](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)です。  
  
 スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。 ただし、スクリプト コンポーネントのしくみを理解する有用なことのセクションで、カスタム データ フロー コンポーネントの開発に必要な手順を読んで、[カスタム データ フロー コンポーネントを開発](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)、特に[同期出力型のカスタム変換コンポーネントの開発](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)です。  
  
## <a name="getting-started-with-a-synchronous-transformation-component"></a>同期変換コンポーネントの概要  
 [データ フロー] ペインにスクリプト コンポーネントを追加すると[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナー、**スクリプト コンポーネントの種類の選択** ダイアログ ボックスが開き、変換元、変換先、または変換コンポーネントの種類を選択するように求められます。 このダイアログ ボックスで選択**変換**です。  
  
## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a>メタデータ デザイン モードでの同期変換コンポーネントの構成  
 使用して、コンポーネントを構成する変換コンポーネントを作成するオプションを選択した後、**スクリプト変換エディター**です。 詳細については、次を参照してください。[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)です。  
  
 スクリプト コンポーネントのスクリプト言語を設定するに設定する、 **[scriptlanguage]**プロパティを**スクリプト**のページ、**スクリプト変換エディター**です。  
  
> [!NOTE]  
>  既定のスクリプト、スクリプト コンポーネントの言語を設定するには、使用、**スクリプト言語** オプションを選択、**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、次を参照してください。 [eneral ページ](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)です。  
  
 データ フロー変換コンポーネントは、1 つの入力を持ち、1 つまたは複数の出力をサポートします。 コンポーネントを使用して、メタデータ デザイン モードで完了する必要がありますのある作業の 1 つの入力と出力の構成、**スクリプト変換エディター**カスタム スクリプトを記述する前に、します。  
  
### <a name="configuring-input-columns"></a>入力列の設定  
 変換コンポーネントには 1 つの入力があります。  
  
 **入力列**のページ、**スクリプト変換エディター、**列リスト データ フローの上流コンポーネントの出力から使用可能な列を示しています。 変換する列、またはそのまま出力する列を選択します。 変換するすべての列の適切な場所に、読み取り/書き込みのマークを付けます。  
  
 詳細については、**入力列**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター &#40;の入力列 ページ"&"#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)です。  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>入力、出力、および出力列の設定  
 変換コンポーネントには、1 つ以上の出力を設定できます。  
  
 **入力と出力**のページ、**スクリプト変換エディター**、1 つの出力が作成されましたが、出力に列がないことを確認できます。 エディターのこのページで、必要に応じて以下の項目を設定します。  
  
-   予期しない値を含む行に対するシミュレートされたエラー出力など、1 つ以上の出力を追加して作成する場合は、 使用して、**出力の追加**と**出力の削除**ボタン、同期変換コンポーネントの出力を管理します。 すべての入力行は、使用できるすべての出力に送信されます。ただし、各行を出力のうちいずれか 1 つにリダイレクトするように指定した場合を除きます。 ゼロ以外の整数値を指定して行をリダイレクトすることを指定する、 **ExclusionGroup**プロパティを出力します。 特定の整数値で入力**ExclusionGroup**出力を識別する、大きな違いはありませんが、指定された出力のグループを一貫して同じ整数を使用する必要があります。  
  
    > [!NOTE]  
    >  0 以外を使用することもできます。 **ExclusionGroup**すべての行を出力したくない場合に、1 つの出力を持つプロパティ値。 ただし、ここでは、明示的に呼び出す必要があります、 **DirectRowTo\<outputbuffer >**行ごとに、出力に送信するメソッド。  
  
-   入力および出力に、わかりやすい名前を割り当てます。 スクリプト コンポーネントはこの名前を使用して、型指定されたアクセサー プロパティを生成します。これは、スクリプト内で入力や出力を参照するために使用できます。  
  
-   同期変換の列は現状のままにしておきます。 通常、同期変換はデータ フローに列を追加しません。 データはバッファーの所定の位置で変更され、バッファーがデータ フロー内の次のコンポーネントに渡されます。 このような場合、変換の出力に対して明示的に出力列を追加したり構成する必要はありません。 出力がエディターに表示される際、明示的に定義された列は含まれません。  
  
-   行レベルのエラー用のシミュレートされたエラー出力に新しい列を追加します。 複数の同じ出力に通常**ExclusionGroup**出力列のセットが同じです。 ただし、シミュレートされたエラー出力を作成するには、エラー情報を格納するために列の追加が必要となる場合があります。 データ フロー エンジンの方法については、エラー行を処理するを参照してください。[データ フロー コンポーネントでエラー出力を使用して](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)です。 スクリプト コンポーネントでは、独自のコードを記述して、追加した列に該当するエラー情報を格納する必要があるので注意してください。 詳細については、次を参照してください。[スクリプト コンポーネントのエラー出力のシミュレート](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)です。  
  
 詳細については、**入力と出力**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター (&) #40 です。 入力し、呼び出し力 ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)です。  
  
### <a name="adding-variables"></a>変数の追加  
 スクリプトで既存の変数を使用する場合でそれらを追加、 **ReadOnlyVariables**と**ReadWriteVariables**プロパティのフィールド、**スクリプト**のページ、**スクリプト変換エディター**です。  
  
 プロパティ フィールドに複数の変数を追加する場合は、各変数名をコンマで区切ります。 省略記号ボタンをクリックして、複数の変数を選択することもできます (**.**) ボタンを**ReadOnlyVariables**と**ReadWriteVariables**プロパティ フィールド内の変数をクリックして、**変数を選択**ダイアログ ボックス。  
  
 スクリプト コンポーネントで変数を使用する方法に関する一般情報は、次を参照してください。[スクリプト コンポーネントで変数を使用して](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)です。  
  
 詳細については、**スクリプト**のページ、**スクリプト変換エディター**を参照してください[スクリプト変換エディター &#40;です。[スクリプト] ページ &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a>コード デザイン モードでの同期変換コンポーネントのスクリプト作成  
 コンポーネントのメタデータを構成した後、カスタム スクリプトを記述できます。 **スクリプト変換エディター**の**スクリプト**] ページで [**スクリプトの編集**を開くには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDEここで、カスタム スクリプトを追加することができます。 使用するスクリプト言語が選択されているかどうかに依存[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Basic または[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual c# のスクリプト言語として、 **[scriptlanguage]**プロパティを**スクリプト**ページです。  
  
 スクリプト コンポーネントを使用して作成されたコンポーネントのすべての種類に適用される重要な情報について、次を参照してください。[コーディングおよびスクリプト コンポーネントのデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)です。  
  
### <a name="understanding-the-auto-generated-code"></a>自動生成されたコードについて  
 開くと、VSTA IDE を作成した後、編集可能な変換コンポーネントの構成**ScriptMain**のスタブをコード エディターでクラスが表示されます、 **ProcessInputRow**メソッドです。 **ScriptMain**クラスは、カスタム コードを記述して**ProcessInputRow**変換コンポーネントで最も重要なメソッドです。  
  
 開く場合、**プロジェクト エクスプ ローラー** VSTA のウィンドウで、スクリプト コンポーネントが、読み取り専用生成も確認できます**BufferWrapper**と**ComponentWrapper**プロジェクト項目。 **ScriptMain**クラスから継承、 **UserComponent**クラス内で、 **ComponentWrapper**プロジェクト項目です。  
  
 データ フロー エンジンを起動、実行時に、 **ProcessInput**メソッドで、 **UserComponent**クラスが優先、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>クラスの親です。 **ProcessInput**メソッドがさらに、入力バッファーと呼び出し内の行をループ処理、 **ProcessInputRow**メソッドを行ごとに 1 回です。  
  
### <a name="writing-your-custom-code"></a>カスタム コードの記述  
 同期出力型の変換コンポーネントは、記述するすべてのデータ フロー コンポーネントの中で最も単純です。 たとえば、このトピックの単一出力の例は、次のカスタム コードで構成されています。  
  
```vb  
Row.City = UCase(Row.City)  
```  
  
```csharp  
Row.City = (Row.City).ToUpper();  
  
```  
  
 カスタムの同期変換コンポーネントの作成を完了するには、使用する、オーバーライドされた**ProcessInputRow**入力バッファーの行ごとにデータを変換するメソッド。 データ フロー エンジンは、バッファーがいっぱいになると、データ フロー内の次のコンポーネントにこのバッファーを渡します。  
  
 要件に応じてすることもスクリプトを記述、 **PreExecute**と**PostExecute**で使用できるメソッド、 **ScriptMain**を実行するクラス準備処理や最終処理します。  
  
### <a name="working-with-multiple-outputs"></a>複数の出力の処理  
 使用できる 2 つ以上の出力のいずれかに入力行を送信する場合でも、前述した単一出力の例と比べて、必要なカスタム コードはそれほど多くありません。 たとえば、このトピックの 2 つの出力の例は、次のカスタム コードで構成されています。  
  
```vb  
Row.City = UCase(Row.City)  
If Row.City = "REDMOND" Then  
    Row.DirectRowToMyRedmondAddresses()  
Else  
    Row.DirectRowToMyOtherAddresses()  
End If  
```  
  
```csharp  
Row.City = (Row.City).ToUpper();  
  
if (Row.City=="REDMOND")  
{  
    Row.DirectRowToMyRedmondAddresses();  
}  
else  
{  
    Row.DirectRowToMyOtherAddresses();  
}  
```  
  
 この例では、スクリプト コンポーネントが生成されます、 **DirectRowTo\<OutputBufferX >**方法は、構成した出力の名前に基づいています。 同様のコードを使用して、シミュレートされたエラー出力にエラー行を送信することもできます。  
  
## <a name="examples"></a>使用例  
 ここで例で必要なカスタム コード、 **ScriptMain**同期変換コンポーネントを作成するクラス。  
  
> [!NOTE]  
>  これらの例を使用して、 **Person.Address**テーブルに、 **AdventureWorks**サンプル データベースと、最初と 4 番目の列を渡す、 **intAddressID**と**nvarchar (30) 市区町村**をデータ フローの列です。 このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。 他の前提条件および仮定条件については、それぞれの例で説明します。  
  
### <a name="single-output-synchronous-transformation-example"></a>単一出力の同期変換の例  
 この例では、単一の出力が含まれる同期変換コンポーネントを示します。 この変換は、 **AddressID**列に変換し、**市区町村**列を大文字にします。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。  
  
2.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、変換元または他の変換の出力を、新しい変換コンポーネントに接続します。 この出力はからデータを提供する必要があります、 **Person.Address**のテーブル、 **AdventureWorks**サンプル データベースを含む、 **AddressID**と**都市**列です。  
  
3.  開く、**スクリプト変換エディター**です。 **入力列**] ページで、[、 **AddressID**と**市区町村**列です。 マーク、**市区町村**列を読み取り/書き込みとして。  
  
4.  **入力と出力** ページで、入力の名前を変更してなど、わかりやすい名前を持つ出力**MyAddressInput**と**MyAddressOutput**です。 注意して、 **SynchronousInputID**に対応する出力の**ID**入力します。 したがって、出力列を追加して設定する必要はありません。  
  
5.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じると、**スクリプト変換エディター**です。  
  
6.  作成および構成が必要ですの変換先コンポーネント、 **AddressID**と**市区町村**列など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に示されている変換先、または変換先コンポーネントのサンプル[スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)です。 変換の出力を変換先コンポーネントに接続します。 コピー先のテーブルを作成するには、次を実行して[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンドを**AdventureWorks**データベース。  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
7.  サンプルを実行します。  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        Row.City = UCase(Row.City)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        Row.City = (Row.City).ToUpper();  
  
    }  
  
}  
```  
  
### <a name="two-output-synchronous-transformation-example"></a>2 つの出力の同期変換の例  
 この例では、2 つの出力を持つ同期変換コンポーネントを示します。 この変換は、 **AddressID**列に変換し、**市区町村**列を大文字にします。 都市名が Redmond の場合、変換はその行を 1 つの出力に送信し、他のすべての行をもう 1 つの出力に送信します。  
  
 このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。  
  
1.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。  
  
2.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、変換元または他の変換の出力を、新しい変換コンポーネントに接続します。 この出力はからデータを提供する必要があります、 **Person.Address**のテーブル、 **AdventureWorks**を含むサンプル データベースには、少なくとも、 **AddressID**と**市区町村**列です。  
  
3.  開く、**スクリプト変換エディター**です。 **入力列**] ページで、[、 **AddressID**と**市区町村**列です。 マーク、**市区町村**列を読み取り/書き込みとして。  
  
4.  **入力と出力** ページで、2 番目の出力を作成します。 新しい出力を追加した後に設定することを確認してください、 **SynchronousInputID**を**ID**入力します。 このプロパティは、既定として作成された最初の出力で既に設定されています。 各出力の設定、 **ExclusionGroup**プロパティが相互に排他的な 2 つの出力の間での入力行に分割することを示すために同じ 0 以外の値にします。 出力列を出力に追加する必要はありません。  
  
5.  名前を変更、入力呼び出し力、わかりやすい名前を持つよう**MyAddressInput**、 **MyRedmondAddresses**、および**MyOtherAddresses**です。  
  
6.  **スクリプト**] ページで [**スクリプトの編集**と次のスクリプトを入力します。 スクリプト開発環境を閉じると、**スクリプト変換エディター**です。  
  
7.  作成および構成する 2 つの変換先コンポーネントを**AddressID**と**市区町村**列など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、フラット ファイル変換先、または変換先コンポーネントのサンプル示されている[スクリプト コンポーネントによる変換先の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)です。 変換の各出力をいずれかの変換先コンポーネントに接続します。 実行して、変換先テーブルを作成することができます、 [!INCLUDE[tsql](../../includes/tsql-md.md)] (の一意のテーブル名) では、次のようなコマンド、 **AdventureWorks**データベース。  
  
    ```sql
    CREATE TABLE [Person].[Address2](  
        [AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL  
    ```  
  
8.  サンプルを実行します。  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        Row.City = UCase(Row.City)  
  
        If Row.City = "REDMOND" Then  
            Row.DirectRowToMyRedmondAddresses()  
        Else  
            Row.DirectRowToMyOtherAddresses()  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        Row.City = (Row.City).ToUpper();  
  
        if (Row.City == "REDMOND")  
        {  
            Row.DirectRowToMyRedmondAddresses();  
        }  
        else  
        {  
            Row.DirectRowToMyOtherAddresses();  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [同期および非同期変換を理解する](~/integration-services/understanding-synchronous-and-asynchronous-transformations.md   
 [スクリプト コンポーネントによる非同期変換の作成](~/integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md   
 [同期出力型のカスタム変換コンポーネントの開発](~/integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md  
  
  



