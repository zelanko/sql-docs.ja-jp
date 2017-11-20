---
title: "データ移行の監視とトラブルシューティング (Stretch Database) | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2016
ms.prod: stretch-database
ms.prod_service: sql-non-specified
ms.service: database-engine
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, monitoring
- monitoring Stretch Database
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 91c10b51a3fec9ccc96c3aa23100abdf2a60ba81
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="monitor-and-troubleshoot-data-migration-stretch-database"></a>データ移行の監視とトラブルシューティング (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch Database モニターでデータ移行を監視するには、SQL Server Management Studio でデータベースについて **[タスク]、[Stretch]\(ストレッチ)、[Monitor]\(監視)** の順に選択します。  
  
## <a name="check-the-status-of-data-migration-in-the-stretch-database-monitor"></a>Stretch Database モニターでのデータ移行の状態の確認  
 SQL Server Management Studio でデータベースについて **[タスク]、[Stretch]\(ストレッチ)、[Monitor]\(監視)** の順に選択して Stretch Database モニターを開き、データ移行を監視します。  
  
-   モニターの上部には、Stretch 対応 SQL Server データベースとリモート Azure データベースの両方についての一般情報が表示されます。  
  
-   モニターの下部には、データベース内の各 Stretch 対応テーブルに関するデータ移行の状態が表示されます。  
  
 ![Stretch データベース モニター](../../sql-server/stretch-database/media/stretch-monitor.PNG "Stretch データベース モニター")  
  
##  <a name="Migration"></a> 動的管理ビューでのデータ移行の状態の確認  
 動的管理ビュー **sys.dm_db_rda_migration_status** を開いて、移行されたバッチ数とデータ行数を確認します。 詳細については、「[sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md)」を参照してください。  
  
##  <a name="Firewall"></a> データ移行のトラブルシューティング  
 **対象の Stretch 対応テーブルの行が Azure に移行されていません。何が問題なのでしょうか。**  
 移行に影響を与え得る問題は複数あります。 次の点を確認してください。  
  
-   SQL Server コンピューターに対するネットワーク接続を確認する。  
  
-   SQL Server からリモート エンドポイントへの接続が Azure ファイアウォールによってブロックされていないかどうかを確認する。  
  
-   動的管理ビュー **sys.dm_db_rda_migration_status** で最新のバッチの状態を確認する。 エラーが発生した場合は、バッチの error_number、error_state、error_severity の値を確認します。  
  
    -   ビューの詳細については、「[sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md)」を参照してください。  
  
    -   SQL Server エラー メッセージの内容の詳細については「[sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)」を参照してください。  
  
 **ローカル サーバーからの接続が Azure ファイアウォールによってブロックされています。**  
 SQL Server がリモート Azure サーバーと通信できるように、Azure サーバーの Azure ファイアウォール設定にルールを追加する必要があります。  
  
## <a name="see-also"></a>参照  
 [Stretch Database の管理とトラブルシューティング](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
  

