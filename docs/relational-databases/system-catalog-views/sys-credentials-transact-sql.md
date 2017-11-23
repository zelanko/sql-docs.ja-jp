---
title: "sys.credentials (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs: TSQL
helpviewer_keywords: sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf03ffcc4dffb40aa53aff24d67e12487f3d069b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  サーバー レベルの資格情報ごとに 1 つの行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|資格情報の ID。 サーバーで一意です。|  
|name|**sysname**|資格情報の名前です。 サーバーで一意です。|  
|credential_identity|**nvarchar (4000)**|使用する識別情報の名前。 通常は Windows ユーザーです。 一意である必要はありません。|  
|create_date|**datetime**|資格情報が作成された日時。|  
|modify_date|**datetime**|資格情報が最後に変更された日時。|  
|target_type|**nvarchar (100)**|資格情報の種類。 従来の資格情報の場合は NULL を返し、暗号化サービス プロバイダーにマップされた資格情報の場合は CRYPTOGRAPHIC PROVIDER を返します。 外部キー管理プロバイダーの詳細については、次を参照してください。[拡張キー管理 &#40;です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|資格情報がマップされているオブジェクトの ID。 従来の資格情報の場合は 0 を返し、暗号化サービス プロバイダーにマップされた資格情報の場合は 0 以外を返します。 外部キー管理プロバイダーの詳細については、次を参照してください。[拡張キー管理 &#40;です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>解説  
データベース レベルの資格情報は、次を参照してください。 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)です。
  
## <a name="permissions"></a>Permissions  
 いずれかが必要`VIEW ANY DEFINITION`権限または`ALTER ANY CREDENTIAL`権限です。 さらに、プリンシパル拒否されていない`VIEW ANY DEFINITION`権限です。  
  
## <a name="see-also"></a>参照  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
