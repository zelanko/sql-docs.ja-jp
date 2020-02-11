---
title: pdw_nodes_tables (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 5fa2412e61e30852497ffa00493ea6dbe244989a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001114"
---
# <a name="syspdw_nodes_tables-transact-sql"></a>pdw_nodes_tables (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  プリンシパルが所有しているか、プリンシパルが権限を許可されている、テーブルオブジェクトごとに1行の値を格納します。  
  
|列名|データ型|[説明]|Range|  
|-----------------|---------------|-----------------|-----------|  
|\<継承された列>||このビューが継承する列の一覧については、「 [sys. オブジェクト](../system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)」を参照してください。||  
|lob_data_space_id|**int**||常に 0 です。|  
|filestream_data_space_id|**int**|FILESTREAM ファイルグループのデータ領域 ID または[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|このテーブルで使用される列の最大 ID。||  
|lock_on_bulk_load|**bit**|テーブルは一括読み込みでロックされています。|TBD|  
|uses_ansi_nulls|**bit**|テーブルは、SET ANSI_NULLS データベース オプションが ON の場合に作成されます。|1 で保護されたプロセスとして起動されました|  
|is_replicated|**bit**|1 = テーブルはレプリケーションを使用してパブリッシュされます。|0レプリケーションはサポートされていません。|  
|has_replication_filter|**bit**|1 = テーブルにはレプリケーションフィルターがあります。|0|  
|is_merge_published|**bit**|1 = テーブルは、マージ レプリケーションを使用してパブリッシュされます。|0サポートされていません。|  
|is_sync_tran_subscribed|**bit**|1 = テーブルは即時更新サブスクリプションを使用してサブスクライブされます。|0サポートされていません。|  
|has_unchecked_assembly_data|**bit**|1 = テーブルには、最後の ALTER ASSEMBLY 中に定義が変更されたアセンブリに依存する永続化されたデータが含まれています。 次の DBCC CHECKDB または DBCC CHECKTABLE が正常に完了した後、は0にリセットされます。|0CLR のサポートはありません。|  
|text_in_row_limit|**int**|0 = Text in row オプションは設定されていません。|常に 0 です。|  
|large_value_types_out_of_row|**bit**|1 = 大きな値の型は、行外に格納されます。|常に 0 です。|  
|is_tracked_by_cdc|**bit**|1 = テーブルで変更データキャプチャが有効になっている|常に0です。CDC サポートはありません。|  
|lock_escalation|**tinyint**|テーブルの LOCK_ESCALATION オプションの値: 2 = AUTO|常に2。|  
|lock_escalation_desc|**nvarchar (60)**|Lock_escalation オプションの説明テキスト。|常にꞌ AUTO ꞌです。|  
|pdw_node_id|**int**|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノードの一意識別子。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスのカタログビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
