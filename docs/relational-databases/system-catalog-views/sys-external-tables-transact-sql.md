---
title: "sys.external_tables (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c261068e68503ff01429c3b215261dffcb48053
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysexternaltables-transact-sql"></a>sys.external_tables (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  現在のデータベース内の各外部テーブルの行が含まれています。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|\<継承された列 >||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。||  
|max_column_id_used|**int**|列の最大の ID がこのテーブルを使用することです。||  
|uses_ansi_nulls|**bit**|テーブルは、SET ANSI_NULLS データベース オプションが ON の場合に作成されます。||  
|data_source_id|**int**|外部データ ソースのオブジェクト ID。||  
|file_format_id|**int**|HADOOP の外部データ ソース経由で外部テーブルは、これは、外部ファイル形式のオブジェクトの ID です。||  
|location|**nvarchar (4000)**|HADOOP の外部データ ソース経由で外部テーブルは、これは、HDFS の外部データのパスです。||  
|reject_type|**tinyint**|HADOOP の外部データ ソース経由で外部テーブルは、これは、外部データを照会するときに、拒否された行はカウント方法です。|値 – 拒否された行の数。<br /><br /> パーセント – 拒否された行の割合。|  
|reject_value|**float**|HADOOP の外部データ ソース経由で外部テーブルの。<br /><br /> *Reject_type =*値で、これは、クエリが失敗するまでに許可する行の拒否された回数。<br /><br /> *Reject_type* = 割合、これは、クエリが失敗するまでに許可する行の却下のパーセンテージです。||  
|reject_sample_value|**int**|*Reject_type* = 割合、これは、読み込むには、成功と失敗、拒否された行の比率を計算する前に行の数。|NULL if reject_type = VALUE.|  
|distribution_type|**int**|SHARD_MAP_MANAGER 外部データ ソース経由で外部テーブルは、これは、行のデータの分布、基になるベース テーブルの間でです。|0 – Sharded<br /><br /> 1 – レプリケート<br /><br /> 2 – ラウンド ロビン|  
|distribution_desc|**nvarchar(120)**|SHARD_MAP_MANAGER 外部データ ソース経由で外部テーブルの場合は、この配布種類を文字列として表示されます。||  
|sharding_column_id|**int**|SHARD_MAP_MANAGER 外部データ ソースと sharded ディストリビューション経由で外部テーブルは、これは、シャーディング キー値を含んでいる列の列の ID です。||  
|remote_schema_name|**sysname**|SHARD_MAP_MANAGER 外部データ ソース経由で外部テーブルの場合 (外部のテーブルが定義されているスキーマとは異なる) 場合は、リモート データベースでベース テーブルの場所のスキーマです。||  
|remote_object_name|**sysname**|SHARD_MAP_MANAGER 外部データ ソース経由で外部テーブルは、これは (外部テーブルの名前と異なる) 場合は、リモート データベースでベース テーブルの名前です。||  
  
## <a name="permissions"></a>権限  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.external_file_formats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
