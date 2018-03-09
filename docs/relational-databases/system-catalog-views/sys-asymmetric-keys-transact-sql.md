---
title: "sys.asymmetric_keys (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- asymmetric_keys
- sys.asymmetric_keys_TSQL
- asymmetric_keys_TSQL
- sys.asymmetric_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.asymmetric_keys catalog view
ms.assetid: bbca796a-9bb5-4a62-9ca8-1d255984553d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c42b7a6bcc17fff443fbbafd960baba6bc359ef
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysasymmetrickeys-transact-sql"></a>sys.asymmetric_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  非対称キーごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|キーの名前。 データベース内で一意です。|  
|**principal_id**|**int**|キーを所有するデータベース プリンシパルの ID。|  
|**asymmetric_key_id**|**int**|キーの ID。 データベース内で一意です。|  
|**pvt_key_encryption_type**|**char(2)**|キーの暗号化方法。<br /><br /> NA = 暗号化されていません。<br /><br /> MK = キーはマスター キーにより暗号化されています。<br /><br /> PW = キーはユーザー定義パスワードにより暗号化されています。<br /><br /> SK = キーはサービス マスター キーにより暗号化されています。|  
|**pvt_key_encryption_type_desc**|**nvarchar (60)**|秘密キーの暗号化方法の説明。<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**拇印**|**varbinary (32)**|キーの SHA-1 ハッシュ。 ハッシュはグローバルに一意です。|  
|**アルゴリズム**|**char(2)**|キーと一緒に使用されるアルゴリズム。<br /><br /> 1R = 512 ビット RSA<br /><br /> 2R = 1024 ビット RSA<br /><br /> 3R = 2048 ビット RSA|  
|**algorithm_desc**|**nvarchar (60)**|キーと一緒に使用されるアルゴリズムの説明。<br /><br /> RSA_512<br /><br /> RSA_1024<br /><br /> RSA_2048|  
|**◆ セグ**|**int**|キーのビット長。|  
|**sid**|**varbinary (85)**|キーに対するログイン SID。 拡張キー管理キーの場合、この値は NULL になります。|  
|**string_sid**|**nvarchar (128)**|キーのログイン SID の文字列形式。 拡張キー管理キーの場合、この値は NULL になります。|  
|**public_key**|**varbinary(max)**|公開キー。|  
|**attested_by**|**nvarchar (260)**|システム使用のみ。|  
|**provider_type**|**nvarchar(120)**|暗号化サービス プロバイダーの種類。<br /><br /> CRYPTOGRAPHIC PROVIDER = 拡張キー管理キー<br /><br /> NULL = 拡張キー管理以外のキー|  
|**cryptographic_provider_guid**|**uniqueidentifier**|暗号化サービス プロバイダーの GUID。 拡張キー管理以外のキーの場合、この値は NULL になります。|  
|**cryptographic_provider_algid**|**sql_variant**|暗号化サービス プロバイダーのアルゴリズム ID。 拡張キー管理以外のキーの場合、この値は NULL になります。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
  
  
