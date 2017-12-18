---
title: "スケーラビリティ | Microsoft Docs"
ms.custom: 
ms.date: 08/27/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a9657320f92fd50b8d07d255e863cb5aebba46f0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="scalability"></a>スケーラビリティ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] SQL Server 2016 では、メモリ最適化テーブル用のディスク上ストレージに対するスケーラビリティ機能が強化されています。  
  
-   **メモリ最適化テーブルを保持する複数のスレッド**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のリリースでは、メモリ最適化テーブルへの変更についてトランザクション ログをスキャンし、メモリ最適化テーブルをチェックポイント ファイル (データ ファイルや差分ファイルなど) に保持する 1 つのオフライン チェックポイント スレッドが存在しました。 使用するコア数が多い場合、1 つのオフライン チェックポイント スレッドでは処理が遅れることがありました。  
  
     [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]では、メモリ最適化テーブルへの変更を保持する複数の同時実行スレッドがあります。  
  
-   **マルチ スレッドの回復**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のリリースでは、回復操作の一環としてのログ適用がシングル スレッド化されていました。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]では、ログ適用はマルチ スレッドです。  
  
-   **MERGE 操作**  
  
     MERGE 操作はマルチ スレッドになりました。  
  
-   **動的管理ビュー**  
  
     [sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) および [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) は大幅に変更されました。  
  
 マルチ スレッドのマージは負荷に応じて実行されるため、手動マージは無効になっています。  
  
 インメモリ OLTP エンジンは FILESTREAM に基づくメモリ最適化ファイル グループを引き続き使用しますが、ファイル グループ内の個々のファイルは FILESTREAM から切り離されています。 これらのファイルは、インメモリ OLTP エンジンによって完全に管理されています (作成、削除、ガベージ コレクションなど)。 [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) はサポートされていません。  
  
  
