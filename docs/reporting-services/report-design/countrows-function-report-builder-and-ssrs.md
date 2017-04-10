---
title: "CountRows 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# CountRows 関数 (レポート ビルダーおよび SSRS)
  NULL 値の行を含めて、指定されたスコープ内の行数を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 構文  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### パラメーター  
 *スコープ (scope)*  
 (**String**) カウントするレポート アイテムを含むデータセット、データ領域、またはグループの名前です。  
  
 *再帰*  
 (**列挙型**) 省略可。 **Simple** (既定値) または **RdlRecursive** です。 集計を再帰的に実行するかどうかを指定します。  
  
## 戻り値の型  
 **Integer**値を返します。  
  
## 解説  
 **CountRows** は、指定されたスコープ内のすべての行 (NULL 値を持つ行を含む) をカウントします。  
  
 *scope* の値には、式を指定することができません。また、この値では、現在のスコープまたはコンテナー スコープを参照する必要があります。  
  
 詳細については、「[集計関数リファレンス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)」および「[合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)」を参照してください。  
  
 再帰的集計の詳細については、「[複数の再帰型階層グループの作成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## 例  
 次のコード例では、(式 `GroupbyCategory` に基づいた) `[Category]` という名前の行グループ内の行数を計算する式を示します。  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## 参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  