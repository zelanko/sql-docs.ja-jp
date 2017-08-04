---
title: "デザイン時のメソッドのデータ フロー コンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
caps.latest.revision: 58
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cf248d93b1b1e581c3315cde9b1f96edc58bcfde
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="design-time-methods-of-a-data-flow-component"></a>データ フロー コンポーネントのデザイン時のメソッド
  実行前のデータ フロー タスクは、増分的に変更が行われるため、デザイン時の状態にあると言えます。 追加される変更には、コンポーネントの追加または削除、コンポーネントを接続するパス オブジェクトの追加または削除、およびコンポーネントのメタデータに対する変更などが含まれます。 メタデータの変更が発生すると、コンポーネントはその変更を監視して対処できます。 たとえば、コンポーネントは特定の変更を禁止したり、ある変更に応じてさらに変更を加えることができます。 デザイン時に、設計者はデザイン時インターフェイス <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> を介して、コンポーネントとやり取りします。  
  
## <a name="design-time-implementation"></a>デザイン時の実装  
 コンポーネントのデザイン時のインターフェイスは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> インターフェイスによって表されます。 このインターフェイスをユーザーが明示的に実装することはありませんが、このインターフェイスで定義されるメソッドを理解しておくと、コンポーネントのデザイン時のインスタンスに対応した基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> のメソッドがわかります。  
  
 コンポーネントを [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] に読み込むと、コンポーネントのデザイン時のインスタンスがインスタンス化され、コンポーネントを編集すると、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> インターフェイスのメソッドが呼び出されます。 基本クラスを実装すると、コンポーネントで必要なこれらのメソッドのみをオーバーライドできます。 多くの場合、これらのメソッドをオーバーライドするとコンポーネントへの不適切な編集が回避できます。 たとえば、ユーザーがコンポーネントに出力を追加できないようにするには、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> メソッドをオーバーライドします。 この処理を行わない場合、基本クラスによるこのメソッドの実装を呼び出すと、コンポーネントに出力が追加されます。  
  
 コンポーネントの目的または機能に関係なく、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>、および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドをオーバーライドする必要があります。 詳細については<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>と<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>を参照してください[データ フロー コンポーネントを検証する](../../../integration-services/extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)です。  
  
## <a name="providecomponentproperties-method"></a>ProvideComponentProperties メソッド  
 コンポーネントの初期化は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドで発生します。 このメソッドは、クラス コンストラクターと同様、コンポーネントがデータ フロー タスクに追加されたときに [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーによって呼び出されます。 コンポーネントの開発者は、このメソッドが呼び出されている間に、コンポーネントの入力、出力、およびカスタム プロパティを作成して初期化する必要があります。 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドは、コンポーネントのデザイン時のインスタンスまたは実行時のインスタンスがインスタンス化されるたびに呼び出されるわけではない点が、コンストラクターとは異なります。  
  
 メソッドの基本クラスの実装により、入力および出力がコンポーネントに追加され、入力の ID が <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> プロパティに割り当てられます。 ただし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、この基本クラスによって追加された入力オブジェクトおよび出力オブジェクトには、名前が付けられていません。 入力を持つコンポーネントが含まれているパッケージまたはその名前のプロパティが設定されていない出力オブジェクトは正常に読み込まれません。 そのため、基底の実装を使用するときに割り当てる必要があります値明示的に既定の入力と出力の名前プロパティにします。  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    /// TODO: Reset the component.  
    /// TODO: Add custom properties.  
    /// TODO: Add input objects.  
    /// TODO: Add output objects.  
}  
```  
  
```vb  
Public Overrides Sub ProvideComponentProperties()  
    ' TODO: Reset the component.  
    ' TODO: Add custom properties.  
    ' TODO: Add input objects.  
    ' TODO: Add output objects.  
End Sub  
```  
  
### <a name="creating-custom-properties"></a>カスタム プロパティの作成  
 コンポーネントの開発者は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドへの呼び出しで、カスタム プロパティ (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) をコンポーネントに追加する必要があります。 カスタム プロパティにはデータ型プロパティがありません。 カスタム プロパティのデータ型は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> プロパティに割り当てた値のデータ型によって設定されます。 ただし、カスタム プロパティに初期値を割り当てた後、別のデータ型の値を割り当てることはできません。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>インターフェイスには、型のプロパティ値のサポートが制限されて**オブジェクト**です。 カスタム プロパティの値として格納できるオブジェクトは、文字列や整数などの単純型の配列のみです。  
  
 値を設定して、カスタム プロパティがプロパティ式をサポートしていることを示すその<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A>プロパティを**CPET_NOTIFY**から、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType>列挙型では、次の例で示すようにします。 ユーザーによって入力されたプロパティ式を処理または検証するためのコードを追加する必要はありません。 プロパティの既定値を設定し、値を検証し、値を読み取って正常に使用することができます。  
  
```csharp  
IDTSCustomProperty100 myCustomProperty;  
...  
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;  
```  
  
```vb  
Dim myCustomProperty As IDTSCustomProperty100  
...  
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY  
```  
  
 使用して、列挙型からカスタム プロパティ値を選択するユーザーを制限することができます、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A>プロパティ、という名前のパブリック列挙値が定義されていることを前提としています、次の例で示すように**MyValidValues**です。  
  
```csharp  
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();  
customProperty.Name = "My Custom Property";  
// This line associates the type with the custom property.  
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;  
// Now you can use the enumeration values directly.  
customProperty.Value = MyValidValues.ValueOne;    
```  
  
```vb  
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New   
customProperty.Name = "My Custom Property"   
' This line associates the type with the custom property.  
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName   
' Now you can use the enumeration values directly.  
customProperty.Value = MyValidValues.ValueOne  
```  
  
 詳細についてを参照してください「一般的な型変換」と「型コンバーターの実装」、 [MSDN ライブラリ](http://go.microsoft.com/fwlink/?LinkId=7022)です。  
  
 次の例に示すように、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> プロパティを使用すると、カスタム プロパティの値を設定するカスタム エディター ダイアログ ボックスを指定できます。 最初に、必要がありますエディターを作成するカスタム型から継承する**System.Drawing.Design.UITypeEditor**ニーズに合った既存の UI 型エディター クラスを見つけられない場合、します。  
  
```csharp  
public class MyCustomTypeEditor : UITypeEditor  
{  
...  
}  
```  
  
```vb  
Public Class MyCustomTypeEditor  
  Inherits UITypeEditor   
  ...  
End Class  
```  
  
 次に、カスタム プロパティの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> プロパティの値として、このクラスを指定します。  
  
```csharp  
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();  
customProperty.Name = "My Custom Property";  
// This line associates the editor with the custom property.  
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;  
```  
  
```vb  
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New   
customProperty.Name = "My Custom Property"   
' This line associates the editor with the custom property.  
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName  
```  
  
 詳細については、「UI 型エディターの実装」を参照してください、 [MSDN ライブラリ](http://go.microsoft.com/fwlink/?LinkId=7022)です。  
  
## <a name="see-also"></a>参照  
 [データ フロー コンポーネントの実行時のメソッド](../../../integration-services/extending-packages-custom-objects/data-flow/run-time-methods-of-a-data-flow-component.md)  
  
  
