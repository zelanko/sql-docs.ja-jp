---
title: "master データベース (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c71617c0-6689-4f52-81c6-58f4cf7c7377
caps.latest.revision: "8"
ms.workload: not set
ms.openlocfilehash: 59acb3fb8c5c1913e8b4d656e9895b2810e19497
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="master-database"></a>master データベース
SQL Server PDW の master データベースは、アプライアンス レベルのログイン情報と、データベース カタログに格納します。 コントロールのノードに存在する SQL Server マスター データベースであります。 そのため、SQL Server PDW のような機能を提供マスターは、SQL Server に示されています。  
  
システム データベースの詳細については、次を参照してください。[システム データベース](system-databases.md)です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
次の一覧では、SQL Server PDW の master データベースに対して実行できない操作について説明します。  
  
*ことはできません。*  
  
-   Master データベースの差分バックアップを実行します。  
  
-   Master 内のユーザー オブジェクトを作成します。  
  
-   Master データベースの照合順序を変更します。  
  
-   Master データベースの所有者を変更します。  
  
-   ドロップまたはマスターの名前を変更します。  
  
-   マスターへのアクセス許可を変更します。  
  
-   実行**DBCC SHRINKLOG**です。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスク|Description|  
|--------|---------------|  
|Master データベースの完全バックアップを作成します。|例:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />詳細については、次を参照してください。 [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)です。|  
|Master データベースを復元します。|Master データベースを復元するには、使用、 [Master データベースの復元](restore-the-master-database.md) ページで、Configuration Manager ツール。|  
|データベースのカタログ情報を表示します。|`SELECT * FROM master.sys.databases;`|  
|システム全体のログインと権限の情報を表示します。|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
