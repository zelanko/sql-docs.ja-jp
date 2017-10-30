---
title: "外部メタデータの実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96d413bca20ec171d515ac6d0ad81b5b994bd854
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-external-metadata"></a>外部メタデータの実装
  コンポーネントがそのデータ ソースから切断されると、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> インターフェイスを使用することによって、入力および出力列のコレクション内の列を、その外部データ ソースの列に対して検証できます。 このインターフェイスを使用すると、外部データ ソースの列のスナップショットを保持し、これらの列をコンポーネントの入力および出力列コレクションの列にマップできます。  
  
 外部メタデータ列を実装することで、追加した列のコレクションに対する管理と検証の必要が生じるため、コンポーネントの開発にオーバーヘッドと複雑性が加わりますが、検証のためのサーバーへのラウンド トリップに余計な費用をかけなくても済むので、開発作業は行う価値のあるものになるでしょう。  
  
## <a name="populating-external-metadata-columns"></a>外部メタデータ列の設定  
 外部メタデータ列は、通常、対応する入力または出力列を作成するときにコレクションに追加されます。 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> メソッドを呼び出して、新しい列を作成します。 次に、外部データ ソースに一致するように列のプロパティを設定します。  
  
 外部メタデータ列を対応する入力または出力列にマップするには、外部メタデータ列の ID を入力または出力列の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> プロパティに割り当てます。 これにより、コレクションの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> メソッドを使用して、特定の入力列または出力列に対する外部メタデータ列を簡単に探すことができます。  
  
 次の例では、外部メタデータ列を作成し、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> プロパティを設定することによって出力列にマップする方法を示します。  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a>外部メタデータ列での検証  
 検証を行うには、外部メタデータ列のコレクションを保持するための手順をコンポーネントに追加する必要があります。追加された列のコレクションに対して検証を行う必要があるためです。 検証は、接続された状態での検証と切断された状態での検証に分けられます。  
  
### <a name="connected-validation"></a>接続された状態での検証  
 コンポーネントが外部データ ソースに接続されると、入力または出力コレクション内の列は、外部データ ソースに対して直接検証されます。 また、外部メタデータのコレクション内の列を検証する必要があります。 これを使用して、外部メタデータ コレクションを変更できるために必要な**詳細エディター**で[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]、し、コレクションに加えられた変更は検出されません。 したがって、接続された状態のコンポーネントでは、外部メタデータ列のコレクション内の列が外部データ ソースの列を継続して反映していることを確認する必要があります。  
  
 内の外部メタデータ コレクションを非表示にすることもできます、**詳細エディター**を設定して、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A>にコレクションのプロパティ**false**です。 ただしこれも非表示に、**列マッピングの**ユーザー列、入力または出力コレクションを外部メタデータ列コレクション内の列にマップできるように、エディターのタブです。 このプロパティを設定**false**は防止しません開発者プログラムによって、コレクションの変更が、排他的に使用されるコンポーネントの外部メタデータ列のコレクションに対する保護のレベルが提供[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]です。  
  
### <a name="disconnected-validation"></a>切断された状態での検証  
 コンポーネントが外部データ ソースから切断されている場合、検証は簡略化されます。これは、外部ソースに対してではなく、外部メタデータのコレクション内の列に対して、入力または出力コレクション内の列が直接検証されるためです。 外部データ ソースへの接続が確立されていないとき、または、コンポーネントは切断されている検証を実行する必要があります、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A>プロパティは**false**です。  
  
 次のコード例は、コンポーネントの外部メタデータ列のコレクションに対し、検証を実行するコンポーネントの実装です。  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  

## <a name="see-also"></a>参照  
 [データ フロー](../../../integration-services/data-flow/data-flow.md)  
  
  

