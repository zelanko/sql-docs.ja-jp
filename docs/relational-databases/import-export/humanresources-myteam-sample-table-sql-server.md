---
title: HumanResources.myTeam サンプル テーブル (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: import-export
ms.reviewer: ''
ms.suite: sql
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ee6230a7aac8dc4913a3d954fcae617787d8e9ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32935514"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>HumanResources.myTeam サンプル テーブル (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  「 [一括データのインポートおよびエクスポート](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) 」のコード例の大部分では、 **myTeam**という名前の特殊なテスト用テーブルが必要になります。 これらのコード例を実行する前に、 **データベースの** HumanResources **スキーマに** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] テーブルを作成する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のサンプル データベースの 1 つです。  
  
 **myTeam** には、次の列が含まれています。  
  
|[列]|データ型|NULL 値の許容|Description|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|**smallint**|不可|行の主キー。 チーム メンバーの従業員 ID。|  
|**名前**|**nvarchar (50)**|不可|チーム メンバーの名前。|  
|**Title**|**nvarchar (50)**|[可]|チームにおける従業員の肩書き。|  
|**背景情報**|**nvarchar (50)**|不可|行が最後に更新された日時 (既定値)。|  
  
**HumanResources.myTeam テーブルを作成するには**  
  
-   次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```sql
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
  
    ```sql
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
    >  これらのステートメントでは、4 番目の列 `Background`がスキップされます。 この行には既定値が設定されています。 この列をスキップすると、この `INSERT` ステートメントを実行した際に、この列が空欄のままになります。  
  
## <a name="see-also"></a>参照  
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
