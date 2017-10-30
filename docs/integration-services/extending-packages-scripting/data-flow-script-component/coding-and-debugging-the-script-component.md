---
title: "コーディングおよびスクリプト コンポーネントのデバッグ |Microsoft ドキュメント"
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
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ff6c9814547a83439717f8a88d3bd52be80c4ca5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-component"></a>スクリプト コンポーネントのコーディングおよびデバッグ
  [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでは、スクリプト コンポーネントにメタデータ デザイン モードとコード デザイン モードの 2 つのモードがあります。 開くと、**スクリプト変換エディター**コンポーネントがメタデータ デザイン モードでをメタデータの構成し、コンポーネントのプロパティの設定を入力します。 メタデータ デザイン モードで、スクリプト コンポーネントのプロパティを設定して、入力と出力を構成したら、コード デザイン モードに切り替えてカスタム スクリプトを記述できます。 メタデータ デザイン モードとコード デザイン モードの詳細については、次を参照してください。[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)です。  
  
## <a name="writing-the-script-in-code-design-mode"></a>コード デザイン モードでのスクリプトの記述  
  
### <a name="script-component-development-environment"></a>スクリプト コンポーネント開発環境  
 スクリプトを作成するをクリックして**スクリプトの編集**上、**スクリプト**のページ、**スクリプト変換エディター**を開くには、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE です。 VSTA IDE には、色分け表示が可能な [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] エディター、IntelliSense、オブジェクト ブラウザーなど、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET 環境での標準機能がすべて含まれています。  
  
 スクリプト コードは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# で記述されます。 スクリプト言語の設定を指定する、 **[scriptlanguage]**プロパティに、**スクリプト変換エディター**です。 その他のプログラミング言語を使用する場合は、選択した言語でカスタム アセンブリを作成し、スクリプト コンポーネント内のコードからその機能を呼び出すことができます。  
  
 スクリプト コンポーネントで作成したスクリプトは、パッケージ定義に格納されます。 スクリプト ファイルが別途存在するわけではありません。 したがって、スクリプト コンポーネントを使用してもパッケージの配置には影響しません。  
  
> [!NOTE]  
>  パッケージをデザインする際、スクリプト コードは一時的にプロジェクト ファイルに書き込まれます。 ファイルに機密情報を格納する潜在的なセキュリティ リスクがあるために、スクリプト コードでのパスワードなどの機密情報を含めないことをお勧めします。  
  
 既定では、 **Option Strict** IDE では無効です。  
  
### <a name="script-component-project-structure"></a>スクリプト コンポーネント プロジェクトの構造  
 スクリプト コンポーネントの威力は、インフラストラクチャ コードを生成して、記述する必要のあるコード量を減らす機能にあります。 この機能を実現するには、入力と出力、およびその列とプロパティが固定され、既知である必要があります。 したがって、コンポーネントのメタデータに後で変更を加えた場合、記述したコードが無効になり、 パッケージの実行中にコンパイル エラーが発生する可能性があります。  
  
#### <a name="project-items-and-classes-in-the-script-component-project"></a>スクリプト コンポーネント プロジェクトのプロジェクト アイテムおよびクラス  
 コード デザイン モードに切り替えると、VSTA IDE が開き、表示されます、 **ScriptMain**プロジェクト項目です。 **ScriptMain**プロジェクト項目が含まれていますが、編集可能な**ScriptMain**エントリとして機能するが、スクリプトをポイントし、これは、コードを記述するクラス。 クラスのコード要素は、スクリプト タスクの選択したプログラミング言語によって異なります。  
  
 スクリプト プロジェクトには、次の 2 つの読み取り専用のプロジェクト アイテムが自動生成され、追加されます。  
  
-   **ComponentWrapper**プロジェクト項目には、3 つのクラスが含まれています。  
  
    -   **UserComponent**から継承されるクラスが<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>メソッドとデータを処理して、パッケージとのやり取りに使用するプロパティが含まれています。 **ScriptMain**クラスから継承、 **UserComponent**クラスです。  
  
    -   A**接続**スクリプト変換エディターの接続マネージャー ページで選択した接続への参照を含むコレクション クラスです。  
  
    -   A**変数**コレクション クラスに入力された変数への参照を含む、 **ReadOnlyVariable**と**ReadWriteVariables**プロパティを**スクリプト**のページ、**スクリプト変換エディター**です。  
  
-   **BufferWrapper**プロジェクト アイテムにはから継承するクラスが含まれています<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>各入力呼び出し力に構成されているため、**入力と出力**のページ、**スクリプト変換エディター**です。 これらの各クラスには、構成された入力列と出力列、およびそれらの列が含まれるデータ フロー バッファーに対応する、型指定されたアクセサー プロパティが含まれています。  
  
 これらのオブジェクト、メソッド、およびプロパティを使用する方法については、次を参照してください。[スクリプト コンポーネント オブジェクト モデルについて](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)です。 スクリプト コンポーネントの特定の種類でこれらのクラスのプロパティとメソッドを使用する方法については、セクションを参照して[スクリプト コンポーネントの他の例](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)です。 サンプルについてのトピックでは、完全なコード例も示します。  
  
 スクリプト コンポーネント変換として構成するときに、 **ScriptMain**プロジェクト項目には、次の自動生成されたコードが含まれています。 コード テンプレートでも、スクリプト コンポーネントの概要、および、変数、イベント、接続など、SSIS オブジェクトを取得および操作する方法に関する追加情報を提供します。  
  
```vb  
' Microsoft SQL Server Integration Services Script Component  
' Write scripts using Microsoft Visual Basic 2008.  
' ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
  
<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _  
<CLSCompliant(False)> _  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub PreExecute()  
        MyBase.PreExecute()  
        '  
        ' Add your code here for preprocessing or remove if not needed  
        '  
    End Sub  
  
    Public Overrides Sub PostExecute()  
        MyBase.PostExecute()  
        '  
        ' Add your code here for postprocessing or remove if not needed  
        ' You can set read/write variables here, for example:  
        ' Me.Variables.MyIntVar = 100  
        '  
    End Sub  
  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
        '  
        ' Add your code here  
        '  
    End Sub  
  
End Class  
```  
  
```csharp  
/* Microsoft SQL Server Integration Services user script component  
*  Write scripts using Microsoft Visual C# 2008.  
*  ScriptMain is the entry point class of the script.*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]  
public class ScriptMain : UserComponent  
{  
  
    public override void PreExecute()  
    {  
        base.PreExecute();  
        /*  
          Add your code here for preprocessing or remove if not needed  
        */  
    }  
  
    public override void PostExecute()  
    {  
        base.PostExecute();  
        /*  
          Add your code here for postprocessing or remove if not needed  
          You can set read/write variables here, for example:  
          Variables.MyIntVar = 100  
        */  
    }  
  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
        /*  
          Add your code here  
        */  
    }  
  
}  
```  
  
#### <a name="additional-project-items-in-the-script-component-project"></a>スクリプト コンポーネント プロジェクトのその他のプロジェクト アイテム  
 スクリプト コンポーネント プロジェクトが既定値以外のアイテムを含めることができます**ScriptMain**項目。 プロジェクトには、クラス、モジュール、コード ファイル、およびフォルダーを追加できます。また、フォルダーを使用してアイテムのグループを整理できます。  
  
 追加したすべてのアイテムは、パッケージ内部に保存されます。  
  
#### <a name="references-in-the-script-component-project"></a>スクリプト コンポーネント プロジェクトの参照  
 マネージ アセンブリへの参照を追加するには、スクリプト タスクでプロジェクトを右クリックして**プロジェクト エクスプ ローラー**、クリックして**参照の追加**です。 詳細については、次を参照してください。[スクリプト ソリューションでその他のアセンブリを参照している](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)です。  
  
> [!NOTE]  
>  プロジェクト参照を表示するには、VSTA IDE 内で**クラス ビュー**または**プロジェクト エクスプ ローラー**です。 これらのウィンドウからのいずれかを開く、**ビュー**メニュー。 新しい参照を追加することができます、**プロジェクト** メニューから**プロジェクト エクスプ ローラー**、またはから**クラス ビュー**です。  
  
## <a name="interacting-with-the-package-in-the-script-component"></a>スクリプト コンポーネント内でのパッケージとの対話  
 スクリプト コンポーネント内で記述するカスタム スクリプトは、自動生成された基本クラス内の、厳密に型指定されたアクセサーを使用して、コンポーネントに含まれているパッケージの変数や接続マネージャーにアクセスし、それらを使用できます。 ただし、変数および接続マネージャーをスクリプトで使用できるようにするには、コード デザイン モードに切り替える前に、その両方を設定する必要があります。 また、スクリプト コンポーネントのコードから、イベントを発生させたり、ログ記録を実行することもできます。  
  
 スクリプト コンポーネント プロジェクト内に自動生成されるプロジェクト アイテムには、パッケージと情報をやり取りするために、以下のオブジェクト、メソッド、およびプロパティが用意されています。  
  
|パッケージの機能|アクセス方法|  
|---------------------|-------------------|  
|変数|名前付きの型指定されたアクセサー プロパティを使用して、**変数**コレクション クラスに、 **ComponentWrapper**を通じて公開されるプロジェクト アイテム、**変数**のプロパティ、 **ScriptMain**クラスです。<br /><br /> **PreExecute**メソッドには、読み取り専用変数のみがアクセスできます。 **PostExecute**メソッド読み取り専用の両方にアクセスして読み取り/書き込み変数です。|  
|接続|名前付きの型指定されたアクセサー プロパティを使用して、**接続**コレクション クラスに、 **ComponentWrapper**を通じて公開されるプロジェクト アイテム、**接続**のプロパティ、 **ScriptMain**クラスです。|  
|イベント|使用してイベントを発生させる、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>のプロパティ、 **ScriptMain**クラスおよび**火災\<X >**のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>インターフェイスです。|  
|ログ記録|使用してログ記録を実行、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>のメソッド、 **ScriptMain**クラスです。|  
  
## <a name="debugging-the-script-component"></a>スクリプト コンポーネントのデバッグ  
 スクリプト コンポーネントのコードをデバッグするには、コードに少なくとも 1 つのブレークポイントを設定し、VSTA IDE を閉じて [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。 パッケージが実行されてスクリプト コンポーネントが開始されると、VSTA IDE が再度開き、読み取り専用モードでコードが表示されます。 実行によりブレークポイントに到達したら、変数の値の検証や、残りのコードのステップ スルーができます。  
  
> [!NOTE]  
>  パッケージ実行タスクから実行されている子パッケージの一部としてスクリプト コンポーネントを実行する場合は、スクリプト コンポーネントをデバッグできません。 このような場合は、子パッケージのスクリプト コンポーネント内で設定したブレークポイントは無視されます。 子パッケージを単独で実行することにより、通常どおりパッケージをデバッグできます。  
  
> [!NOTE]  
>  複数のスクリプト コンポーネントが含まれるパッケージをデバッグする場合、デバッガーによってデバッグされるスクリプト コンポーネントは 1 つです。 Foreach ループまたは For ループ コンテナーの場合と同様に、デバッガーが完了した場合、システムは別のスクリプト コンポーネントをデバッグできます。  
  
 ただし、次の方法を使用することにより、スクリプト コンポーネントの実行を監視することもできます。  
  
-   実行を中断しを使用して、モーダル メッセージを表示、 **MessageBox.Show**メソッドで、 **System.Windows.Forms**名前空間。 デバッグが完了したら、このコードは削除してください。  
  
-   情報メッセージ、警告、およびエラーを発生させます。 FireInformation、FireWarning、および FireError メソッドは、Visual Studio で、イベントの説明を表示**出力**ウィンドウです。 ただし、FireProgress メソッド、Console.Write メソッド、および Console.WriteLine メソッド情報を表示しない任意で、**出力**ウィンドウです。 FireProgress イベントからのメッセージが表示される、**進行**のタブ[!INCLUDE[ssIS](../../../includes/ssis-md.md)]デザイナー。 詳細については、次を参照してください。[スクリプト コンポーネントでのイベントの発生](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)です。  
  
-   イベントまたはユーザー定義のメッセージを、有効なログ プロバイダーに記録します。 詳細については、次を参照してください。[スクリプト コンポーネントでのログ記録](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)です。  
  
 宛先にデータを保存せず、ソースまたは変換として構成されているスクリプト コンポーネントの出力を確認する場合は、使用してデータ フローを停止することができます、 [Row Count Transformation](../../../integration-services/data-flow/transformations/row-count-transformation.md)とスクリプト コンポーネントの出力にデータ ビューアーをアタッチします。 データ ビューアーの詳細については、次を参照してください。[データ フローのデバッグ](../../../integration-services/troubleshooting/debugging-data-flow.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 スクリプト コンポーネントのコーディングの詳細については、このセクションの次のトピックを参照してください。  
  
 [スクリプト コンポーネント オブジェクト モデルをについてください。](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 スクリプト コンポーネントで使用できる、オブジェクト、メソッド、およびプロパティの使用方法について説明します。  
  
 [スクリプティング ソリューションの他のアセンブリを参照します。](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 スクリプト コンポーネントで、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] クラス ライブラリのオブジェクトを参照する方法について説明します。  
  
 [スクリプト コンポーネントのエラー出力のシミュレート](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 スクリプト コンポーネントによる処理中にエラーを発生させる行の、エラー出力のシミュレーション方法について説明します。  
  
## <a name="external-resources"></a>外部リソース  
  
-   ブログ エントリ「 [VSTA のセットアップと構成に関する問題の SSIS 2008 および R2 インストール](http://go.microsoft.com/fwlink/?LinkId=215661)、blogs.msdn.com です。  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成します。](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
  
  

