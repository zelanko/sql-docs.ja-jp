---
title: "スクリプト コンポーネントのエラー出力のシミュレート |Microsoft ドキュメント"
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
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 0af8434531660958557928376cf8a4fd19ca9e68
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="simulating-an-error-output-for-the-script-component"></a>スクリプト コンポーネントに対するエラー出力のシミュレート
  エラー行の自動処理のスクリプト コンポーネントでエラー出力として出力を直接構成することはできませんが、別の出力を作成するか、可能な場合はスクリプトで条件ロジックを使用してこの出力に行を送信することによって、組み込みエラー出力の機能を再現することができます。 2 つの出力列を追加してエラー番号、およびエラーが発生した列の ID を受け取ることにより、組み込みエラー出力の動作を模倣することもできます。  
  
 事前定義された特定の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードに対応するエラーの説明を追加する場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> メソッドを使用できます。これは、スクリプト コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> プロパティから使用できます。  
  
## <a name="example"></a>例  
 次に示す例では、2 つの同期出力を持つ変換として構成された、スクリプト コンポーネントを使用します。 このスクリプト コンポーネントの目的は、AdventureWorks サンプル データベースの住所データから、エラー行をフィルター選択することです。 この架空の例では、北米の顧客向けプロモーションを準備中であり、北米以外の住所をフィルターによって除外する必要があるものとします。  
  
#### <a name="to-configure-the-example"></a>例を構成するには  
  
1.  新しいスクリプト コンポーネントの作成前に、接続マネージャーを作成し、AdventureWorks サンプル データベースから住所データを選択するデータ フローの変換元を構成します。 この例では CountryRegionName 列のみを調べるので、単純に Person.vStateCountryProvinceRegion ビューを使用できます。また、Person.Address、Person.StateProvince、および Person.CountryRegion の表を結合して、データを選択することもできます。  
  
2.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。 開く、**スクリプト変換エディター**です。  
  
3.  **スクリプト** ページで、設定、 **scriptlanguage**プロパティをスクリプトのコードを使用するスクリプト言語です。  
  
4.  **[スクリプトの編集]** をクリックして、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) を開きます。  
  
5.  **Input0_ProcessInputRow**メソッドを入力するか次に示すサンプル コードを貼り付けます。  
  
6.  VSTA を閉じます。  
  
7.  **入力列** ページで、スクリプト変換で処理する列を選択します。 この例では CountryRegionName 列のみを使用します。 選択しなかった使用可能な入力列は、データ フロー内で変更されず、そのまま渡されます。  
  
8.  **入力と出力**ページ、新しい追加し、2 番目の出力を設定その**SynchronousInputID**値でもあると、入力の id 値の**SynchronousInputID**既定の出力プロパティです。 設定、 **ExclusionGroup**両方の出力の各行が 2 つの出力の 1 つのみに転送されることを示すために同じ 0 ではない値 (たとえば、1) プロパティです。 新しいエラー出力に、"MyErrorOutput" などのわかりやすい名前を付けます。  
  
9. 必要なエラー情報を取得するため、追加の出力列を新しいエラー出力に追加します。エラー コード、エラーが発生した列の ID、エラーの説明などを含めることができます。 この例では、新しい列 ErrorColumn および ErrorMessage を作成しています。 事前定義された [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラーを独自の実装で検出する場合、エラー番号用の ErrorCode 列を必ず追加してください。  
  
10. スクリプト コンポーネントがエラー状態を確認する入力列 (複数の場合もある) の ID 値を書き留めます。 この例では、この列 ID を使用して ErrorColumn 値を設定します。  
  
11. 閉じる、**スクリプト変換エディターです。**  
  
12. スクリプト コンポーネントの出力を、適切な変換先にアタッチします。 フラット ファイル変換先は、アドホック テスト用に構成する最も簡単です。  
  
13. パッケージを実行します。  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
## <a name="see-also"></a>参照  
 [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)   
 [データ フロー コンポーネントでエラー出力の使用](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [スクリプト コンポーネントによる同期変換の作成](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
  
  

