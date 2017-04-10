---
title: "HumanResources.myTeam サンプル テーブル (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "myTeam サンプル テーブル [SQL Server]"
  - "一括インポート [SQL Server], 例"
  - "一括エクスポート [SQL Server], 例"
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# HumanResources.myTeam サンプル テーブル (SQL Server)
  「[一括データのインポートおよびエクスポート](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)」のコード例の大部分では、**myTeam** という名前の特殊なテスト用テーブルが必要になります。 これらのコード例を実行する前に、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの **HumanResources** スキーマに **myTeam** テーブルを作成する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]  は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のサンプル データベースの 1 つです。  
  
 **myTeam** には、次の列が含まれています。  
  
|列|データ型|NULL 値の許容|説明|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|**smallint**|不可|行の主キー。 チーム メンバーの従業員 ID。|  
|**名前**|**nvarchar (50)**|不可|チーム メンバーの名前。|  
|**[タイトル]**|**nvarchar (50)**|[可]|チームにおける従業員の肩書き。|  
|**背景情報**|**nvarchar (50)**|不可|行が最後に更新された日時  (既定値)。|  
  
 **HumanResources.myTeam テーブルを作成するには**  
  
-   次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 **HumanResources.myTeam テーブルに行を設定するには**  
  
-   次の `INSERT` ステートメントでは、テーブルに 2 つの行を設定します。  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  これらのステートメントでは、4 番目の列 `Background` がスキップされます。 この行には既定値が設定されています。 この列をスキップすると、この `INSERT` ステートメントを実行した際に、この列が空欄のままになります。  
  
## 参照  
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  