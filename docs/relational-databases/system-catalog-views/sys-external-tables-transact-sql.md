---
title: sys.external_tables (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 58c86f9eed16b83d9cc63c54f907f50dda1aab4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702720"
---
# <a name="sysexternaltables-transact-sql"></a>sys.external_tables (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  現在のデータベース内の各外部テーブルの行が含まれています。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|\<列を継承 >||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)します。||  
|max_column_id_used|**int**|列の最大の ID がこのテーブルを使用することです。||  
|uses_ansi_nulls|**bit**|テーブルは、SET ANSI_NULLS データベース オプションが ON の場合に作成されます。||  
|data_source_id|**int**|外部データ ソースのオブジェクト ID。||  
|file_format_id|**int**|HADOOP の外部データ ソース経由で外部テーブルの外部ファイル形式のオブジェクト ID です。||  
|location|**nvarchar (4000)**|HADOOP の外部データ ソース経由で外部テーブルは、これは、HDFS 内の外部データのパスです。||  
|reject_type|**tinyint**|HADOOP の外部データ ソース経由で外部テーブルは、これは、外部データを照会するときに、拒否された行はカウント方法です。|VALUE – 拒否された行の数。<br /><br /> PERCENTAGE – 拒否された行の割合。|  
|reject_value|**float**|HADOOP の外部データ ソース経由で外部テーブルは。<br /><br /> *Reject_type =* valueで、これは、クエリが失敗するまでに許可する行の拒否された回数。<br /><br /> *Reject_type* = percentage、これは、クエリが失敗するまでに許可する行の却下のパーセンテージです。||  
|reject_sample_value|**int**|*Reject_type* = percentage、これは、読み込むには、成功と失敗、拒否された行の比率を計算する前に行の数。|reject_type = value の場合は NULL です。|  
|distribution_type|**int**|SHARD_MAP_MANAGER の外部データ ソース経由で外部テーブルの基になるベース テーブルの間で、行のデータ分布になります。|0 – Sharded<br /><br /> 1 – レプリケート<br /><br /> 2 – ラウンド ロビン|  
|distribution_desc|**nvarchar(120)**|SHARD_MAP_MANAGER の外部データ ソース経由で外部テーブルは、これは、分布の種類を文字列として表示されます。||  
|sharding_column_id|**int**|SHARD_MAP_MANAGER の外部データ ソースと sharded ディストリビューション経由で外部テーブルは、シャーディング キー値を含む列の列 ID です。||  
|remote_schema_name|**sysname**|SHARD_MAP_MANAGER の外部データ ソース経由で外部テーブルの場合、ベース テーブルの場所 (外部テーブルが定義されているスキーマと異なる) 場合は、リモート データベースでスキーマです。||  
|remote_object_name|**sysname**|SHARD_MAP_MANAGER の外部データ ソース経由で外部テーブルは、これは、(外部テーブルの名前と異なる) 場合は、リモート データベースでベース テーブルの名前です。||  
  
## <a name="permissions"></a>アクセス許可  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.external_file_formats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
