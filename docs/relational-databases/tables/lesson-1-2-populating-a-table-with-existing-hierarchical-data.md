---
title: "既存の階層データを使用したテーブルの設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 49f9580f99974d4453a7633c6640f8b5ca418e35
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-1-2---populating-a-table-with-existing-hierarchical-data"></a>レッスン 1-2 - 既存の階層データを使用したテーブルの設定
ここでは、新しいテーブルを作成して、そのテーブルに **EmployeeDemo** テーブルのデータを設定します。 この作業には、次の手順があります。  
  
-   **hierarchyid** 列を含む新しいテーブルを作成します。 この列を、既存の **EmployeeID** 列や **ManagerID** 列の代わりに使用してもかまいません。 ただし、これらの列は保持する必要があります。 これは、既存のアプリケーションがこれらの列を参照している可能性があるためでもあり、転送後のデータをわかりやすくするためでもあります。 テーブル定義では、 **OrgNode** が主キーであることを指定します。したがって、この列には一意の値を格納する必要があります。 **OrgNode** 列のクラスター化インデックスは、 **OrgNode** シーケンスのデータを格納します。  
  
-   各管理者に直属する従業員の数を追跡するために使用する一時テーブルを作成します。  
  
-   新しいテーブルを、 **EmployeeDemo** テーブルのデータを使用して設定します。  
  
### <a name="to-create-a-new-table-named-neworg"></a>NewOrg という名前の新しいテーブルを作成するには  
  
-   クエリ エディター ウィンドウで、次のコードを実行し、 **HumanResources.NewOrg**という名前の新しいテーブルを作成します。  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a>#Children という名前の一時テーブルを作成するには  
  
1.  **Num** という名前の列を持つ **#Children** という名前の一時テーブルを作成します。この列は、各ノードの子の数を格納します。  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  インデックスを作成します。このインデックスによって、 **NewOrg** テーブルを設定するクエリの速度が大幅に向上します。  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a>NewOrg テーブルを設定するには  
  
1.  再帰クエリでは、集計を含むサブクエリが禁止されています。 代わりに、 **ROW_NUMBER()** メソッドを使用して [Num](../../t-sql/functions/row-number-transact-sql.md) 列を設定する次のコードによって、 **#Children** テーブルを設定します。  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  **#Children** テーブルを確認します。 **Num** 列に、各管理者の連続する番号がどのように格納されているかに注目してください。  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    `EmployeeID ManagerID Num`  
  
    `---------- --------- ---`  
  
    `1        NULL       1`  
  
    `2         1         1`  
  
    `3         1         2`  
  
    `4         2         1`  
  
    `5         2         2`  
  
    `6         2         3`  
  
    `7         3         1`  
  
    `8         3         2`  
  
    `9         4         1`  
  
    `10        4         2`  
  
3.  **NewOrg** テーブルを設定します。 GetRoot メソッドと ToString メソッドを使用して **Num** 値を **hierarchyid** 形式に連結し、結果の階層値で **OrgNode** 列を更新します。  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  **hierarchyid** 列は、文字形式に変換すると、よりわかりやすくなります。 次のコードを実行して、 **NewOrg** テーブルのデータを確認します。このコードには、 **OrgNode** 列の 2 つの表記が含まれています。  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
    **LogicalNode** 列は、階層を表す読みやすいテキスト形式に **hierarchyid** 列を変換します。 残りの作業では、 `ToString()` メソッドを使用して、 **hierarchyid** 列の論理形式を表示します。  
  
5.  不要になった一時テーブルを削除します。  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
次の作業では、階層構造をサポートするインデックスを作成します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[NewOrg テーブルの最適化](../../relational-databases/tables/lesson-1-3-optimizing-the-neworg-table.md)  
  
  
  
