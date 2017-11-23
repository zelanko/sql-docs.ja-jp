---
title: "データベース オブジェクトにアクセス権の付与 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5ccbacfe52541c59e12b992220f40806cae46bca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>レッスン 2-4-データベースのオブジェクトへのアクセスを許可します。
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]管理者からの SELECT を実行することができます、**製品**テーブルおよび**vw_Names**表示、および実行、 **pr_Names**プロシージャであるただし、Mary ことはできません。 Mary に必要な権限を付与するには、GRANT ステートメントを使用します。  
  
### <a name="procedure-title"></a>手順のタイトル  
  
1.  次のステートメントを実行して、 `Mary` ストアド プロシージャの `EXECUTE` 権限を `pr_Names` に与えます。  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
このシナリオでは、Mary はストアド プロシージャを使用して **Products** テーブルにのみアクセスできます。 Mary がビューに対して SELECT ステートメントを実行できるようにする場合は、 `GRANT SELECT ON vw_Names TO Mary`も実行する必要があります。 データベース オブジェクトへのアクセス権を削除するには、REVOKE ステートメントを使用します。  
  
> [!NOTE]  
> テーブル、ビュー、およびストアド プロシージャが同じスキーマに所有されていない場合は、権限を付与すると、複雑になります。  
  
## <a name="about-grant"></a>GRANT について  
ストアド プロシージャを実行するには、EXECUTE 権限が必要です。 データにアクセスしたり、データを変更するには、SELECT、INSERT、UPDATE、および DELETE 権限が必要です。 GRANT ステートメントは、テーブルを作成する権限など、他の権限にも使用されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[概要 : データベース オブジェクトに対する権限の構成](../t-sql/lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>参照  
[GRANT &#40;Transact-SQL&#41;](../t-sql/statements/grant-transact-sql.md)  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
  
  
  
