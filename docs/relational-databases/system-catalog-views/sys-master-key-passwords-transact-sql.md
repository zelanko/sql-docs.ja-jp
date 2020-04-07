---
title: master_key_passwords (トランザクション-SQL) |マイクロソフトドキュメント
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
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752898"
---
# <a name="sysmaster_key_passwords-transact-sql"></a>master_key_passwords (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  **sp_control_dbmasterkey_password**ストアド プロシージャを使用して追加されたデータベース マスター キー パスワードごとに、行を返します。 マスターキーを保護するために使用されるパスワードは、資格情報ストアに格納されます。 資格情報名は次の形式に従います: ##DBMKEY_<database_family_guid>#random_password_guid<>_>_<。 パスワードは資格情報の秘密として保存されます。 **sp_control_dbmasterkey_password**を使用して追加された各パスワードに対して、 **sys.credentials**に行があります。  
  
 このビューの各行には **、その**資格情報に関連付けられたパスワードによって保護されているマスターキーのcredential_idと**データベースのfamily_guid**が表示されます。 **credential_id**で**sys.credentials**を使用して結合すると **、create_date**や資格情報名などの有用なフィールドが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|パスワードが属する資格情報の ID。 この ID はサーバー インスタンス内で一意です。|  
|**family_guid**|**Uniqueidentifier**|作成時の元のデータベースの一意の ID。 この GUID は、データベースが復元または添付されたり、データベース名が変更されたりしても変わりません。<br /><br /> サービス マスター キーによる自動復号化が失敗した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は **、family_guid**を使用して、データベース マスター キーを保護するために使用されるパスワードを含む資格情報を特定します。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;トランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [セキュリティ カタログ ビュー&#40;トランザクション SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [対称キー&#40;Transact-SQL&#41;を作成する](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
