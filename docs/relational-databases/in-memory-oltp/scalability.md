---
title: スケーラビリティ | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ad3dd62bbf82314be6b981944186711eaa5ce62b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766078"
---
# <a name="scalability"></a>スケーラビリティ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SQL Server 2016 では、メモリ最適化テーブル用のディスク上ストレージに対するスケーラビリティ機能が強化されています。  
  
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
  
 インメモリ OLTP エンジンは FILESTREAM に基づくメモリ最適化ファイル グループを引き続き使用しますが、ファイル グループ内の個々のファイルは FILESTREAM から切り離されています。 これらのファイルは、インメモリ OLTP エンジンによってフル マネージドです (作成、削除、ガベージ コレクションなど)。 [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) はサポートされていません。  
  
  
