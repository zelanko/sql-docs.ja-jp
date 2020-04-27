---
title: インメモリ OLTP のシステムビュー、ストアドプロシージャ、Dmv、および待機の種類Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d047cbc4fe3ba3f4945acd9da4f627a05992e779
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62842401"
---
# <a name="system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp"></a>インメモリ OLTP 向けのシステム ビュー、ストアド プロシージャ、DMV、待機の種類
  このトピックでは、簡単な説明を行い、インメモリ OLTP をサポートする多くのデータベース オブジェクトへのリンクを提供します。  
  
### <a name="system-views"></a>システム ビュー  
  
|システム ビュー|説明|インメモリ OLTP 機能|  
|-----------------|-----------------|-----------------------------|  
|[sys.data_spaces &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-data-spaces-transact-sql)|ファイル グループにメモリ最適化データが含まれているかどうか確認します。|次の列には、**種類**と**type_desc**の追加値が表示されます。|  
|[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)|メモリ最適化テーブルにインデックスが付けられているか確認します。|次の列には、**種類**と**type_desc**の追加値が表示されます。|  
|[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql)|パラメーターが null 非許容であることを確認します (ネイティブコンパイルストアドプロシージャをより効率的に実行するため)。|**is_nullable**列。|  
|[all_sql_modules &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql)|ストアドプロシージャがネイティブにコンパイルされているかどうかを確認します。|**uses_native_compilation**列。|  
|[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)|ストアドプロシージャがネイティブにコンパイルされているかどうかを確認します。|**uses_native_compilation**列。|  
|[table_types &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-table-types-transact-sql)|テーブルがメモリ最適化されているか確認します。|**is_memory_optimized**列。|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|テーブルがメモリ最適化されているかどうかを確認し、テーブルの持続性の設定を確認します。|**持続性**、 **durability_desc**、 **is_memory_optimized**列。|  
|[sys.hash_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-hash-indexes-transact-sql)|メモリ最適化テーブルのハッシュ インデックスを表示します。|インメモリ OLTP 固有|  
  
### <a name="metadata-functions"></a>メタデータ関数  
  
|Metadata 関数|説明|インメモリ OLTP 機能|  
|-----------------------|-----------------|-----------------------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|データベース オブジェクトがメモリ最適化されているか確認します。|**ExecIsWithNativeCompilation**プロパティと**Tableismemoryoptimized**プロパティ。<br /><br /> **Isschemabound**プロパティは、プロシージャオブジェクト型をサポートしています (NULL ではなくプロシージャの場合は0を返します)。|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|サーバーがインメモリ OLTP をサポートしているか確認します。|**サポートされている**プロパティです。|  
  
### <a name="system-stored-procedures"></a>システム ストアド プロシージャ  
  
|ストアド プロシージャ|説明|  
|----------------------|-----------------|  
|[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)|インメモリ OLTP データベースをリソース プールにバインドします。|  
|[sp_xtp_checkpoint_force_garbage_collection &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-checkpoint-force-garbage-collection-transact-sql)|インメモリ OLTP データベースのガベージ コレクションを開始します。|  
|[sp_xtp_control_proc_exec_stats &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql)|ネイティブコンパイルストアドプロシージャの統計コレクションを有効にします。|  
|[sp_xtp_control_query_exec_stats &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql)|ネイティブコンパイルストアドプロシージャのクエリ統計コレクションごとに有効にします。|  
|[sp_xtp_merge_checkpoint_files &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)|データファイルとデルタファイルをマージします。|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)|データベースとリソース プールの間のバインドを削除します。|  
  
## <a name="dynamic-management-views-dmvs"></a>動的管理ビュー (DMV)  
 メモリ最適化テーブルにはいくつかの DMV があります。  
  
 詳細については、「 [transact-sql&#41;&#40;メモリ最適化テーブルの動的管理ビュー ](/sql/relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql)」を参照してください。  
  
## <a name="wait-types"></a>待機の種類  
 インメモリ OLTP をサポートする待機の種類がいくつかあります。  
  
 詳細については、「 **WAIT_XTP**のプレフィックスが付いている待機の種類」および「 [dm_os_wait_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql) **トピックの「** 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Transact-SQL によるインメモリ OLTP のサポート](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
