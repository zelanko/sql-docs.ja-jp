---
title: sys.dm_database_encryption_keys (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: af4506e46dbe910b96d0141afd09eb5815e341aa
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544302"
---
# <a name="sysdmdatabaseencryptionkeys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベースの暗号化の状態およびデータベースに関連付けられているデータベース暗号化キーに関する情報を返します。 データベース暗号化の詳細については、「[Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**int**|データベースの ID です。|  
|encryption_state|**int**|データベースが暗号化されているかどうかを示します。<br /><br /> 0 = データベース暗号化キーがなく暗号化されていない<br /><br /> 1 = 暗号化されていない<br /><br /> 2 = 暗号化中<br /><br /> 3 = 暗号化<br /><br /> 4 = キーの変更中<br /><br /> 5 = 暗号化解除中<br /><br /> 6 = 保護の変更中 (データベース暗号化キーを暗号化する証明書または非対称キーの変更中)|  
|create_date|**datetime**|暗号化キーが作成された日付を表示します。|  
|regenerate_date|**datetime**|暗号化キーが再生成された日付を表示します。|  
|modify_date|**datetime**|暗号化キーが変更された日付を表示します。|  
|set_date|**datetime**|暗号化キーがデータベースに適用された日付を表示します。|  
|opened_date|**datetime**|データベース キーが最後に開かれた日時を表示します。|  
|key_algorithm|**nvarchar(32)**|キーで使用されるアルゴリズムを表示します。|  
|key_length|**int**|キーの長さを表示します。|  
|encryptor_thumbprint|**varbinary(20)**|暗号化のサムプリントを表示します。|  
|encryptor_type|**nvarchar(32)**|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。<br /><br /> 暗号化機能を説明します。|  
|percent_complete|**real**|データベース暗号化の状態変更の完了率です。 状態変更がない場合は 0 になります。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   

## <a name="see-also"></a>参照  

 [セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [透過的なデータ暗号化 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL Server の暗号化](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server とデータベースの暗号化キー &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
