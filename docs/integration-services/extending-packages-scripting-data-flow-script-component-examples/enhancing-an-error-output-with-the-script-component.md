---
title: "スクリプト コンポーネントによるエラー出力の強化 |Microsoft ドキュメント"
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
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 3881b57f4089dbb075d019f9bd1a88a96a307b72
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="enhancing-an-error-output-with-the-script-component"></a>スクリプト コンポーネントによるエラー出力の強化
  既定では、次の 2 つの余分な列、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ErrorCode および ErrorColumn、エラー出力はエラー番号と、エラーが発生した列の ID を表す数値コードのみを含めます。 これらの数値は、対応するエラーの説明と列の名前がない使用制限の可能性があります。  
  
 このトピックでは、スクリプト コンポーネントを使用して、データ フロー内の既存のエラー出力データに、エラーの説明と列名を追加する方法について説明します。 この例では、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> メソッドを使用して、事前定義された特定の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードに対応するエラーの説明を追加します。これは、スクリプト コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> プロパティから使用できます。 この例を使用してキャプチャした系列 ID に対応する列名を追加してから、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData130.GetIdentificationStringByID%2A>同じインターフェイスのメソッドです。  
  
> [!NOTE]  
>  複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、このスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。 詳細については、「 [カスタム データ フロー コンポーネントの開発](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。  
  
## <a name="example"></a>例  
 次に示す例では、変換として構成されたスクリプト コンポーネントを使用して、データ フロー内の既存のエラー出力データにエラーの説明と列名を追加します。  
  
 データ フローの変換として使用するため、スクリプト コンポーネントを構成する方法の詳細については、次を参照してください。[スクリプト コンポーネントによる同期変換を作成する](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)と[スクリプト コンポーネントによる非同期変換の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)です。  
  
#### <a name="to-configure-this-script-component-example"></a>このスクリプト コンポーネントの例を構成するには  
  
1.  新しいスクリプト コンポーネントを作成する前に、データ フローの上流コンポーネントを構成して、エラーや切り捨てが発生した場合に行をエラー出力にリダイレクトするようにします。 テスト目的の場合、たとえば、参照が失敗するような 2 つのテーブル間の参照変換を構成するなどして、エラーが発生するような形でコンポーネントを構成します。  
  
2.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。  
  
3.  上流コンポーネントからのエラー出力を新しいスクリプト コンポーネントに接続します。  
  
4.  開く、**スクリプト変換エディター**、および、**スクリプト** ページの**scriptlanguage**プロパティ、スクリプト言語を選択します。  
  
5.  をクリックして**スクリプトの編集**を開くには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を以下に示すサンプル コードを追加します。  
  
6.  VSTA を閉じます。  
  
7.  スクリプト変換エディターで、**入力列** ページで、ErrorCode および ErrorColumn の列を選択します。  
  
8.  **入力と出力** ページで、次の 2 つの新しい列を追加します。  
  
    -   型の新しい出力列の追加**文字列**という**ErrorDescription**です。 長いメッセージをサポートするために、新しい列の既定の長さを 255 に拡張します。  
  
    -   型の別の新しい出力列の追加**文字列**という**ColumnName**です。 長い値をサポートするために 255 を新しい列の既定の長さを増やします。  
  
9. 閉じる、**スクリプト変換エディターです。**  
  
10. 適切な送信先をスクリプト コンポーネントの出力をアタッチします。 アドホック テスト用に最も構成しやすいのは、フラット ファイル変換先です。  
  
11. パッケージを実行します。  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription = _  
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
      Dim componentMetaData130 = TryCast(Me.ComponentMetaData, IDTSComponentMetaData130)  
      If componentMetaData130 IsNot Nothing Then  
        Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn)  
         End If  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
      Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
      var componentMetaData130 = this.ComponentMetaData as IDTSComponentMetaData130;  
      if (componentMetaData130 != null)  
        {  
            Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn);  
        }  
  
    }  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)   
 [データ フロー コンポーネントでエラー出力の使用](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [スクリプト コンポーネントによる同期変換の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
  
  
