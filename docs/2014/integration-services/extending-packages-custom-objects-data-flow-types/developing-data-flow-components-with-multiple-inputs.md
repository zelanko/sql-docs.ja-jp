---
title: 複数の入力を持つデータ フロー コンポーネントの開発 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86a3fc9a1ad5978e7bc27f233c3d5c92d23afcef
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427949"
---
# <a name="developing-data-flow-components-with-multiple-inputs"></a>複数の入力を持つデータ フロー コンポーネントの開発
  複数の入力によってデータが不均一なレートで生成される場合に、複数の入力があるデータ フローコンポーネントによって過度にメモリが消費されることがあります。 複数の入力をサポートするカスタム データ フロー コンポーネントを開発するときは、Microsoft.SqlServer.Dts.Pipeline 名前空間の次のメンバーを使用してこのメモリの負荷を管理できます。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティ。 カスタム データ フロー コンポーネントに必要なコードを実装して不均一なレートのデータ フローを管理する場合は、このプロパティの値を `true` に設定します。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッド。 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> プロパティを `true` に設定する場合は、このメソッドを実装する必要があります。 実装しない場合、データ フロー エンジンは実行時に例外を発生させます。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッド。 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> プロパティを `true` に設定し、カスタム コンポーネントが複数の入力をサポートしている場合は、このメソッドも実装する必要があります。 実装しない場合、ユーザーが複数の入力をアタッチすると、データ フロー エンジンは実行時に例外を発生させます。  
  
 また、これらのメンバーを使用すると、マージ変換およびマージ結合変換用にマイクロソフトが開発したような、メモリ負荷のためのソリューションを開発できます。  
  
## <a name="setting-the-supportsbackpressure-property"></a>SupportsBackPressure プロパティの設定  
 複数の入力をサポートするカスタム データ フロー コンポーネントでより効率的なメモリ管理を実装するための最初の手順は、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> で <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> プロパティの値を `true` に設定することです。 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> の値が `true` の場合、データ フロー エンジンは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドを呼び出し、複数の入力があるときは、実行時に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドも呼び出します。  
  
### <a name="example"></a>例  
 次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> を実装して、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> の値を `true` に設定します。  
  
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
 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティの値を `true` に設定する場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドも実装する必要があります。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドの実装では、基本クラスで実装を呼び出す必要はありません。 基本クラスでのこのメソッドの既定の実装では、`NotImplementedException` を発生させるだけです。  
  
 このメソッドを実装し、コンポーネントの各入力に対して Boolean 型の *canProcess* 配列で要素の状態を設定します (入力は、 *inputIDs*配列内の ID 値によって識別されます)。*Canprocess*配列の要素の値を入力用にに設定すると、 `true` データフローエンジンは、コンポーネントのメソッドを呼び出し、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 指定された入力に対してより多くのデータを提供します。  
  
 より多くのアップストリームデータを使用できますが、少なくとも1つの入力の*Canprocess*配列要素の値は、常にであるか、処理が停止する必要があり `true` ます。  
  
 データ フロー エンジンは、データの各バッファーを送信する前に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドを呼び出して、追加データの受信を待機している入力を判断します。 入力がブロックされていることが戻り値によって示された場合、データ フロー エンジンは、バッファーをコンポーネントに送信する代わりに、入力データの追加バッファーを一時的にキャッシュします。  
  
> [!NOTE]  
>  独自に記述するコード内で、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは呼び出しません。 データ フロー エンジンはコンポーネントを実行するとき、これらのメソッドやオーバーライドする `PipelineComponent` クラスのその他のメソッドを呼び出します。  
  
### <a name="example"></a>例  
 次の例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> の実装により、以下の条件に該当する場合に入力が追加のデータを待っていることを示します。  
  
-   入力に対する追加の上流データがある (`!inputEOR`)。  
  
-   コンポーネントが、受信済みのバッファーで入力に対して処理できるデータを現在持っていない (`inputBuffers[inputIndex].CurrentRow() == null`)。  
  
 入力がさらに多くのデータの受信を待機している場合、データフローコンポーネントは、 `true` その入力に対応する*canprocess*配列の要素の値をに設定することによってこれを示します。  
  
 逆に、コンポーネントが入力に対して処理できるデータを持っている場合、この例では入力の処理を中断します。 この例では、この `false` 入力に対応する*canprocess*配列の要素の値をに設定します。  
  
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
  
 前の例は、Boolean 型の `inputEOR` 配列を使用して、各入力で追加のアップストリーム データを使用できるかどうかを示します。 配列名の `EOR` は "行セットの末尾 (end of rowset)" を示し、データ フロー バッファーの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティを参照します。 ここに含まれていない例の部分では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドを使用して、受信するデータの各バッファーに対して <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティの値を確認します。 値 `true` によって、入力でこれ以上のアップストリーム データを利用できないことが示された場合、その入力の `inputEOR` 配列要素の値を `true` に設定します。 このメソッドの例では、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 配列要素の値によって、 *canProcess* `false` `inputEOR` 入力に使用できるアップストリームデータがないことが示された場合に、canprocess 配列内の対応する要素の値をに設定します。  
  
## <a name="implementing-the-getdependentinputs-method"></a>GetDependentInputs メソッドの実装  
 カスタム データ フロー コンポーネントが複数の入力をサポートしている場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドも実装する必要があります。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドの実装では、基本クラスで実装を呼び出す必要はありません。 基本クラスでのこのメソッドの既定の実装では、`NotImplementedException` を発生させるだけです。  
  
 データ フロー エンジンは、ユーザーが 3 つ以上の入力をコンポーネントにアタッチする場合に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドを呼び出すだけです。 コンポーネントに入力が2つしかないときに、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドが1つの入力がブロックされていることを示している場合 (*canprocess*  =  `false` )、データフローエンジンは、他の入力がさらに多くのデータの受信を待機していることを認識します。 ただし、入力が 2 つより多い場合に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> メソッドによって 1 つの入力がブロックされていることが示されたときは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> の追加のコードはどの入力が追加データの受信を待機しているかを示します。  
  
> [!NOTE]  
>  独自に記述するコード内で、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> メソッドは呼び出しません。 データ フロー エンジンはコンポーネントを実行するとき、これらのメソッドやオーバーライドする `PipelineComponent` クラスのその他のメソッドを呼び出します。  
  
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
  
  
