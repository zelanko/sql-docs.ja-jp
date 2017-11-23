---
title: "suspect_pages (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- suspect_page_table
- suspect_page_table_TSQL
dev_langs: TSQL
helpviewer_keywords:
- suspect_pages system table
- suspect pages [SQL Server]
ms.assetid: 119c8d62-eea8-44fb-bf72-de469c838c50
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3dba370508c90a07cc66c4f4ef97c8d3d21d82c7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="suspectpages-transact-sql"></a>suspect_pages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マイナー 823 エラーまたは 824 エラーで失敗したページごとに 1 行が含まれています。 このテーブルには、問題がある可能性はあるものの、実際には問題がないことも考えられるページが格納されます。 未確認のページが修復されたら、その状態は更新で、 **event_type**列です。  
  
 次の表は、最大 1,000 行にある場合は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|このページが適用されるデータベースの ID。|  
|**file_id**|**int**|データベース内のファイルの ID です。|  
|**page_id**|**bigint**|問題があると考えられるページの ID。 すべてのページには 32 ビット値のページ ID が付けられており、データベース内のページの場所を識別します。 **Page_id**は 8 KB ページのデータ ファイルへのオフセット。 各ページ ID はファイル内で一意です。|  
|**event_type**|**int**|エラーの種類。次のいずれかになります。<br /><br /> 1 = 問題があると考えられるページ (ディスク エラーなど) の原因となった 823 エラー、または、不正なチェックサムまたは破損ページ (不適切なページ ID) 以外の 824 エラー。<br /><br /> 2 = 不正なチェックサム。<br /><br /> 3 = 破損ページ。<br /><br /> 4 = 復元済み (不正とマークされた後、復元されたページ)。<br /><br /> 5 = 修復済み (DBCC で修復されたページ)。<br /><br /> 7 = DBCC により割り当て解除。|  
|**error_count**|**int**|エラーの発生回数。|  
|**last_update_date**|**datetime**|最終更新日時のタイムスタンプ。|  
  
## <a name="permissions"></a>Permissions  
 **msdb** に対するアクセスを持つユーザー は、 **suspect_pages** テーブルのデータを読み取ることができます。 suspect_pages テーブルに対する UPDATE 権限を持つすべてのユーザーは、そのレコードを更新できます。 **msdb** の **db_owner** 固定データベース ロールのメンバーまたは **sysadmin** 固定サーバー ロールのメンバーは、レコードの挿入、更新、および削除を行うことができます。  
  
## <a name="see-also"></a>参照  
 [ページ復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [Database Suspect Data Page イベント クラス](../../relational-databases/event-classes/database-suspect-data-page-event-class.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
