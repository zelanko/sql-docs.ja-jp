---
title: data_spaces (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab7be8ba4aba0241b45800b77e28b44e168ab182
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823419"
---
# <a name="sysdata_spaces-transact-sql"></a>data_spaces (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  データ領域ごとに 1 行のデータがあります。 データ領域はファイル グループ、パーティション構成、または FILESTREAM データ ファイル グループです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|name|**sysname**|データ領域の名前。データベース内で一意です。|  
|data_space_id|**int**|データ領域 ID 番号。データベース内で一意です。|  
|型|**char(2)**|データ領域の種類:<br /><br /> FG = ファイル グループ<br /><br /> FD = FILESTREAM データ ファイル グループ<br /><br /> FX = メモリ最適化テーブルファイルグループ<br /><br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降。<br /><br /> PS = パーティション構成|  
|type_desc|**nvarchar(60)**|データ領域の種類の説明:<br /><br /> FILESTREAM_DATA_FILEGROUP<br /><br /> MEMORY_OPTIMIZED_DATA_FILEGROUP<br /><br /> **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降。<br /><br /> PARTITION_SCHEME<br /><br /> ROWS_FILEGROUP|  
|is_default|**bit**|1 = 既定のデータ領域です。 既定のデータ領域は、CREATE TABLE または CREATE INDEX ステートメントでファイル グループやパーティション構成が指定されない場合に使用されます。<br /><br /> 0 = 既定のデータ領域ではありません。|  
|is_system|**bit**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降。<br /><br /> 1 = データ領域は、フルテキストインデックスフラグメントに使用されます。<br /><br /> 0 = フルテキスト インデックス フラグメントに使用しないデータ領域。|  
  
## <a name="permissions"></a>アクセス許可  
 public ロールのメンバーシップが必要です。  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ領域 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)   
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [destination_data_spaces &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys. ファイルグループ &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [partition_schemes &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
