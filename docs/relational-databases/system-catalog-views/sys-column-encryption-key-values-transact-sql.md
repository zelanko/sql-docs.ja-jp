---
title: sys.column_encryption_key_values (Transact SQL) |マイクロソフトのドキュメント
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: e89df0a5d451ce280bb884e49f29c189f89d6e1a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561552"
---
# <a name="syscolumnencryptionkeyvalues-transact-sql"></a>sys.column_encryption_key_values (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  暗号化キー (CEKs) のいずれかの方法で作成された列の暗号化された値についての情報を取得、[列の暗号化キーの作成](../../t-sql/statements/create-column-encryption-key-transact-sql.md)または[列の暗号化キーの変更&#40;Transact SQL&#41; ](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)ステートメントです。 各行は、マスター_キーで暗号化された、列 (CMK)、CEK の値を表します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_id**|**int**|データベースに CEK の ID です。|  
|**column_master_key_id**|**int**|CEK 値の暗号化に使用された列のマスター_キーの ID です。|  
|**encrypted_value**|**varbinary(8000)**|CEK コンテンツ column_master_key_id で指定された CMK で暗号化された値です。|  
|**encryption_algorithm_name**|**sysname**|CEK 値の暗号化に使用するアルゴリズムの名前です。<br /><br /> 値を暗号化するために使用する暗号化アルゴリズムの名前です。 システム プロバイダー用のアルゴリズムである必要があります**RSA_OAEP**。|  
  
## <a name="permissions"></a>アクセス許可  
 必要です、**ビューの列の暗号化キー**のアクセス許可。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
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
  
  
