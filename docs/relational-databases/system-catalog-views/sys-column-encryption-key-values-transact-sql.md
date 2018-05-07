---
title: sys.column_encryption_key_values (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_encryption_key_values
- column_encryption_key_values_TSQL
- sys.column_encryption_key_values
- sys.column_encryption_key_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_key_values catalog view
ms.assetid: 440875ab-b0e9-4966-8c16-01503558fedd
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 02d0ce79355422943b21608d546890ebd1bc61e0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syscolumnencryptionkeyvalues-transact-sql"></a>sys.column_encryption_key_values (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  暗号化キー (CEKs) のいずれかで作成された列の暗号化された値に関する情報を返します、 [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md)または[ALTER COLUMN ENCRYPTION KEY &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)ステートメントです。 各行は、マスター_キーで暗号化された、列 (CMK)、CEK の値を表します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_id**|**int**|データベースに CEK の ID です。|  
|**column_master_key_id**|**int**|CEK 値の暗号化に使用された列のマスター_キーの ID です。|  
|**encrypted_value**|**varbinary(8000)**|CEK コンテンツ column_master_key_id で指定された CMK で暗号化された値です。|  
|**encryption_algorithm_name**|**sysname**|CEK 値の暗号化に使用するアルゴリズムの名前です。<br /><br /> 値を暗号化するために使用する暗号化アルゴリズムの名前です。 システム プロバイダーのアルゴリズムである必要があります**RSA_OAEP**です。|  
  
## <a name="permissions"></a>権限  
 必要があります、 **VIEW ANY COLUMN ENCRYPTION KEY**権限です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
  
