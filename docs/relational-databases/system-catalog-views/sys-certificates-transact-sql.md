---
title: sys.certificates (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6adf267137533d7436349de5a42e8552072216bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942566"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース内の各証明書の行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|証明書の名前です。 データベース内で一意です。|  
|**certificate_id**|**int**|証明書の ID。 データベース内で一意です。|  
|**principal_id**|**int**|この証明書を所有するデータベース プリンシパルの ID。|  
|**pvt_key_encryption_type**|**char(2)**|秘密キーの暗号化方法。<br /><br /> NA = 証明書に秘密キーはありません。<br /><br /> MK = 秘密キーはマスター _ キーによって暗号化<br /><br /> PW = 秘密キーはユーザー定義パスワードにより暗号化<br /><br /> SK = 秘密キーはサービス マスター_キーによって暗号化されます。|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|秘密キーを暗号化する方法の説明です。<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|1 の場合、この証明書を使用してを暗号化されたサービスでダイアログを開始します。|  
|**issuer_name**|**nvarchar(442)**|証明書の発行者の名前です。|  
|**cert_serial_number**|**nvarchar(64)**|証明書のシリアル番号。|  
|**sid**|**varbinary(85)**|この証明書に対するログイン SID。|  
|**string_sid**|**nvarchar(128)**|この証明書に対するログイン SID の文字列表現|  
|**subject**|**nvarchar (4000)**|証明書のサブジェクト。|  
|**expiry_date**|**datetime**|証明書が期限切れにします。|  
|**start_date**|**datetime**|ときに証明書が無効です。|  
|**拇印**|**varbinary(32)**|証明書の SHA-1 ハッシュ。 Sha-1 ハッシュはグローバルに一意です。|  
|**attested_by**|**nvarchar(260)**|システムでのみ使用します。|  
|pvt_key_last_backup_date|**datetime**|日付と時刻の証明書の秘密キーが前回エクスポートされました。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
