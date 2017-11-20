---
title: "複数の入力データ フロー コンポーネントの開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects-data-flow-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2cafe3a18fbe930088347304ed758afe505771d6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="developing-data-flow-components-with-multiple-inputs"></a>複数の入力を持つデータ フロー コンポーネントの開発
  複数の入力によってデータが不均一なレートで生成される場合に、複数の入力があるデータ フローコンポーネントによって過度にメモリが消費されることがあります。 2 つ以上の入力をサポートするカスタム データ フロー コンポーネントを開発する場合は、Microsoft.SqlServer.Dts.Pipeline 名前空間には次のメンバーを使用してこのメモリの負荷を管理できます。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティ。 このプロパティの値を設定**true**データが不均一なレートでフローを管理するカスタム データ フロー コンポーネントに必要なコードを実装するかどうか。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッド。 設定した場合は、このメソッドの実装を提供する必要があります、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>プロパティを**true**です。 実装しない場合、データ フロー エンジンは実行時に例外を発生させます。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッド。 設定した場合にも、このメソッドの実装を提供する必要があります、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>プロパティを**true**カスタム コンポーネントは、複数の 2 つの入力をサポートしているとします。 実装しない場合、ユーザーが複数の入力をアタッチすると、データ フロー エンジンは実行時に例外を発生させます。  
  
 また、これらのメンバーを使用すると、マージ変換およびマージ結合変換用にマイクロソフトが開発したような、メモリ負荷のためのソリューションを開発できます。  
  
## <a name="setting-the-supportsbackpressure-property"></a>SupportsBackPressure プロパティの設定  
 複数の入力をサポートするカスタム データ フロー コンポーネントがの値を設定するには、メモリ管理の強化を実装する際に、まず、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>プロパティを**true**で、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>です。 ときの値<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>は**true**、データ フロー エンジンの呼び出し、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A>メソッドと、複数の 2 つの入力がある場合にも呼び出します、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A>メソッド実行時にします。  
  
### <a name="example"></a>例  
 次の例では、実装では、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>の値を設定<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>に**true**です。  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a>IsInputReady メソッドの実装  
 値を設定すると、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>プロパティを**true**で、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>オブジェクトの実装を提供する必要がありますも、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A>のメソッド、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>クラスです。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドの実装では、基本クラスで実装を呼び出す必要はありません。 ベースでは、このメソッドの既定の実装クラスが生成するだけ、 **NotImplementedException**です。  
  
 要素の状態を設定するブール値でこのメソッドを実装するときに*canProcess*の各コンポーネントの入力の配列。 (入力が内の ID 値で識別される、 *inputIDs*配列です)。内の要素の値を設定すると、 *canProcess*配列を**true** 、入力データ フロー エンジンは、コンポーネントを呼び出して<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>メソッド、指定された入力に対して複数のデータを提供します。  
  
 追加の上流データが使用中の値、 *canProcess*配列要素には、少なくとも 1 つの入力を必ず**true**、処理が停止します。  
  
 データ フロー エンジンは、データの各バッファーを送信する前に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドを呼び出して、追加データの受信を待機している入力を判断します。 入力がブロックされていることが戻り値によって示された場合、データ フロー エンジンは、バッファーをコンポーネントに送信する代わりに、入力データの追加バッファーを一時的にキャッシュします。  
  
> [!NOTE]  
>  独自に記述するコード内で、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは呼び出しません。 データ フロー エンジンは、これらのメソッドやの他のメソッドを呼び出す、 **PipelineComponent**データ フロー エンジンは、コンポーネントを実行するときに、オーバーライドするクラス。  
  
### <a name="example"></a>例  
 次の例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> の実装により、以下の条件に該当する場合に入力が追加のデータを待っていることを示します。  
  
-   入力に対する追加の上流データがある (`!inputEOR`)。  
  
-   コンポーネントが、受信済みのバッファーで入力に対して処理できるデータを現在持っていない (`inputBuffers[inputIndex].CurrentRow() == null`)。  
  
 入力がより多くのデータの受信を待機している場合、データ フロー コンポーネントを示しますこのに設定した**true**内の要素の値、 *canProcess*その入力に対応する配列。  
  
 逆に、コンポーネントが入力に対して処理できるデータを持っている場合、この例では入力の処理を中断します。 例に設定することで**false**内の要素の値、 *canProcess*その入力に対応する配列。  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 前の例は、Boolean 型の `inputEOR` 配列を使用して、各入力で追加のアップストリーム データを使用できるかどうかを示します。 配列名の `EOR` は "行セットの末尾 (end of rowset)" を示し、データ フロー バッファーの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティを参照します。 ここに含まれていない例の部分では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドを使用して、受信するデータの各バッファーに対して <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティの値を確認します。 値**true**入力に使用できる以上の上流データが、この例の値を設定することを示します、`inputEOR`配列要素には、その入力を**true**です。 この例の<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A>メソッド内の対応する要素の値を設定、 *canProcess*配列を**false** 、入力時の値、`inputEOR`配列要素には、ことを示しますこれ以上のアップ ストリーム データは、入力使用できます。  
  
## <a name="implementing-the-getdependentinputs-method"></a>GetDependentInputs メソッドの実装  
 カスタム データ フロー コンポーネントが複数の入力をサポートしている場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドも実装する必要があります。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドの実装では、基本クラスで実装を呼び出す必要はありません。 ベースでは、このメソッドの既定の実装クラスが生成するだけ、 **NotImplementedException**です。  
  
 データ フロー エンジンは、ユーザーが 3 つ以上の入力をコンポーネントにアタッチする場合に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドを呼び出すだけです。 コンポーネントの 2 つの入力であるときに、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A>メソッドでは、1 つの入力がブロックされていることを示します (*canProcess* = **false**)、データ フロー エンジンは、もう一方の入力が認識しています多くのデータの受信を待機しています。 ただし、入力が 2 つより多い場合に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドによって 1 つの入力がブロックされていることが示されたときは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> の追加のコードはどの入力が追加データの受信を待機しているかを示します。  
  
> [!NOTE]  
>  独自に記述するコード内で、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは呼び出しません。 データ フロー エンジンは、これらのメソッドやの他のメソッドを呼び出す、 **PipelineComponent**データ フロー エンジンは、コンポーネントを実行するときに、オーバーライドするクラス。  
  
### <a name="example"></a>例  
 ある 1 つの入力がブロックされている場合、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドの次の実装は、追加データの受信を待機している入力のコレクションを返し、はじめの 1 つの入力はブロッキング状態のままになります。 コンポーネントは、既に受信したバッファー内に、ブロックされている入力以外の入力が処理できるデータが現在ないことをチェックして、ブロックしている入力を特定します (`inputBuffers[i].CurrentRow() == null`)。 次に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは、ブロックしている入力のコレクションを入力 ID のコレクションとして返します。  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  

