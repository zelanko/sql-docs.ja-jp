---
title: 資格情報 (トランザクション SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f87378897256f8b4fae26b30263577bedede6175
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752891"
---
# <a name="syscredentials-transact-sql"></a>クレデンシャル (トランザクション SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-asdw-pdw-md.md)]

  サーバー レベルの資格情報ごとに 1 行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|資格情報の ID。 サーバー内で一意です。|  
|name|**Sysname**|資格情報の名前。 サーバー内で一意です。|  
|credential_identity|**nvarchar(4000)**|使用する識別情報の名前。 これは通常、Windows ユーザーになります。 一意である必要はありません。|  
|create_date|**datetime**|資格情報が作成された日時。|  
|modify_date|**datetime**|資格情報が最後に変更された時刻。|  
|target_type|**nvarchar(100)**|資格情報の種類。 従来の資格情報では NULL を返し、暗号化プロバイダーにマップされた資格情報の暗号化プロバイダーを返します。 外部キー管理プロバイダの詳細については、「[拡張キー管理&#40;EKM&#41;」](../../relational-databases/security/encryption/extensible-key-management-ekm.md)を参照してください。|  
|target_id|**int**|資格情報がマップされているオブジェクトの ID。 従来の資格情報の場合は 0 を返し、暗号化プロバイダーにマップされた資格情報の場合は 0 以外を返します。 外部キー管理プロバイダの詳細については、「[拡張キー管理&#40;EKM&#41;」](../../relational-databases/security/encryption/extensible-key-management-ekm.md)を参照してください。|  

## <a name="remarks"></a>Remarks  
データベース レベルの資格情報については、 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)を参照してください。
  
## <a name="permissions"></a>アクセス許可  
 アクセス許可`VIEW ANY DEFINITION`または`ALTER ANY CREDENTIAL`アクセス許可が必要です。 また、プリンシパルはアクセス許可を拒否`VIEW ANY DEFINITION`できません。  
  
## <a name="see-also"></a>参照  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [データベース エンジン&#41;&#40;資格情報](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [セキュリティ カタログ ビュー&#40;トランザクション SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [プリンシパル&#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
