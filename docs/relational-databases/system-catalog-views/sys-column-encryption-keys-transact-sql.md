---
title: column_encryption_keys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_encryption_keys
- column_encryption_keys_TSQL
- sys.column_encryption_keys_TSQL
- column_encryption_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_keys catalog view
ms.assetid: 43980dd8-b9b1-4869-a304-2c183ae8977d
author: jaszymas
ms.author: jaszymas
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4cd6b4a4cb8eeed0dd0a2a78adc2d39c6a2e895d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73593728"
---
# <a name="syscolumn_encryption_keys--transact-sql"></a>column_encryption_keys (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-xxx-md.md)]

  [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md)ステートメントで作成された列暗号化キー (ceks) に関する情報を返します。 各行は CEK を表します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|CMK の名前。|  
|**column_encryption_key_id**|**int**|CEK の ID。|  
|**create_date**|**DATETIME**|CEK が作成された日付。|  
|**modify_date**|**DATETIME**|CEK が最後に変更された日付。|  
  
## <a name="permissions"></a>アクセス許可  
 **VIEW ANY COLUMN ENCRYPTION KEY**権限が必要です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の列暗号化キーの作成](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [Transact-sql&#41;&#40;列暗号化キーの変更](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [Transact-sql&#41;&#40;列暗号化キーを削除します。](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-sql&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [column_encryption_key_values &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Secure enclaves での Always Encrypted](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Always Encrypted のキー管理の概要](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [セキュリティで保護されたエンクレーブが設定された Always Encrypted のキーを管理する](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)    

  
  
