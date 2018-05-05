---
title: Stretch Database の拡張ストアド プロシージャ (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e302aba2baf35f7a01f7242b2fa0eaaad45ee18f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Stretch Database の拡張ストアド プロシージャ (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 このセクションでは、Stretch Database に関連付けられている拡張ストアド プロシージャについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
[sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)ローカルの Stretch 対応データベースとリモート Azure データベース間で認証された接続を削除します。

[sys.sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)確実に、リモート Azure データベースの完全復元場合は、復元が必要になるステージング テーブル内の SQL Server が保持される移行データの時間数を取得します。
  
 [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) Stretch に対して有効になっているローカル データベースと、リモート データベース間で認証された接続を復元します。
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 リモートの Azure テーブルに格納されているバッチ ID を持つ最近に移行されたデータの Stretch 対応 SQL Server テーブルに格納されているバッチ ID を調整します。 
 
[sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md)内の列に、リモート Azure テーブルに列の整合性を保ちます、Stretch 対応 SQL Server テーブル。
 
 [sys.sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md)リモート テーブルでインデックスを調整するスキーマ タスク キューに配置します。
 
 [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)現在 Stretch 対応データベースとそのテーブルに対するクエリがローカルおよびリモートの両方のデータ (既定)、またはローカル データだけを返すかどうかを指定します。
 
 [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)確実に、リモート Azure データベースの完全復元場合は、復元が必要になるステージング テーブルで SQL Server が保持される移行データの時間数を設定します。
 
 [sys.sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md)から SQL Server がリモート Azure サーバーへの接続をテストし、データの移行を妨げる可能性のある問題を報告します。
 
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
