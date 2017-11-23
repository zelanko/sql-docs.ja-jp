---
title: "sys.dm_db_xtp_object_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_object_stats_TSQL
- sys.dm_db_xtp_object_stats
- dm_db_xtp_object_stats
- sys.dm_db_xtp_object_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_xtp_object_stats dynamic management view
ms.assetid: 07300b59-3cab-4d3e-8138-5ea8f584f88f
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b07eb152c42c2f9c991d99ff6e3256b62d1cef8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbxtpobjectstats-transact-sql"></a>sys.dm_db_xtp_object_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  各操作によって影響を受ける行の数を報告、[!INCLUDE[hek_2](../../includes/hek-2-md.md)]最後のデータベースからオブジェクトを再起動します。 トランザクションがコミットされたかロールバックされたかに関係なく、統計情報は操作の実行時に更新されます。  
  
 sys.dm_db_xtp_object_stats は、変化の著しいメモリ最適化テーブルを特定するために役立ちます。 各インデックスはパフォーマンスに影響するため、テーブル内でまったく使用されていないインデックスまたはほとんど使用されていないインデックスの削除を検討することができます。 ハッシュ インデックスがあれば、バケット数を定期的に再評価する必要があります。 詳細については、次を参照してください。[ハッシュ インデックスの適切なバケット数を決定する](http://msdn.microsoft.com/library/6d1ac280-87db-4bd8-ad43-54353647d8b5)です。  
  
 sys.dm_db_xtp_object_stats は、書き込みと書き込みの競合が発生しているメモリ最適化テーブルを特定するために役立ちます。このような競合は、アプリケーションのパフォーマンスに影響します。 たとえば、トランザクションの再試行ロジックがあれば、同じステートメントの実行が複数回必要になることがあります。 また、この情報を使用して、書き込みと書き込みのエラー処理を必要とするテーブル (およびビジネス ロジック) を特定することもできます。  
  
 このビューには、データベース内のメモリ最適化テーブルごとに 1 行のデータが格納されます。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|オブジェクトの ID です。|  
|row_insert_attempts|**bigint**|前回データベースが再起動されてから、コミットされたトランザクションおよび中断されたトランザクションの両方によってテーブルに挿入された行の数。|  
|row_update_attempts|**bigint**|前回データベースが再起動されてから、コミットされたトランザクションおよび中断されたトランザクションの両方によってテーブル内で更新された行の数。|  
|row_delete_attempts|**bigint**|前回データベースが再起動されてから、コミットされたトランザクションおよび中断されたトランザクションの両方によってテーブルから削除された行の数。|  
|write_conflicts|**bigint**|前回データベースが再起動されてから発生した書き込み競合の数。|  
|unique_constraint_violations|**bigint**|前回データベースが再起動されてから発生した UNIQUE 制約違反の数。|  
|object_address|**varbinary (8)**|内部使用のみです。|  
  
## <a name="permissions"></a>Permissions  
 現在のデータベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
