---
title: Stretch Database の拡張ストアド プロシージャ (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5acbd4a14de04df412d71fb4ec8fd7d40e8fb7a8
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65979981"
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Stretch Database の拡張ストアド プロシージャ (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 このセクションでは、Stretch Database に関連する拡張ストアド プロシージャについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
[sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)ローカルの Stretch 対応データベースとリモート Azure データベース間の認証された接続を削除します。

[sys.sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)復元が必要な場合、リモート Azure データベースの完全復元をことを確認するためにステージング テーブル内の SQL サーバーが保持する移行されたデータの時間数を取得します。
  
 [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)のストレッチを有効になっているローカル データベースとリモート データベース間で認証された接続を復元します。
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 リモート Azure テーブルに格納されているバッチ ID を持つ最も最近移行したデータの SQL Server の拡張が有効なテーブルに格納されているバッチ ID を調整します。 
 
[sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) Stretch 対応 SQL Server テーブルの列に、リモート Azure テーブルの列を調整します。
 
 [sys.sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md)リモート テーブルのインデックスを調整するスキーマ タスク キューに配置します。
 
 [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) Stretch が有効な現在のデータベースとそのテーブルに対するクエリが、ローカルとリモートの両方のデータ (既定)、またはローカルのデータのみを返すかどうかを指定します。
 
 [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)復元が必要な場合、リモート Azure データベースの完全復元をことを確認するためにステージング テーブルでの SQL Server に移行したデータの時間数を設定します。
 
 [sys.sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) SQL Server から、リモート Azure サーバーへの接続をテストし、データの移行を妨げる可能性のある問題が報告されました。
 
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
