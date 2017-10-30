---
title: "データ フロー コンポーネントのバージョンのアップグレード |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 65e38600b0974d75f5509a4231f6ebb0a15ba19a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="upgrading-the-version-of-a-data-flow-component"></a>データ フロー コンポーネントのバージョンのアップグレード
  古いバージョンのコンポーネントで作成されたパッケージには、新しいバージョンのコンポーネントでは使い方が変更されているカスタム プロパティなど、既に有効でないメタデータが含まれている可能性があります。 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 基本クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドをオーバーライドすると、以前に古いパッケージに保存したメタデータを、コンポーネントの現在のプロパティを反映して更新することができます。  
  
> [!NOTE]  
>  新しいバージョンの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 用にカスタム コンポーネントを再コンパイルする場合、コンポーネントのプロパティが変更されていなければ、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> プロパティの値を変更する必要はありません。  
  
## <a name="example"></a>例  
 次のサンプルには、架空のデータ フロー コンポーネントのバージョン 2.0 のコードが含まれています。 新しいバージョン番号は、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティで定義されています。 このコンポーネントには、しきい値を超えた数値の処理方法を定義するプロパティがあります。 この架空のコンポーネントのバージョン 1.0 では、このプロパティの名前は `RaiseErrorOnInvalidValue` で、指定できる値は true または false のブール値でした。 バージョン 2.0 ではプロパティ名が `InvalidValueHandling` に変更されて、カスタム列挙の 4 つの値のいずれかを指定できるようになっています。  
  
 次のサンプルのオーバーライドされた <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> メソッドは、以下のアクションを実行します。  
  
-   コンポーネントの現在のバージョンを取得します。  
  
-   古いカスタム プロパティの値を取得します。  
  
-   カスタム プロパティ コレクションから古いプロパティを削除します。  
  
-   古いプロパティの値に基づいて新しいカスタム プロパティの値を設定します (可能な場合)。  
  
-   バージョンのメタデータをコンポーネントの現在のバージョンに設定します。  
  
> [!NOTE]  
>  データ フロー エンジンに渡しますに独自のバージョン番号、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A>メソッドで、 *pipelineVersion*パラメーター。 このパラメーターは、バージョン 1.0 の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では有用ではありませんが、今後のバージョンで役に立つようになります。  
  
 このサンプル コードでは、カスタム プロパティの以前のブール値に直接マップされる 2 つの列挙値のみが使用されています。 使用できるその他の列挙値を選択するには、コンポーネントのカスタム ユーザー インターフェイスを使用するか、詳細エディターを使用するか、プログラミングを行います。 高度なエディターでカスタム プロパティの列挙値を表示する方法については、「カスタム プロパティの作成」を参照してください[データ フロー コンポーネントのデザイン時メソッド](../../../integration-services/extending-packages-custom-objects/data-flow/design-time-methods-of-a-data-flow-component.md)です。  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```

