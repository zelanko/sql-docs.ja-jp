---
title: "スクリプト コンポーネント エディターでスクリプト コンポーネントの構成 |Microsoft ドキュメント"
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
- SSIS Script component
- Script Component Editor
- SSIS Script component, configuring
- Script component [Integration Services], configuring
ms.assetid: 586dd799-f383-4d6d-b1a1-f09233d14f0a
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8488fcc7d402430f66b9b9018b31956a5a1d8383
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-component-in-the-script-component-editor"></a>スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成
  スクリプト コンポーネントでカスタム コードを記述する前に、作成するデータ フロー コンポーネントの種類を選択する必要があります: 変換元、変換、または変換先-し、コンポーネントのメタデータおよびプロパティを構成、**スクリプト変換エディター**です。  
  
## <a name="selecting-the-type-of-component-to-create"></a>作成するコンポーネントの種類の選択  
 [データ フロー] ペインにスクリプト コンポーネントを追加すると[!INCLUDE[ssIS](../../../includes/ssis-md.md)]デザイナー、**スクリプト コンポーネントの種類の選択** ダイアログ ボックスが表示されます。 コンポーネントをあらかじめ、変換元、変換、または変換先として構成しておきます。 この初期選択を行うと後、は、内のコンポーネントの構成を続行することができます、**スクリプト変換エディター**です。  
  
 スクリプト コンポーネントの既定のスクリプト言語を設定するには、使用、**スクリプト言語** オプションを選択、**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、「 [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)」を参照してください。  
  
## <a name="understanding-the-two-design-time-modes"></a>デザイン時の 2 つのモードについて  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでは、スクリプト コンポーネントにメタデータ デザイン モードとコード デザイン モードの 2 つのモードがあります。  
  
 開くと、**スクリプト変換エディター**、コンポーネント メタデータ デザイン モードに入るとします。 このモードでは、入力列の選択、および出力と出力列の追加または構成を行うことができますが、コードは記述できません。 このコンポーネントのメタデータを構成した後で、コード デザイン モードに切り替えてスクリプトを記述できます。  
  
 切り替えるとコード デザイン モード をクリックして**スクリプトの編集**、スクリプト コンポーネントは、追加の変更を防ぐためにメタデータがロックされ、入力と出力のメタデータから基本コードを自動的に生成します。 コードの自動生成が完了すると、カスタム コードを入力できるようになります。 作成したコードは自動生成された基本クラスを使用し、すべて厳密に型指定されたオブジェクトとして、入力行の処理、バッファーおよびバッファー内の列へのアクセス、およびパッケージからの接続マネージャーと変数の取得を行います。  
  
 コード デザイン モードでカスタム コードを入力したら、モードを切り替えてメタデータ デザイン モードに戻すことができます。 これによって入力したコードが削除されることはありませんが、次にメタデータを変更すると、基本クラスが再生成されます。 その後、カスタム コードが参照するオブジェクトが存在しないか、または変更されたために、コンポーネントの検証に失敗する可能性があります。 その場合、再生成された基本クラスに対してコードが正常にコンパイルされるように、コードを手動で修正する必要があります。  
  
## <a name="configuring-the-component-in-metadata-design-mode"></a>メタデータ デザイン モードでのコンポーネントの構成  
 メタデータ デザイン モードでは、入力列の選択、および出力と出力列の追加や構成を行うことができますが、コードは記述できません。 コンポーネントのメタデータを構成した後で、コード デザイン モードに切り替えてスクリプトを記述します。  
  
 カスタム エディターで構成する必要のあるプロパティは、スクリプト コンポーネントの使用法に応じて異なります。 スクリプト コンポーネントは、変換元、変換、または変換先として構成できます。 コンポーネントの使用方法に応じて、入力または出力のどちらか、またはその両方がサポートされます。 記述するカスタム コードでは、入力および出力の行と列が処理されます。  
  
### <a name="inputs-columns-page-of-the-script-transformation-editor"></a>[スクリプト変換エディター] の [入力列] ページ  
 **入力列**のページ、**スクリプト変換エディター**変換および変換先、のではなくソースが表示されます。 このページでは、使用できる入力列から、使用するカスタム スクリプトを選択し、その入力列に読み取り専用でアクセスするか、または読み取り/書き込みでアクセスするかを指定します。  
  
 このメタデータに基づいて生成されるコード プロジェクトでは、BufferWrapper プロジェクト アイテムに、各入力のクラスが含まれます。このクラスには、選択した各入力列用の型指定されたアクセサー プロパティが含まれています。 たとえば、整数値を選択する場合**CustomerID**列と文字列**CustomerName**という名前の入力からの列**CustomerInput**、BufferWrapper プロジェクト アイテムが含まれます、 **CustomerInput**から派生したクラス<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>、および**CustomerInput**クラスが名前付き整数のプロパティを公開**CustomerID**およびという名前の文字列プロパティ**CustomerName**です。 この規則により、次のような型チェック付きのコードが記述できます。  
  
```vb  
Dim currentCustomerID as Integer = CustomerInput.CustomerID  
Dim currentCustomerName as String = CustomerInput.CustomerName  
```  
  
 特定の種類のデータ フロー コンポーネントの入力列を構成する方法の詳細については、下にある、該当する例を参照してください。[スクリプト コンポーネントの種類を特定の開発](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)です。  
  
### <a name="inputs-and-outputs-page-of-the-script-transformation-editor"></a>[スクリプト変換エディター] の [入力および出力] ページ  
 **入力呼び出し力**のページ、**スクリプト変換エディター**元、変換、および変換先が表示されます。 このページでは、カスタム スクリプトで使用する入力、出力、および出力列を追加、削除、および構成します。ただし、次のような制限があります。  
  
-   スクリプト コンポーネントを変換元として使用する場合、入力はありませんが複数の出力がサポートされます。  
  
-   スクリプト コンポーネントを変換として使用する場合、1 つの入力と複数の出力がサポートされます。  
  
-   スクリプト コンポーネントを変換先として使用する場合、1 つの入力がサポートされますが出力はありません。  
  
 このメタデータに基づいて生成されるコード プロジェクトでは、BufferWrapper プロジェクト アイテムに、各入力および出力のクラスが含まれます。 という名前の出力を作成する場合など**CustomerOutput**、BufferWrapper プロジェクト アイテムが含まれます、 **CustomerOutput**から派生したクラス<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>、および**CustomerOutput**クラスが作成された各出力列の型指定されたアクセサー プロパティを格納します。  
  
 のみで出力列を構成することができます、**入力呼び出し力**ページ。 変換および変換先の入力列を選択できます、**入力列**ページ。 BufferWrapper プロジェクト アイテムで作成された、型指定されたアクセサー プロパティは、出力列の書き込み専用プロパティです。 入力列のアクセサー プロパティは読み取り専用または読み取り/書き込みの各列に対して選択した使用法の種類に応じて、**入力列**ページ。  
  
 特定のデータ型の入力と出力を構成する方法については、フロー コンポーネントで、該当する例を参照してください。[スクリプト コンポーネントの種類を特定の開発](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)です。  
  
> [!NOTE]  
>  エラー行の自動処理のスクリプト コンポーネントでエラー出力として出力を直接構成することはできませんが、別の出力を作成するか、可能な場合はスクリプトを使用してこの出力に行を送信することによって、エラー出力の機能を再現することができます。 詳細については、次を参照してください。[スクリプト コンポーネントのエラー出力のシミュレート](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)です。  
  
#### <a name="exclusiongroup-and-synchronousinputid-properties-of-outputs"></a>出力の ExclusionGroup プロパティおよび SynchronousInputID プロパティ  
 **ExclusionGroup**プロパティでは、0 以外の値をコードがフィルターまたは分岐を実行し、同じ 0 以外を共有する出力のいずれかに各行を導く、同期出力型の変換でのみ**ExclusionGroup**値。 たとえば変換は、行を既定の出力またはエラー出力のどちらかに送信できます。 このシナリオに追加の出力を作成するときに確認の値を設定する、 **SynchronousInputID**プロパティと一致する整数を**ID**コンポーネントの入力のです。  
  
 **SynchronousInputID**プロパティでは、0 以外の値を同期出力型の変換でのみです。 このプロパティの値が 0 の場合、出力が非同期型であることを示します。 このプロパティには、ここで行に渡されるを介して選択されている出力または出力、新しい行を追加することがなく、同期出力の**ID**コンポーネントの入力のです。  
  
> [!NOTE]  
>  ときに、**スクリプト変換エディター**最初の出力では、エディターのセットを作成、 **SynchronousInputID**する出力のプロパティ、 **ID**コンポーネントの入力のです。 ただし、エディターは、後の出力を作成するときに、エディター設定、 **SynchronousInputID**をゼロにそれらの出力のプロパティです。  
>   
>  同期出力型コンポーネントを作成する場合、各出力があります、 **SynchronousInputID**プロパティに設定、 **ID**コンポーネントの入力のです。 したがって、それぞれの出力、エディターが最初の出力があります後が作成されるその**SynchronousInputID**値が 0 から変更された、 **ID**コンポーネントの入力のです。  
>   
>  各出力する必要がありますが、非同期出力型コンポーネントを作成する場合、 **SynchronousInputID**プロパティを 0 に設定します。 したがって、最初の出力が必要、 **SynchronousInputID**から値が変更された、 **ID**をゼロにコンポーネントの入力のです。  
  
 スクリプト コンポーネント内の 2 つの同期出力型のいずれかに行を指示することの例は、次を参照してください。[スクリプト コンポーネントによる同期変換を作成する](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)です。  
  
### <a name="object-names-in-generated-script"></a>生成されたスクリプトのオブジェクト名  
 スクリプト コンポーネントは、入力と出力の名前を解析し、入力と出力内の列の名前を解析します。次に、これらの名前に基づいて、BufferWrapper プロジェクト アイテムにクラスとプロパティを生成します。 見つかった名前が、Unicode カテゴリに属していない文字を含めるかどうか**UppercaseLetter**、 **LowercaseLetter**、 **TitlecaseLetter**、 **ModifierLetter**、**数字**、または**DecimalDigitLetter**、生成された名前では無効な文字が削除されます。 たとえば、スペースは削除される、そのため 2 つの入力列の名前を持つ**FirstName**と [**名**] 列の名前を持つものとして解釈されます両方**FirstName**、予期しない結果にします。 このような状況を防ぐには、スクリプト コンポーネントで使用される入力と出力の名前、および入力と出力の列の名前には、このセクションで一覧表示されている Unicode カテゴリに属する文字のみが含まれるようにする必要があります。  
  
### <a name="script-page-of-the-script-transformation-editor"></a>[スクリプト変換エディター] の [スクリプト] ページ  
 **スクリプト**のページ、**スクリプト タスク エディター**、一意の名前と、スクリプト タスクの説明を割り当てます。 また、次のプロパティの値を割り当てることができます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] およびそれ以降のバージョンでは、すべてのスクリプトがプリコンパイル済みです。 以前のバージョンで指定したスクリプトを設定してプリコンパイルするかどうか、**プリコンパイル**タスクのプロパティです。  
  
#### <a name="validateexternalmetadata-property"></a>ValidateExternalMetadata プロパティ  
 ブール値、 **ValidateExternalMetadata**プロパティは、このコンポーネントが、デザイン時に外部データ ソースに対する検証を実行するかどうか、または実行時まで検証を延期するかどうかを指定します。 既定では、このプロパティの値は**True**; デザイン時および実行時の両方に、外部メタデータの検証は、します。 するには、このプロパティの値を設定することがあります**False**ときに、外部データ ソースが利用できないデザイン時: たとえば、ときに、パッケージ ソースをダウンロードまたは実行時にのみ、変換先を作成します。  
  
#### <a name="readonlyvariables-and-readwritevariables-properties"></a>ReadOnlyVariables プロパティおよび ReadWriteVariables プロパティ  
 既存の変数をコンマ区切りリストとして、これらのプロパティの値に入力すると、スクリプト コンポーネントのコード内で、その変数に読み取り専用アクセスまたは読み取り/書き込みアクセスできるようになります。 変数には、自動生成された基本クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> および <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> プロパティを介して、コード内でアクセスします。 詳細については、次を参照してください。[スクリプト コンポーネントで変数を使用して](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)です。  
  
> [!NOTE]  
>  変数名の大文字と小文字は区別されます。  
  
#### <a name="scriptlanguage"></a>[ScriptLanguage]  
 スクリプト コンポーネントのプログラミング言語として、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# を選択できます。  
  
#### <a name="edit-script-button"></a>[スクリプトの編集] ボタン  
 **スクリプトの編集**ボタンが開き、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE は、カスタム スクリプトを記述します。 詳細については、次を参照してください。[コーディングおよびスクリプト コンポーネントのデバッグ](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)です。  
  
### <a name="connection-managers-page-of-the-script-transformation-editor"></a>[スクリプト変換エディター] の [接続マネージャー] ページ  
 **接続マネージャー**のページ、**スクリプト変換エディター**、追加して、カスタム スクリプトで使用する接続マネージャーを削除します。 通常、変換元または変換先コンポーネントを作成する場合は、接続マネージャーを参照する必要があります。  
  
 コードで生成されるプロジェクトはこのメタデータに基づいて、 **ComponentWrapper**プロジェクト項目が含まれています、**接続**をそれぞれ選択されている接続マネージャーの型指定されたアクセサー プロパティを持つコレクション クラスです。 型指定された各アクセサー プロパティの名前は、接続マネージャー自体の名前と同じであり、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100> のインスタンスとして、接続マネージャーへの参照を返します。 たとえば、という名前の接続マネージャーを追加した場合`MyADONETConnection`上、**接続マネージャー**ページ エディターのことができます参照を取得する接続マネージャーに、スクリプトで次のコードを使用しています。  
  
```vb  
Dim myADONETConnectionManager As IDTSConnectionManager100 = _  
    Me.Connections.MyADONETConnection  
```  
  
 詳細については、次を参照してください。[スクリプト コンポーネントでデータ ソースに接続する](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)です。  
  
## <a name="see-also"></a>参照  
 [コーディングおよびスクリプト コンポーネントのデバッグ](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  

