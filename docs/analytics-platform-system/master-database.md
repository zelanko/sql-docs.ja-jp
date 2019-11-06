---
title: Master データベースの Parallel Data Warehouse |Microsoft Docs
description: Parallel Data Warehouse での master データベースについて説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9f37c7a85baea3b41f6016a57e4f57579b427719
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960652"
---
# <a name="master-database---parallel-data-warehouse"></a>Master データベースの Parallel Data Warehouse
SQL Server PDW の master データベースには、アプライアンス レベルのログイン情報と、データベース カタログが格納されます。 コントロールのノード上に存在する SQL Server マスター データベースになります。 そのため、SQL Server PDW のような機能を提供マスターを SQL Server に提供します。  
  
システム データベースの詳細については、次を参照してください。[システム データベース](system-databases.md)します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
次の一覧には、SQL Server PDW の master データベースで実行できない操作について説明します。  
  
*ことはできません。*  
  
-   マスターの差分バックアップを実行します。  
  
-   マスターでユーザー オブジェクトを作成します。  
  
-   マスターの照合順序を変更します。  
  
-   マスターの所有者を変更します。  
  
-   削除するか、マスターの名前を変更します。  
  
-   マスターへのアクセス許可を変更します。  
  
-   実行**DBCC SHRINKLOG**します。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスク|説明|  
|--------|---------------|  
|マスターの完全バックアップを作成します。|例:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />詳細については、次を参照してください。 [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)します。|  
|master データベースの復元|Master データベースを復元するには、使用、 [Master データベースの復元](restore-the-master-database.md)構成マネージャー ツールのページ。|  
|データベースのカタログ情報を表示します。|`SELECT * FROM master.sys.databases;`|  
|システム全体のログインと権限の情報を表示します。|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
