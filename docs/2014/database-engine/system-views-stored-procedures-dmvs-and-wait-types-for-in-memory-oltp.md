---
title: システム ビュー、ストアド プロシージャ、Dmv の待機の種類、インメモリ OLTP の |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: a4e50744a716e42e0fd2767ec9cc677b2ccc085f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176007"
---
# <a name="system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp"></a>システム ビュー、ストアド プロシージャ、Dmv およびインメモリ OLTP での待機の種類
  このトピックでは、簡単な説明を行い、インメモリ OLTP をサポートする多くのデータベース オブジェクトへのリンクを提供します。  
  
### <a name="system-views"></a>システム ビュー  
  
|システム ビュー|説明|インメモリ OLTP 機能|  
|-----------------|-----------------|-----------------------------|  
|[sys.data_spaces &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-data-spaces-transact-sql)|ファイル グループにメモリ最適化データが含まれているかどうか確認します。|次の列が追加の値を表示:**型**と**type_desc**です。|  
|[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)|メモリ最適化テーブルにインデックスが付けられているか確認します。|次の列が追加の値を表示:**型**と**type_desc**です。|  
|[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql)|Not null 許容の (ネイティブ コンパイル ストアド プロシージャのより効率的に実行) のパラメーターを確認します。|**によって is_nullable**列です。|  
|[sys.all_sql_modules &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql)|ストアド プロシージャをネイティブでコンパイルかどうかを確認してください。|**uses_native_compilation**列です。|  
|[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)|ストアド プロシージャをネイティブでコンパイルかどうかを確認してください。|**uses_native_compilation**列です。|  
|[sys.table_types &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-table-types-transact-sql)|テーブルがメモリ最適化されているか確認します。|**is_memory_optimized**列です。|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|テーブルがメモリ最適化されているか確認し、さらにテーブルの持続性の設定を確認します。|**持続性**、 **durability_desc**、および**is_memory_optimized**列です。|  
|[sys.hash_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-hash-indexes-transact-sql)|メモリ最適化テーブルのハッシュ インデックスを表示します。|インメモリ OLTP 固有|  
  
### <a name="metadata-functions"></a>メタデータ関数  
  
|メタデータ関数|説明|インメモリ OLTP 機能|  
|-----------------------|-----------------|-----------------------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|データベース オブジェクトがメモリ最適化されているか確認します。|**ExecIsWithNativeCompilation**と**TableIsMemoryOptimized**プロパティです。<br /><br /> **IsSchemaBound**プロパティ (NULL の代わりにプロシージャの場合は 0 を返します) プロシージャ オブジェクトの種類をサポートしています。|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|サーバーがインメモリ OLTP をサポートしているか確認します。|**IsXTPSupported**プロパティです。|  
  
### <a name="system-stored-procedures"></a>システム ストアド プロシージャ  
  
|ストアド プロシージャ|説明|  
|----------------------|-----------------|  
|[sys.sp_xtp_bind_db_resource_pool &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)|インメモリ OLTP データベースをリソース プールにバインドします。|  
|[sys.sp_xtp_checkpoint_force_garbage_collection &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-checkpoint-force-garbage-collection-transact-sql)|インメモリ OLTP データベースのガベージ コレクションを開始します。|  
|[sys.sp_xtp_control_proc_exec_stats &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql)|ネイティブ コンパイル ストアド プロシージャの統計コレクションを有効にします。|  
|[sys.sp_xtp_control_query_exec_stats &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql)|ネイティブ コンパイル ストアド プロシージャのクエリ統計コレクションごとの有効化します。|  
|[sys.sp_xtp_merge_checkpoint_files &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)|データ ファイルとデルタ ファイルをマージします。|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)|データベースとリソース プールの間のバインドを削除します。|  
  
## <a name="dynamic-management-views-dmvs"></a>動的管理ビュー (DMV)  
 メモリ最適化テーブルにはいくつかの DMV があります。  
  
 詳細については、「[メモリ最適化テーブルの動的管理ビュー &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql)です。  
  
## <a name="wait-types"></a>待機の種類  
 インメモリ OLTP をサポートする待機の種類がいくつかあります。  
  
 詳細については、次を参照してください。 待機の種類が付いている**WAIT_XTP**、および**XTPPROC**で、 [sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)トピックです。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Transact-SQL によるインメモリ OLTP のサポート](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
