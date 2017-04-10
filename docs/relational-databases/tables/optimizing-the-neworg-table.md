---
title: "NewOrg テーブルの最適化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "テーブルの最適化"
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# NewOrg テーブルの最適化
「[既存の階層データを使用したテーブルの設定](../../relational-databases/tables/populating-a-table-with-existing-hierarchical-data.md)」の作業で作成した **NewOrd** テーブルにはすべての従業員情報が格納されており、その階層構造は **hierarchyid** データ型によって表されています。 ここでは、**hierarchyid** 列の検索をサポートする新しいインデックスを追加します。  
  
## クラスター化インデックス  
**hierarchyid** 列 (**OrgNode**) は、**NewOrg** テーブルの主キーです。 **OrgNode** 列に一意性を持たせるため、このテーブルには作成時に **PK_NewOrg_OrgNode** という名前のクラスター化インデックスが格納されています。 このクラスター化インデックスは、テーブルの深さ優先検索もサポートしています。  
  
## 非クラスター化インデックス  
この手順では、一般的な検索をサポートする 2 つの非クラスター化インデックスを作成します。  
  
#### 効率的な検索のため NewOrg テーブルにインデックスを付けるには  
  
1.  階層の同じレベルでのクエリを容易にするには、[GetLevel](../../t-sql/data-types/getlevel-database-engine.md) メソッドを使用して、階層内のレベルを格納する計算列を作成します。 次に、レベルと **Hierarchyid** に基づく複合インデックスを作成します。 次のコードを実行すると、計算列と幅優先のインデックスが作成されます。  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  **EmployeeID** 列に一意のインデックスを作成します。 これは、**EmployeeID** の番号によって 1 人の従業員を検索する従来の単一参照です。 次のコードを実行すると、**EmployeeID** のインデックスが作成されます。  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  次のコードを実行して、3 種類の各インデックスの順にテーブルからデータを取得します。  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  結果セットを比較して、順序がどのように格納されているかをインデックスの種類ごとに確認します。 それぞれの出力の最初の 4 行だけを以下に示します。  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    深さ優先のインデックス : 従業員のレコードは、それぞれのマネージャーのレコードに隣接して格納されます。  
  
    `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
    `/             0x         0         1      zarifin`  
  
    `/1/          0x58        1         2      tplate`  
  
    `/1/1/       0x5AC0       2         4      schai`  
  
    `/1/1/1/     0x5AD6       3         9      jwang`  
  
    `/1/1/2/     0x5ADA       3        10      malexander`  
  
    `/1/2/       0x5B40       2         5      elang`  
  
    `/1/3/       0x5BC0       2         6      gsmits`  
  
    `/2/         0x68         1         3      hjensen`  
  
    `/2/1/       0x6AC0       2         7      sdavis`  
  
    `/2/2/       0x6B40       2         8      norint`  
  
    **EmployeeID** 優先のインデックス: 行は **EmployeeID** の順に格納されます。  
  
    `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
    `/             0x         0         1      zarifin`  
  
    `/1/          0x58        1         2      tplate`  
  
    `/2/         0x68         1         3      hjensen`  
  
    `/1/1/       0x5AC0       2         4      schai`  
  
    `/1/2/       0x5B40       2         5      elang`  
  
    `/1/3/       0x5BC0       2         6      gsmits`  
  
    `/2/1/       0x6AC0       2         7      sdavis`  
  
    `/2/2/       0x6B40       2         8      norint`  
  
    `/1/1/1/     0x5AD6       3         9      jwang`  
  
    `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
> 深さ優先のインデックスと幅優先のインデックスの違いを示す図については、「[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)」を参照してください。  
  
#### 不要な列を削除するには  
  
1.  **ManagerID** 列が表す従業員とマネージャーのリレーションシップは、現在は **OrgNode** 列によって表されるようになっています。 **ManagerID** 列を必要とするアプリケーションが他にない場合は、次のステートメントを使用してこの列を削除することを検討します。  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  **EmployeeID** 列も冗長です。 各従業員は、**OrgNode** 列によって一意に識別されます。 **EmployeeID** 列を必要とするアプリケーションが他にない場合は、次のコードを使用して、インデックスを削除した後に列を削除することを検討します。  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### 元のテーブルを新しいテーブルに置き換えるには  
  
1.  元のテーブルに追加のインデックスや制約が格納されている場合は、それらを **NewOrg** テーブルに追加します。  
  
2.  古い **EmployeeDemo** テーブルを新しいテーブルに置き換えます。 次のコードを実行すると、古いテーブルが削除され、新しいテーブルの名前がその古い名前に変更されます。  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  次のコードを実行して、最終的なテーブルを確認します。  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## このレッスンの次の作業  
[まとめ : テーブルの階層構造への変換](../../relational-databases/tables/summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
  
