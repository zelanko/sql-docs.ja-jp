---
title: dm_cryptographic_provider_properties (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b08159d666fb18cc92feb88f087168b249ff523
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824698"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  登録されている暗号化サービスプロバイダーに関する情報を返します。  
  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|暗号化サービスプロバイダーの識別番号。|  
|guid|**uniqueidentifier**|一意のプロバイダー GUID。|  
|provider_version|**nvarchar(256)**|プロバイダーのバージョンを '*aa.bb.cccc.dd*' の形式で指定します。|  
|sqlcrypt_version|**nvarchar(256)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]'*Aa.bb.cccc.dd*' 形式の暗号化 API のメジャーバージョン。|  
|friendly_name|**nvarchar(2048)**|プロバイダーによって指定された名前。|  
|authentication_type|**nvarchar(256)**|WINDOWS、BASIC、またはその他。|  
|symmetric_key_support|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_export|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_import|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_persistance|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|asymmetric_key_support|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|asymmetric_key_export|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_import|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_persistance|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
  
## <a name="remarks"></a>Remarks  
 sys.dm_cryptographic_provider_properties ビューはパブリックに表示できます。  
  
## <a name="see-also"></a>参照  
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Transact-sql&#41;&#40;暗号化サービスプロバイダーを作成する](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
