---
title: sys.master_key_passwords (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a0aa45dc4ee0e54e7880837e289b2331b5ff11e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017722"
---
# <a name="sysmasterkeypasswords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各データベースのマスター _ キーのパスワードを使用して追加の行を返します、 **sp_control_dbmasterkey_password**ストアド プロシージャ。 マスター キーの保護に使用されるパスワードは、資格情報ストアに格納されています。 資格情報名は、##DBMKEY_<database_family_guid>_<random_password_guid>## の形式で表されます。 パスワードは、資格情報シークレットとして格納されています。 使用して追加された各パスワード**sp_control_dbmasterkey_password**、内の行がある**sys.credentials**します。  
  
 このビューの各行を示しています、 **credential_id**と**family_guid**のうち、マスター _ キーがその資格情報に関連付けられているパスワードで保護されたデータベース。 参加**sys.credentials**上、 **credential_id**など有用なフィールドを返す、 **create_date**と資格情報の名前。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|パスワードが属する資格情報の ID。 この ID はサーバー インスタンス内で一意です。|  
|**family_guid**|**uniqueidentifier**|作成時の元のデータベースの一意 ID。 この GUID は、データベースが復元または添付されたり、データベース名が変更されたりしても変わりません。<br /><br /> サービス マスター_キーによる自動暗号化解除が失敗した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、 **family_guid**データベース マスター _ キーを保護するために使用するパスワードを含む可能性のある資格情報を識別するためにします。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
