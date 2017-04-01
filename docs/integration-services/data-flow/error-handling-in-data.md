---
title: "データのエラー処理 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.configureerroroutput.f1"
helpviewer_keywords: 
  - "データの切り捨て"
  - "データ変換エラー [Integration Services]"
  - "エラー [Integration Services], データ フロー コンポーネント"
  - "参照 [Integration Services]"
  - "エラー [Integration Services]"
  - "エラー [Integration Services], データ フロー出力"
  - "エラー出力 [Integration Services]"
  - "データ フロー [Integration Services], エラー"
  - "式 [Integration Services], エラー"
ms.assetid: c61667b4-25cb-4d45-a52f-a733e32863f4
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 62
---
# データのエラー処理
  データ フロー コンポーネントが変換を列データに適用したり、変換元のデータを抽出したり、変換先にデータを読み込んだりするときに、エラーが発生する場合があります。 エラーが発生する原因の主なものは、予期しないデータ値です。 たとえば、数字ではなく文字列が列に含まれる場合、データ変換は失敗します。また、データは日付データであるが列のデータ型は数値の場合、データベース列への挿入は失敗します。あるいは、列の値が 0 の場合に数学的演算の結果が無効となり、それが原因で式の評価が失敗します。  
  
 エラーは一般的に、次のカテゴリのいずれかに分類されます。  
  
-   データ変換エラー。変換により、有効桁の損失、有効桁以外の桁の損失、および文字列の切り捨てなどの結果が返された場合に発生します。 要求された変換がサポートされていない場合にも、データ変換エラーは発生します。  
  
-   式の評価エラー。実行時に評価される式が無効な演算を実行したり、データ値の不足または無効のため構文的に間違った状態になる場合に発生します。  
  
-   参照エラー。参照操作が、参照テーブル内で一致を見つけられなかった場合に発生します。  
  
 Integration Services のエラー、警告、および他のメッセージの一覧については、「 [Integration Services Error and Message Reference](../../integration-services/integration-services-error-and-message-reference.md)」を参照してください。  
  
## エラー出力での行レベル エラーのキャプチャ  
 多くのデータ フロー コンポーネントではエラー出力がサポートされています。これを利用すると、コンポーネントが行う、入力データと出力データの両方での行レベルのエラー処理の方法を制御できます。 入力または出力の個々の列にオプションを設定することにより、切り捨てまたはエラーが発生したときのコンポーネントの動作方法を指定します。 たとえば、顧客名のデータが切り捨てられたときは失敗するが、それよりも重要でないデータが含まれる別の列で切り捨てが発生した場合はエラーを無視するように、コンポーネントを指定できます。  
  
 エラー出力は、別の変換の入力に連結したり、エラー出力以外の別の変換先に読み込むことができます。 たとえば、エラー出力は、空白列に文字列を提供する派生列変換に連結できます。  
  
 次の図は、エラー出力が含まれる簡単なデータ フローを示しています。  
  
 ![エラー出力のあるデータ フロー](../../integration-services/data-flow/media/mw-dts-11.gif "エラー出力のあるデータ フロー")  
  
 詳細については、「[データ フロー](../../integration-services/data-flow/data-flow.md)」と「[Integration Services のパス](../../integration-services/data-flow/integration-services-paths.md)」を参照してください。  
  
## エラーと切り捨て  
 エラーは、エラーまたは切り捨ての、2 つのカテゴリのいずれかに分類されます。  
  
 **エラー**。 エラーは決定的な失敗を示し、NULL 値の結果を生成します。 このようなエラーには、データ変換エラーまたは式の評価エラーが含まれます。 たとえば、英文字が含まれる文字列を数字に変換しようとすると、エラーが発生します。 データ変換、式の評価、および変数、プロパティ、データ列への式の結果の割り当ては、無効なキャストおよび互換性のないデータ型のために失敗する場合があります。 詳細については、「[Cast &#40;SSIS 式&#41;](../../integration-services/expressions/cast-ssis-expression.md)[式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md), 」、および「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
 **切り捨て**。 切り捨ては、エラーほど重大ではありません。 切り捨てによって生成される結果は、使用できる場合も、むしろ望ましい場合もあります。 切り捨てをエラーとして扱うか、または許容できる条件として扱うかを選択できます。 たとえば、15 文字の文字列を、文字幅が 1 文字のみの列に挿入する場合、文字列の切り捨てを選択できます。  
  
## エラー処理オプションの選択  
 変換元、変換、および変換先によるエラーと切り捨ての処理方法を構成できます。 次の表では、このオプションについて説明します。  
  
|オプション|Description|  
|------------|-----------------|  
|エラー コンポーネント|エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 [失敗] は、エラーおよび切り捨ての既定のオプションです。|  
|エラーを無視する|エラーまたは切り捨ては無視され、データ行は変換または変換元の出力に送られます。|  
|行のリダイレクト|エラーまたは切り捨てのデータ行は、変換元、変換、または変換先のエラー出力に送られます。|  
  
## エラーに関する詳細の取得  
 データ列の他に、エラー出力には **ErrorCode** 列と **ErrorColumn** 列が含まれています。 **ErrorCode** 列はエラーを識別し、 **ErrorColumn** 列にはエラー列の系列 ID が含まれます。  
  
 状況によっては、 **ErrorColumn** 列の値が 0 に設定されていることがあります。 これは、エラー状態が 1 列ではなく行全体に影響していることを示します。 たとえば、参照変換で参照に失敗した場合などです。  
  
 この 2 つの数値は、対応するエラーの説明と列の名前がないとあまり役に立ちません。 エラーの説明と列の名前を取得する方法をいくつか次に示します。  
  
-   エラーの説明と列の名前の両方を確認するには、データ ビューアーをエラー出力にアタッチします。 SSIS デザイナーで、エラー出力を指す赤の矢印を右クリックし、**[データ ビューアーを有効にする]** を選択します。  
  
-   列の名前を確認するには、ログ記録を有効にして、 **DiagnosticEx** イベントを選択します。 このイベントは、データ フロー列マップをログに書き込みます。 その後、この列マップの識別子から列名を参照できます。 **DiagnosticEx** イベントでは XML 出力に含まれる空白が維持されないので、ログのサイズを軽減できます。 読みやすくするために、XML 書式と構文の強調表示をサポートする XML エディター (たとえば Visual Studio) にログをコピーします。 ログ記録の詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」を参照してください。  
  
     データ フロー列マップの例を次に示します。  
  
    ```xml  
  
    <DTS:PipelineColumnMap xmlns:DTS="www.microsoft.com/SqlServer/Dts">  
        <DTS:Pipeline DTS:Path="\Package\Data Flow Task">  
            <DTS:Column DTS:ID="11" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Customer]"/>  
            <DTS:Column DTS:ID="12" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Product]"/>  
            <DTS:Column DTS:ID="13" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Price]"/>  
            <DTS:Column DTS:ID="14" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Timestamp]"/>  
            <DTS:Column DTS:ID="20" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Customer]"/>  
            <DTS:Column DTS:ID="21" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Product]"/>  
            <DTS:Column DTS:ID="22" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Price]"/>  
            <DTS:Column DTS:ID="23" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Timestamp]"/>  
            <DTS:Column DTS:ID="24" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[ErrorCode]"/>  
            <DTS:Column DTS:ID="25" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[ErrorColumn]"/>  
            <DTS:Column DTS:ID="31" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Customer]"/>  
            <DTS:Column DTS:ID="32" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Product]"/>  
            <DTS:Column DTS:ID="33" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Price]"/>  
            <DTS:Column DTS:ID="34" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Timestamp]"/>  
        </DTS:Pipeline>  
    </DTS:PipelineColumnMap>  
  
    ```  
  
-   スクリプト コンポーネントを使用して、エラーの説明と列の名前を、エラー出力の追加の列に挿入することもできます。 例については、「[スクリプト コンポーネントによるエラー出力の強化](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)」を参照してください。  
  
    -   追加列にエラーの説明を含めるには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> メソッドを呼び出す 1 行のスクリプトを使用します。  
  
    -   追加列に列名を含めるには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetIdentificationStringByID%2A> メソッドを呼び出す 1 行のスクリプトを使用します。  
  
     スクリプト コンポーネントは、エラーをキャプチャするデータ フロー コンポーネントよりデータ フローの下流にある任意のエラー セグメントに追加できます。 通常、このスクリプト コンポーネントは、エラー行が出力先に書き込まれる直前に配置します。 これにより、スクリプトは、書き込まれたエラー行についてのみ説明を参照します。 データ フロー内のエラー セグメントによってエラーの一部が修正されることがあり、こうした行は、エラーの出力先には書き込まれません。  
  
### エラー出力を構成するには  
  
-   [データ フロー コンポーネントでエラー出力を構成する](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)  
  
## 参照  
 [データ フロー](../../integration-services/data-flow/data-flow.md)   
 [変換を使用してデータを変換する](../../integration-services/data-flow/transformations/transform-data-with-transformations.md)   
 [パスを使用してコンポーネントを連結する](../Topic/Connect%20Components%20with%20Paths.md)   
 [[データ フロー タスク]](../../integration-services/control-flow/data-flow-task.md)   
 [データ フロー](../../integration-services/data-flow/data-flow.md)  
  
  