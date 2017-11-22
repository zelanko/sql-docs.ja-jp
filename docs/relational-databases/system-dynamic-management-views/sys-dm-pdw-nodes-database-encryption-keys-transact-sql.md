---
title: "sys.dm_pdw_nodes_database_encryption_keys (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: e7fd02b2-5d7e-4816-a0af-b58ae2ac3f7a
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1fdfeeccb7bbf0ffae44566b46e589c3f90e9c75
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwnodesdatabaseencryptionkeys-transact-sql"></a>sys.dm_pdw_nodes_database_encryption_keys (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  データベースの暗号化の状態およびデータベースに関連付けられているデータベース暗号化キーに関する情報を返します。 **sys.dm_pdw_nodes_database_encryption_keys**ノードごとにこの情報を提供します。 データベース暗号化の詳細については、次を参照してください。[透過的なデータ暗号化 (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d)です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|各ノード上の物理データベースの ID です。|  
|encryption_state|**int**|このノード上のデータベースが暗号化または暗号化されていないかどうかを示します。<br /><br /> 0 = データベース暗号化キーがなく暗号化されていない<br /><br /> 1 = 暗号化されていない<br /><br /> 2 = 暗号化中<br /><br /> 3 = 暗号化<br /><br /> 4 = キーの変更中<br /><br /> 5 = 暗号化解除中<br /><br /> 6 = 保護の変更中 (データベース暗号化キーを暗号化するための証明書変更されています)。|  
|create_date|**datetime**|暗号化キーが作成された日付を表示します。|  
|regenerate_date|**datetime**|暗号化キーが再生成された日付を表示します。|  
|modify_date|**datetime**|暗号化キーが変更された日付を表示します。|  
|set_date|**datetime**|暗号化キーがデータベースに適用された日付を表示します。|  
|opened_date|**datetime**|データベース キーが最後に開かれた日時を表示します。|  
|key_algorithm|**varchar(?)**|キーで使用されるアルゴリズムを表示します。|  
|key_length|**int**|キーの長さを表示します。|  
|encryptor_thumbprint|**varbin**|暗号化のサムプリントを表示します。|  
|percent_complete|**real**|データベース暗号化の状態変更の完了率です。 状態変更がない場合は 0 になります。|  
|node_id|**int**|ノードに関連付けられている一意の数値 id です。|  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例の結合`sys.dm_pdw_nodes_database_encryption_keys`TDE の各ノードで保護されたデータベースの暗号化の状態を示すには、他のシステム テーブル。  
  
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
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [データベース暗号化キー &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  

