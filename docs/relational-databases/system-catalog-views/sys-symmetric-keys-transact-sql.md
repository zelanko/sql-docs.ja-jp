---
title: symmetric_keys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- symmetric_keys
- sys.symmetric_keys
- sys.symmetric_keys_TSQL
- symmetric_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.symmetric_keys catalog view
ms.assetid: d410eae1-3a52-45de-b9a1-52d2bd93a8eb
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5b4607c5873889c17e9934cc4f24465fe4e83007
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108929"
---
# <a name="syssymmetric_keys-transact-sql"></a>sys.symmetric_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  CREATE SYMMETRIC KEY ステートメントを使用して作成した対称キーごとに 1 行のデータを返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|キーの名前。 データベース内で一意です。|  
|**principal_id**|**int**|キーを所有するデータベースプリンシパルの ID。|  
|**symmetric_key_id**|**int**|キーの ID。 データベース内で一意です。|  
|**key_length**|**int**|キーの長さ (ビット単位)。|  
|**key_algorithm**|**char (2)**|キーで使用されるアルゴリズム。<br /><br /> R2 = RC2<br /><br /> R4 = RC4<br /><br /> D = DES<br /><br /> D3 = Triple DES<br /><br /> DT = TRIPLE_DES_3KEY<br /><br /> DX = DESX<br /><br /> A1 = AES 128<br /><br /> A2 = AES 192<br /><br /> A3 = AES 256<br /><br /> NA = EKM キー|  
|**algorithm_desc**|**nvarchar (60)**|キーで使用されるアルゴリズムの説明。<br /><br /> RC2<br /><br /> RC4<br /><br /> DES<br /><br /> Triple_DES<br /><br /> TRIPLE_DES_3KEY<br /><br /> DESX<br /><br /> AES_128<br /><br /> AES_192<br /><br /> AES_256<br /><br /> NULL (拡張キー管理アルゴリズムのみ)|  
|**create_date**|**DATETIME**|キーが作成された日付。|  
|**modify_date**|**DATETIME**|キーが変更された日付。|  
|**key_guid**|**UNIQUEIDENTIFIER**|キーに関連付けられているグローバル一意識別子 (GUID)。 保存されたキーに対しては、自動生成されます。 一時キーの Guid は、ユーザーが指定したパスフレーズから派生します。|  
|**key_thumbprint**|**sql_variant**|キーの SHA-1 ハッシュ。 ハッシュはグローバルに一意です。 拡張キー管理以外のキーの場合、この値は NULL になります。|  
|**provider_type**|**nvarchar (120)**|暗号化サービスプロバイダーの種類:<br /><br /> 暗号化サービスプロバイダー = 拡張キー管理キー<br /><br /> NULL = 拡張キー管理以外のキー|  
|**cryptographic_provider_guid**|**UNIQUEIDENTIFIER**|暗号化サービスプロバイダーの GUID。 拡張キー管理以外のキーの場合、この値は NULL になります。|  
|**cryptographic_provider_algid**|**sql_variant**|暗号化サービスプロバイダーのアルゴリズム ID。 拡張キー管理以外のキーの場合、この値は NULL になります。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 RC4 アルゴリズムは非推奨とされます。 [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
> [!NOTE]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。  
  
 **DES アルゴリズムに関する説明:**  
  
-   DESX は不適切な名前でした。 ALGORITHM = DESX を使用して作成された対称キーでは、実際には 192 ビット キーを使用した TRIPLE DES 暗号が使用されます。 DESX アルゴリズムは提供されません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
-   ALGORITHM = TRIPLE_DES_3KEY を使用して作成された対称キーでは、192 ビット キーを使用した TRIPLE DES が使用されます。  
  
-   ALGORITHM = TRIPLE_DES を使用して作成された対称キーでは、128 ビット キーを使用した TRIPLE DES が使用されます。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
