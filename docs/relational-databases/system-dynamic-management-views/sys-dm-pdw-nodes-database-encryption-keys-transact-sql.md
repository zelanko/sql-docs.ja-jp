---
title: sys.dm_pdw_nodes_database_encryption_keys (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e7fd02b2-5d7e-4816-a0af-b58ae2ac3f7a
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 34de2634c0aa1dd6a0b55ef281dba4c7d8579afd
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58657068"
---
# <a name="sysdmpdwnodesdatabaseencryptionkeys-transact-sql"></a>sys.dm_pdw_nodes_database_encryption_keys (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  暗号化キー、データベースとその関連付けられているデータベースの暗号化の状態に関する情報を返します。 **sys.dm_pdw_nodes_database_encryption_keys** provides this information for each node. データベース暗号化の詳細については、[Transparent Data Encryption (SQL Server PDW)](../../analytics-platform-system/transparent-data-encryption.md)を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**int**|各ノード上の物理データベースの ID。|  
|encryption_state|**int**|このノード上のデータベースが暗号化および暗号化されていないかどうかを示します。<br /><br /> 0 = データベース暗号化キーが存在する、暗号化なし<br /><br /> 1 = Unencrypted<br /><br /> 2 = 暗号化中<br /><br /> 3 = 暗号化<br /><br /> 4 = キーの変更中<br /><br /> 5 = 暗号化解除中<br /><br /> 6 = 保護の変更中 (データベース暗号化キーを暗号化する証明書変更されています)。|  
|create_date|**datetime**|暗号化キーが作成された日付を表示します。|  
|regenerate_date|**datetime**|暗号化キーが再生成された日付を表示します。|  
|modify_date|**datetime**|暗号化キーが変更された日付を表示します。|  
|set_date|**datetime**|暗号化キーがデータベースに適用された日付を表示します。|  
|opened_date|**datetime**|データベース キーが最後に開かれた日時を示します。|  
|key_algorithm|**varchar(?)**|キーに使用されるアルゴリズムを表示します。|  
|◆ セグ|**int**|キーの長さを表示します。|  
|encryptor_thumbprint|**varbin**|暗号化のサムプリントを表示します。|  
|percent_complete|**real**|データベース暗号化の状態変更の完了率。 状態の変更がない場合は、0 になります。|  
|node_id|**int**|ノードに関連付けられている一意の数値 id。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例の結合`sys.dm_pdw_nodes_database_encryption_keys`を TDE の各ノードで保護されたデータベースの暗号化の状態を示すために他のシステム テーブル。  
  
```  
SELECT D.database_id AS DBIDinMaster, D.name AS UserDatabaseName,   
PD.pdw_node_id AS NodeID, DM.physical_name AS PhysDBName,   
keys.encryption_state  
FROM sys.dm_pdw_nodes_database_encryption_keys AS keys  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON keys.database_id = PD.database_id AND keys.pdw_node_id = PD.pdw_node_id  
JOIN sys.pdw_database_mappings AS DM  
    ON DM.physical_name = PD.physical_name  
JOIN sys.databases AS D  
    ON D.database_id = DM.database_id  
ORDER BY D.database_id, PD.pdw_node_ID;  
```  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  

