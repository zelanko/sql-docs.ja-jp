---
title: "sys.cryptographic_providers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cryptographic_providers
- sys.cryptographic_providers
- sys.cryptographic_providers_TSQL
- cryptographic_providers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.cryptographic_providers catalog view
ms.assetid: 9da0da95-792e-48b4-9f60-47f0729c279c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c453171a7378a0fb7201c8a2e577b207e5042337
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syscryptographicproviders-transact-sql"></a>sys.cryptographic_providers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  登録されている暗号プロバイダーごとに 1 行を返します。  
    
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|暗号化サービス プロバイダーの ID 番号。|  
|**name**|**sysname**|暗号プロバイダーの名前。|  
|**guid**|**uniqueidentifier**|一意のプロバイダー GUID。|  
|**version**|**nvarchar (50)**|バージョンの形式でプロバイダー '*aa.bb.cccc.dd*' です。|  
|**dll_path**|**nvarchar(512)**|拡張キー管理 (EKM) アプリケーション プログラミング インターフェイス (API) を実装する DLL へのパス。|  
|**is_enabled**|**bit**|サーバーでプロバイダーが有効になっているかどうか。<br /><br /> 0 = 有効ではない (既定)<br /><br /> 1 = 有効になっています。|  
  
## <a name="remarks"></a>解説  
 **Sys.cryptographic_providers**ビューは、パブリックに表示します。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)  
  
  
