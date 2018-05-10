---
title: NewOrg テーブルの最適化 | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be243734f05365ea7376e2e48e30479e46a7865c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-3---optimizing-the-neworg-table"></a>レッスン 1-3 - NewOrg テーブルの最適化
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
「 **既存の階層データを使用したテーブルの設定** 」の作業で作成した [NewOrd](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) テーブルにはすべての従業員情報が格納されており、その階層構造は **hierarchyid** データ型によって表されています。 ここでは、 **hierarchyid** 列の検索をサポートする新しいインデックスを追加します。  
  
## <a name="clustered-index"></a>クラスター化インデックス  
**hierarchyid** 列 (**OrgNode**) は、 **NewOrg** テーブルの主キーです。 **OrgNode** 列に一意性を持たせるため、このテーブルには作成時に **PK_NewOrg_OrgNode** という名前のクラスター化インデックスが格納されています。 このクラスター化インデックスは、テーブルの深さ優先検索もサポートしています。  
  
## <a name="nonclustered-index"></a>非クラスター化インデックス  
この手順では、一般的な検索をサポートする 2 つの非クラスター化インデックスを作成します。  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>効率的な検索のため NewOrg テーブルにインデックスを付けるには  
  
1.  階層の同じレベルでのクエリを容易にするには、 [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) メソッドを使用して、階層内のレベルを格納する計算列を作成します。 次に、レベルと **Hierarchyid**に基づく複合インデックスを作成します。 次のコードを実行すると、計算列と幅優先のインデックスが作成されます。  
  
    ```  
    ALTER TABLE HumanResources.NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON HumanResources.NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  **EmployeeID** 列に一意のインデックスを作成します。 これは、 **EmployeeID** の番号によって 1 人の従業員を検索する従来の単一参照です。 次のコードを実行すると、 **EmployeeID**のインデックスが作成されます。  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON HumanResources.NewOrg(EmployeeID) ;  
    GO
    ```  
  
3.  次のコードを実行して、3 種類の各インデックスの順にテーブルからデータを取得します。  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM HumanResources.NewOrg   
    ORDER BY OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY H_Level, OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  結果セットを比較して、順序がどのように格納されているかをインデックスの種類ごとに確認します。 それぞれの出力の最初の 4 行だけを以下に示します。  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    深さ優先のインデックス : 従業員のレコードは、それぞれのマネージャーのレコードに隣接して格納されます。  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    ```

    **EmployeeID** 優先のインデックス: 行は **EmployeeID** の順に格納されます。  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    /1/1/5/1/   0x5AE358    4   12  adventure-works\thierry0
    ```
  
> [!NOTE]  
> 深さ優先のインデックスと幅優先のインデックスの違いを示す図については、「[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)」を参照してください。  
  
#### <a name="to-drop-the-unnecessary-columns"></a>不要な列を削除するには  
  
1.  **ManagerID** 列が表す従業員とマネージャーのリレーションシップは、現在は **OrgNode** 列によって表されるようになっています。 **ManagerID** 列を必要とするアプリケーションが他にない場合は、次のステートメントを使用してこの列を削除することを検討します。  
  
    ```  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  **EmployeeID** 列も冗長です。 各従業員は、 **OrgNode** 列によって一意に識別されます。 **EmployeeID** 列を必要とするアプリケーションが他にない場合は、次のコードを使用して、インデックスを削除した後に列を削除することを検討します。  
  
    ```  
    DROP INDEX EmpIDs_unq ON HumanResources.NewOrg ;  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a>元のテーブルを新しいテーブルに置き換えるには  
  
1.  元のテーブルに追加のインデックスや制約が格納されている場合は、それらを **NewOrg** テーブルに追加します。  
  
2.  古い **EmployeeDemo** テーブルを新しいテーブルに置き換えます。 次のコードを実行すると、古いテーブルが削除され、新しいテーブルの名前がその古い名前に変更されます。  
  
    ```  
    DROP TABLE HumanResources.EmployeeDemo ;  
    GO  
    sp_rename 'HumanResources.NewOrg', 'EmployeeDemo' ;  
    GO  
    ```  
  
3.  次のコードを実行して、最終的なテーブルを確認します。  
  
    ```  
    SELECT * FROM HumanResources.EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[まとめ : テーブルの階層構造への変換](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
  
