---
title: master_key_passwords (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 926acd9beb00102e19dbc2844e282d74bc890915
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "80752898"
---
# <a name="sysmaster_key_passwords-transact-sql"></a>master_key_passwords (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  **Sp_control_dbmasterkey_password**ストアドプロシージャを使用して追加されたデータベースマスターキーのパスワードごとに1行のデータを返します。 マスターキーを保護するために使用されるパスワードは、資格情報ストアに格納されます。 資格情報名は、# #DBMKEY_<database_family_guid>_<random_password_guid # # の形式に従います。 パスワードは、資格情報のシークレットとして保存されます。 **Sp_control_dbmasterkey_password**を使用して追加されたパスワードごとに、 **sys. 資格情報**に行があります。  
  
 このビューの各行には、 **credential_id**と、その資格情報に関連付けられているパスワードによって保護されているデータベースの**family_guid**が表示されます。 **Credential_id**での**sys. 資格情報**の結合では、 **create_date**や資格情報名などの便利なフィールドが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|パスワードが属する資格情報の ID。 この ID はサーバー インスタンス内で一意です。|  
|**family_guid**|**uniqueidentifier**|作成時の元のデータベースの一意の ID。 この GUID は、データベースが復元または添付されたり、データベース名が変更されたりしても変わりません。<br /><br /> サービスマスターキーによる自動暗号化解除が失敗[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]した場合、は**family_guid**を使用して、データベースマスターキーの保護に使用されるパスワードを含む可能性のある資格情報を識別します。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-sql&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
