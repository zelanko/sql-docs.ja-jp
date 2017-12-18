---
title: "Employee テーブルの現在の構造の確認 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 599385dfefc12252d03a3e532e3d084077f72464
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-1---examining-the-current-structure-of-the-employee-table"></a>レッスン 1-1 - Employee テーブルの現在の構造の確認
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] サンプル [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースには、**HumanResources** スキーマに含まれる **Employee** テーブルがあります。 元のテーブルを変更しないように、この手順では、 **Employee** テーブルのコピーを作成して **EmployeeDemo**という名前を付けます。 例を単純にするために、元のテーブルから 5 列だけをコピーします。 次に、 **HumanResources.EmployeeDemo** テーブルに対してクエリを実行し、 **hierarchyid** データ型が使用されていないテーブル内のデータ構造を確認します。  
  
### <a name="to-copy-the-employee-table"></a>Employee テーブルをコピーするには  
  
1.  クエリ エディターのウィンドウで、次のコードを実行し、 **Employee** テーブルから新しいテーブルの **EmployeeDemo**にテーブル構造とデータをコピーします。  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>EmployeeDemo テーブルの構造とデータを確認するには  
  
-   この新しい **EmployeeDemo** テーブルは、新しい構造に移行可能な、既存のデータベースの一般的なテーブルを表しています。 クエリ エディター ウィンドウで次のコードを実行すると、テーブルで自己結合を使用して従業員と管理者のリレーションシップを示しているようすを確認できます。  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
    結果は合計 290 行にわたります。  
  
**ORDER BY** 句を使用していることによって、出力では、各管理レベルの直属の部下がまとめて表示されていることに注意してください。 たとえば、 **MgrID** 3 (roberto0) の 7 人の直属の部下がすべて左右に並べて表示されています。 実際に **MgrID** 3 に直属するすべての人をグループ化することは、不可能ではありませんが、かなり難しくなります。  
  
次の作業では、 **hierarchyid** データ型を使用して新しいテーブルを作成し、この新しいテーブルにデータを移動します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[既存の階層データを使用したテーブルの設定](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
  
