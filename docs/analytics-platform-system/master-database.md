---
title: Master データベースの並列データ ウェアハウス |Microsoft ドキュメント
description: Parallel Data Warehouse で master データベースについて説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: bf07b9c27e08a49cb0866b177a0ec37fed4528a0
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538542"
---
# <a name="master-database---parallel-data-warehouse"></a>Master データベースの並列データ ウェアハウス
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
  
