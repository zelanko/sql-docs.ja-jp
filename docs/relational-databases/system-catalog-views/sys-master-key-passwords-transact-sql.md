---
title: "sys.master_key_passwords (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.master_key_passwords_TSQL
- master_key_passwords_TSQL
- sys.master_key_passwords
- master_key_passwords
dev_langs:
- TSQL
helpviewer_keywords:
- sys.master_key_passwords catalog view
ms.assetid: b8e18cff-a9e6-4386-98ce-1cd855506e03
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6bb1977fb034f2fd2c682b12b4466bd7914009dd
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysmasterkeypasswords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用して追加されたデータベースのマスター _ キーのパスワードごとに行を返します、 **sp_control_dbmasterkey_password**ストアド プロシージャです。 マスター キーの保護に使用されるパスワードは、資格情報ストアに格納されています。 資格情報名は、##DBMKEY_<database_family_guid>_<random_password_guid>## の形式で表されます。 パスワードは、資格情報シークレットとして格納されています。 使用して追加されたパスワードごと**sp_control_dbmasterkey_password**、内の行がある**sys.credentials**です。  
  
 このビューの各行を示しています、 **credential_id**と**family_guid**これのマスター _ キーがその資格情報に関連付けられているパスワードで保護されたデータベースのです。 参加**sys.credentials**上、 **credential_id**など有用なフィールドを返す、 **create_date**と資格情報の名前。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|パスワードが属する資格情報の ID。 この ID はサーバー インスタンス内で一意です。|  
|**family_guid**|**uniqueidentifier**|作成時の元のデータベースの一意 ID。 この GUID は、データベースが復元または添付されたり、データベース名が変更されたりしても変わりません。<br /><br /> サービス マスター _ キーによる自動暗号化解除が失敗した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、 **family_guid**をデータベース マスター _ キーを保護するためのパスワードを含む可能性のある資格情報を識別します。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
