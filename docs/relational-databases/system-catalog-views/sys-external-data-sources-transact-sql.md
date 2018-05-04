---
title: sys.external_data_sources (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1016db6e-9950-4ae2-a004-bd4171e27359
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1380dcaa90a42f011b4029f4577b018b234f2795
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysexternaldatasources-transact-sql"></a>sys.external_data_sources (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  1 行の現在のデータベースの各外部データ ソースのデータを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、および[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。  
  
 各外部データ ソース用のサーバー上の行を格納[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|data_source_id|**int**|外部データ ソースのオブジェクト ID。||  
|name|**sysname**|外部データ ソースの名前です。||  
|location|**nvarchar (4000)**|接続文字列、プロトコル、IP アドレス、および外部データ ソース用のポートが含まれています。||  
|type_desc|**nvarchar (255)**|データ ソースの種類を文字列として表示されます。|HADOOP, RDBMS、SHARD_MAP_MANAGER、RemoteDataArchiveTypeExtDataSource|  
|型|**tinyint**|データ ソースの種類の数値として表示されます。|0: HADOOP<br /><br /> 1-RDBMS<br /><br /> 2-SHARD_MAP_MANAGER<br /><br /> 3-RemoteDataArchiveTypeExtDataSource|  
|resource_manager_location|**nvarchar (4000)**|HADOOP、IP とポートを入力、Hadoop リソース マネージャーの場所。 これは Hadoop のデータ ソース上のジョブを送信するために使用されます。<br /><br /> その他の種類の外部データ ソースの場合は NULL です。||  
|credential_id|**int**|データベースのオブジェクト ID には、外部データ ソースへの接続に使用される資格情報がスコープ設定されます。||  
|database_name|**sysname**|種類 RDBMS、リモート データベースの名前。 種類、SHARD_MAP_MANAGER、シャードのマップ manager データベースの名前。 その他の種類の外部データ ソースの場合は NULL です。||  
|shard_map_name|**sysname**|型 SHARD_MAP_MANAGER、シャードのマップの名前。 その他の種類の外部データ ソースの場合は NULL です。||  
  
## <a name="permissions"></a>権限  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.external_file_formats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_tables &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  
