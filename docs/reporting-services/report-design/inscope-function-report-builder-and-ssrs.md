---
title: "InScope 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# InScope 関数 (レポート ビルダーおよび SSRS)
  アイテムの現在のインスタンスが、指定したスコープ内にあるかどうかを示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 構文  
  
```  
InScope(scope)  
```  
  
#### パラメーター  
 *スコープ (scope)*  
 (**String**) スコープを指定するデータセット、データ領域、またはグループの名前です。  
  
## 戻り値の型  
 **Boolean** 値を返します。  
  
## 解説  
 **InScope** 関数では、レポート アイテムの現在のインスタンスのスコープを調べて、*scope* パラメーターで指定されたスコープのメンバーシップを確認します。  
  
 *Scope* には、式を指定することはできません。  
  
 **InScope** 関数は、通常、動的スコープを利用するデータ領域で使用されます。 たとえば、**InScope** をデータ領域のセル内のドリルスルー リンクに使用して、クリックされたセルに応じて異なるレポート名とパラメーター セットが返されるようにすることができます。 この例を以下に示します。  
  
-   次の式では、ドリルスルー リンクのレポート名として使用し、`Month` グループ内のセルがクリックされた場合は `ProductDetail` レポートが開き、それ以外のセルがクリックされた場合は `ProductSummary` レポートが開くようにしています。  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   次の式では、詳細レポート パラメーターの **Omit** プロパティに使用し、`Product` グループ内のセルがクリックされた場合のみ、目的のレポートにパラメーターが渡されるようにしています。  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 詳細については、「[集計関数リファレンス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)」および「[合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)」を参照してください。  
  
## 例  
 次のコード例では、アイテムの現在のインスタンスが、`Product` データセット、データ領域、またはグループのスコープにあるかどうかが示されます。  
  
```  
=InScope("Product")  
```  
  
## 参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  