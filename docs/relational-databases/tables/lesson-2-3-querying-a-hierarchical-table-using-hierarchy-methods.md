---
title: "階層的な手法を使用した階層テーブルのクエリ | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
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
helpviewer_keywords: HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
caps.latest.revision: "18"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5cdd782633ee4a2cf6970c9ce838bd623039a013
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-2-3---querying-a-hierarchical-table-using-hierarchy-methods"></a>レッスン 2-3 - 階層的な手法を使用した階層テーブルのクエリ
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] HumanResources.EmployeeOrg テーブルに完全にデータが設定されたので、ここでは階層的な手法のいくつかを使用して階層をクエリする方法を示します。  
  
### <a name="to-find-subordinate-nodes"></a>下位要素を検索するには  
  
1.  Sariya には 1 人の部下がいます。 Sariya の部下に対するクエリを実行するには、 [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) メソッドを使用する次のクエリを実行します。  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
    結果には、Sariya と Wanida の両方が表示されます。 Sariya は、0 レべルの子孫であるために表示されています。 Wanida は 1 レベルの子孫です。  
  
2.  [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md) メソッドを使用してこの情報に対してクエリを実行することもできます。 `GetAncestor` 返そうとしているレベルの引数を受け取ります。 Wanida は Sariya よりも 1 つ下のレベルであるため、次のコードに示すように `GetAncestor(1)` を使用します。  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
    この場合、結果には Wanida のみが表示されます。  
  
3.  次に、 `@CurrentEmployee` を David (EmployeeID 6) に、レベルを 2 にそれぞれ変更します。 次のコードを実行した場合も Wanida が返されます。  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
    この場合は、David に直属する 2 つ下のレベルの Mary も返されます。  
  
### <a name="to-use-getroot-and-getlevel"></a>GetRoot および GetLevel を使用するには  
  
1.  階層が大きくなるにつれ、メンバーが階層内のどこに位置するのかを確認するのが難しくなります。 各行が階層内の何レベル下にあるかを検索するには、 [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) メソッドを使用します。 すべての行のレベルを表示するには次のコードを実行します。  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  階層内のルート ノードを検索するには、 [GetRoot](../../t-sql/data-types/getroot-database-engine.md) メソッドを使用します。 次のコードは、ルートである 1 つの行を返します。  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
次に、階層を再編成します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[階層的な手法を使用した階層テーブルのデータの並べ替え](../../relational-databases/tables/lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
