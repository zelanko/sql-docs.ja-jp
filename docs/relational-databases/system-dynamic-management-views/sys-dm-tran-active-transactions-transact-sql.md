---
title: sys.dm_tran_active_transactions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_active_transactions
- sys.dm_tran_active_transactions_TSQL
- dm_tran_active_transactions_TSQL
- dm_tran_active_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_active_transactions dynamic management view
ms.assetid: 154ad6ae-5455-4ed2-b014-e443abe2c6ee
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ce8289358c8efbff859d80411914712c3cfeddc7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmtranactivetransactions-transact-sql"></a>sys.dm_tran_active_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのトランザクションに関する情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_tran_active_transactions**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|データベース レベルではなくインスタンス レベルのトランザクションの ID。 これはインスタンス内のすべてのデータベースでのみ一意ですが、すべてのサーバー インスタンスにおいては一意ではありません。|  
|name|**nvarchar(32)**|トランザクション名。 トランザクションがマークされている場合、この名前が上書きされます。マークされた名前がトランザクション名と置き換わります。|  
|transaction_begin_time|**datetime**|トランザクションの開始時刻。|  
|transaction_type|**int**|トランザクションの種類です。<br /><br /> 1 = 読み取り/書き込みトランザクション<br /><br /> 2 = 読み取り専用トランザクション<br /><br /> 3 = システム トランザクション<br /><br /> 4 = 分散トランザクション|  
|transaction_uow|**uniqueidentifier**|分散トランザクションの、トランザクション作業単位 (UOW) 識別子。 MS DTC では UOW 識別子を使って分散トランザクションが処理されます。|  
|transaction_state|**int**|0 = トランザクションはまだ完全に初期化されていません。<br /><br /> 1 = トランザクションは初期化されていますが、開始されていません。<br /><br /> 2 = トランザクションはアクティブです。<br /><br /> 3 = トランザクションは終了しました。 これは、読み取り専用トランザクションに使用されます。<br /><br /> 4 = 分散トランザクションでコミット処理が開始されています。 これは、分散トランザクションのみに使用されます。 分散トランザクションはまだアクティブですが、追加の処理は行えません。<br /><br /> 5 = トランザクションは準備された状態で解決を待機しています。<br /><br /> 6 = トランザクションはコミットされました。<br /><br /> 7 = トランザクションはロールバック中です。<br /><br /> 8 = トランザクションはロールバックされています。|  
|transaction_status |**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_state|**int**|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (初回のリリースから[現在のリリース](http://go.microsoft.com/fwlink/p/?LinkId=299659))。<br /><br /> 1 = ACTIVE<br /><br /> 2 = PREPARED<br /><br /> 3 = COMMITTED<br /><br /> 4 = ABORTED<br /><br /> 5 = RECOVERED|  
|dtc_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_isolation_level|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|filestream_transaction_id|**varbinary (128)**|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (初回のリリースから[現在のリリース](http://go.microsoft.com/fwlink/p/?LinkId=299659))。<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="see-also"></a>参照  
 [sys.dm_tran_session_transactions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [sys.dm_tran_database_transactions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-database-transactions-transact-sql.md)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


