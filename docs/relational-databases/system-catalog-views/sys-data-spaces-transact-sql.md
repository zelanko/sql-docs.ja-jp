---
title: sys.data_spaces (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- data_spaces
- sys.data_spaces_TSQL
- sys.data_spaces
- data_spaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.data_spaces catalog view
ms.assetid: f39d55fe-2c0f-472d-a77f-cebc6fea95b5
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2107523229f30909d6c7e2584a3fcb1627419675
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdataspaces-transact-sql"></a>sys.data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  データ領域ごとに 1 行のデータがあります。 データ領域はファイル グループ、パーティション構成、または FILESTREAM データ ファイル グループです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|データ領域の名前。データベース内で一意です。|  
|data_space_id|**int**|データ領域の ID 番号。データベース内で一意です。|  
|型|**char(2)**|データ領域の種類。<br /><br /> FG = ファイル グループ<br /><br /> FD = FILESTREAM データ ファイル グループ<br /><br /> FX = メモリ最適化テーブルのファイル グループ<br /><br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> PS = パーティション構成|  
|type_desc|**nvarchar(60)**|データ領域の種類の説明。<br /><br /> FILESTREAM_DATA_FILEGROUP<br /><br /> MEMORY_OPTIMIZED_DATA_FILEGROUP<br /><br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> PARTITION_SCHEME<br /><br /> ROWS_FILEGROUP|  
|is_default|**bit**|1 = 既定のデータ領域。 既定のデータ領域は、CREATE TABLE または CREATE INDEX ステートメントでファイル グループやパーティション構成が指定されない場合に使用されます。<br /><br /> 0 = 既定のデータ領域ではない。|  
|is_system|**bit**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = フルテキスト インデックス フラグメントに使用するデータ領域。<br /><br /> 0 = フルテキスト インデックス フラグメントに使用しないデータ領域。|  
  
## <a name="permissions"></a>権限  
 public ロールのメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ領域&#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.destination_data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
