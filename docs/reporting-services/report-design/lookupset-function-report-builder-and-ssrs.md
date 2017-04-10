---
title: "LookupSet 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# LookupSet 関数 (レポート ビルダーおよび SSRS)
  名前と値のペアを含むデータセットから、指定された名前に対応する一連の値を返します  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 構文  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### パラメーター  
 *source_expression*  
 (**Variant**) 現在のスコープ内で評価される式。参照する名前またはキーを指定します。 たとえば、`=Fields!ID.Value` のようにします。  
  
 *destination_expression*  
 (**Variant**) データセット内の各行に対して評価される式。照合する名前またはキーを指定します。 たとえば、`=Fields!CustomerID.Value` のようにします。  
  
 *result_expression*  
 (**Variant**) *source_expression* = *destination_expression* であるデータセットの行で評価され、取得する値を指定する式。 たとえば、`=Fields!PhoneNumber.Value` のようにします。  
  
 *データセット (dataset)*  
 レポート内のデータセットの名前を指定する定数。 たとえば、"ContactInformation" のように指定します。  
  
## 戻り値  
 **VariantArray**を返します。一致する結果がなかった場合は、 **Nothing** を返します。  
  
## 解説  
 指定したデータセットで、名前と値のペアについて 1 対多のリレーションシップが存在する場合、**LookupSet** を使用して一連の値を取得します。 たとえば、テーブル内の顧客識別子に対して **LookupSet** を使用して、データ領域にバインドされていないデータセットから、顧客に関連付けられている電話番号をすべて取得することができます。  
  
 **LookupSet** を実行すると、次の処理が行われます。  
  
-   ソースの式を現在のスコープ内で評価します。  
  
-   フィルターを適用した後で、指定されたデータセットの照合順序に基づき、指定されたデータセットの各行に対して変換先の式を評価します。  
  
-   変換元の式と変換先の式が一致するたびに、データセット内のその行に対して結果式を評価します。  
  
-   結果式の一連の値を返します。  
  
 指定した名前に対応する、名前と値のペアを含むデータセットに 1 対 1 のリレーションシップが存在する場合、このデータセットから 1 つの値を取得するには、[Lookup 関数 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/lookup-function-report-builder-and-ssrs.md) を使用します。 一連の値に対して **Lookup** を呼び出すには、[Multilookup 関数 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/multilookup-function-report-builder-and-ssrs.md) を使用します。  
  
 次の制限があります。  
  
-   **LookupSet** は、すべてのフィルター式が適用された後で評価されます。  
  
-   1 レベルの参照のみがサポートされます。 変換元、変換先、または結果の式に、Lookup 関数への参照を含めることはできません。  
  
-   変換元および変換先の式は、同じデータ型として評価される必要があります。  
  
-   変換元、変換先、結果の式には、レポート変数またはグループ変数への参照を含めることができません。  
  
-   **LookupSet** は、次のレポート アイテムを求める式として使用することはできません。  
  
    -   データ ソースの動的な接続文字列。  
  
    -   データセット内の計算フィールド。  
  
    -   データセット内のクエリ パラメーター。  
  
    -   データセット内のフィルター。  
  
    -   レポート パラメーター。  
  
    -   Report.Language プロパティ。  
  
 詳細については、「[集計関数リファレンス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)」および「[合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)」を参照してください。  
  
## 例  
 次の例では、販売区域の識別子である TerritoryGroupID を含むデータセットにテーブルがバインドされているとします。 別のデータセットである "Stores" には、販売区域の全店舗の一覧が含まれ、販売区域識別子 ID と、店舗名を表す StoreName が含まれています。  
  
 次の式では、"Stores" という名前のデータセットの各行に対して **LookupSet** を実行し、TerritoryGroupID の値を ID と比較します。 一致するたびに、その行の StoreName フィールドの値が結果セットに追加されます。  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## 例  
 **LookupSet** はオブジェクトのコレクションを返すため、結果式をテキスト ボックスに直接表示することはできません。 コレクション内の各オブジェクトの値を文字列として連結することはできます。  
  
 一連のオブジェクトから区切り記号付きの文字列を作成するには、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数である **Join** を使用します。 コンマを区切り記号として使用し、オブジェクトを 1 行に結合します。 レンダラーによっては、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の改行 (`vbCrLF`) を区切り記号として使用し、各値を新しい 1 つの行に表示することもできます。  
  
 次の式では、テキスト ボックスの Value プロパティとして使用したときに、**Join** を使用して一覧を作成します。  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## 例  
 数回しか表示されないテキスト ボックスでは、テキスト ボックスの値を表示する HTML を生成するカスタム コードを追加してもよいでしょう。 テキスト ボックス内に HTML を生成すると追加の処理が必要になるため、数千回も表示されるようなテキスト ボックスの場合、この方法はお勧めできません。  
  
 次の [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数をレポート定義の Code ブロックにコピーします。 **MakeList** では、*result_expression* で返されたオブジェクト配列を受け取り、HTML タグを使用して、順序指定されないリストを生成します。 **Length** は、オブジェクト配列内の項目数を返します。  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## 例  
 HTML を生成するには、関数を呼び出す必要があります。 次の式をテキスト ボックスの Value プロパティに貼り付け、テキストのマークアップの種類を HTML に設定します。 詳細については、「[レポートへの HTML の追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-html-into-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## 参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  