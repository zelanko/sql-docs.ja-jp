---
title: "Last 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: 123b78a0-d6c9-4f78-b0e7-73b21854a250
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Last 関数 (レポート ビルダーおよび SSRS)
  指定された式の指定されたスコープの最後の値を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 構文  
  
```  
  
Last(expression, scope)  
```  
  
#### パラメーター  
 *式 (expression)*  
 (**Variant** または **Binary**) この集計関数の実行対象の式です (`=Fields!Fieldname.Value` など)。  
  
 *スコープ (scope)*  
 (**String**) (省略可) この関数の適用先となるレポート アイテムを含むデータセット、データ領域、またはグループの名前です。 *scope* を指定しない場合、現在のスコープが使用されます。  
  
## 戻り値の型  
 式の種類によって決まります。  
  
## 解説  
 **Last** 関数は、指定されたスコープですべての並べ替えおよびフィルター処理が適用された後、データセットの最後の値を返します。  
  
 **Last** 関数は、現在 (既定) のスコープ以外のスコープを使用してグループ化フィルター式で使用することはできません。  
  
 また、ページ ヘッダーで **Last** を使用して、ページの **ReportItems** コレクションから最後の値を返し、各ページの最初と最後のエントリを表示する辞書形式のヘッダーを作成することもできます。  
  
 *scope* の値は文字列定数である必要があり、式にすることはできません。 外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。 集計の集計では、入れ子になった集計に、子のスコープを指定できます。  
  
 *Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。  
  
-   入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。 式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。  
  
-   入れ子集計の*Scope* には、データセット名は使用できません。  
  
-   *Expression* には、 **First**、 **Last**、 **Previous**、または **RunningValue** の各関数を含めることができません。  
  
-   *Expression* には、 *recursive*を指定する入れ子集計を含めることができません。  
  
 詳細については、「[集計関数リファレンス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)」および「[合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)」を参照してください。  
  
 再帰的集計の詳細については、「[複数の再帰型階層グループの作成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## 例  
 次のコード例では、データ領域の `Category` グループの最後の製品番号が返されます。  
  
```  
=Last(Fields!ProductNumber.Value, "Category")  
```  
  
## 参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  