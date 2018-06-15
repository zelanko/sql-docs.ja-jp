---
title: sys.certificates (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- certificates
- certificates_TSQL
- sys.certificates_TSQL
- sys.certificates
dev_langs:
- TSQL
helpviewer_keywords:
- sys.certificates catalog view
ms.assetid: e5046102-a65c-401e-b80d-05636884dec9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f5aaf349d050b2b1b1d27ae3067f003186c8c6eb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180318"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース内の証明書ごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|証明書の名前。 データベース内で一意です。|  
|**certificate_id**|**int**|証明書の ID。 データベース内で一意です。|  
|**principal_id**|**int**|証明書を所有するデータベース プリンシパルの ID。|  
|**pvt_key_encryption_type**|**char(2)**|秘密キーの暗号化方法。<br /><br /> NA = 証明書に秘密キーはありません。<br /><br /> MK = 秘密キーはマスター キーにより暗号化されています。<br /><br /> PW = 秘密キーはユーザー定義パスワードにより暗号化されています。<br /><br /> SK = 秘密キーはサービス マスター キーにより暗号化されています。|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|秘密キーの暗号化方法の説明。<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|1 の場合、この証明書はサービス間で暗号化されたメッセージ交換を開始するために使用されます。|  
|**issuer_name**|**nvarchar(442)**|証明書の発行者の名前。|  
|**cert_serial_number**|**nvarchar(64)**|証明書のシリアル番号。|  
|**sid**|**varbinary(85)**|証明書に対するログイン SID。|  
|**string_sid**|**nvarchar(128)**|証明書に対するログイン SID の文字列形式。|  
|**subject**|**nvarchar (4000)**|証明書のサブジェクト。|  
|**expiry_date**|**datetime**|証明書が期限切れにします。|  
|**start_date**|**datetime**|証明書が有効になる日付。|  
|**拇印**|**varbinary(32)**|証明書の SHA-1 ハッシュ。 SHA-1 ハッシュはグローバルに一意です。|  
|**attested_by**|**nvarchar(260)**|システム使用のみ。|  
|pvt_key_last_backup_date|**datetime**|証明書の秘密キーが前回エクスポートされた日時。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
