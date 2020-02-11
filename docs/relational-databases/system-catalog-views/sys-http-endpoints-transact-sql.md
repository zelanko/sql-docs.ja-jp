---
title: http_endpoints (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41ca717399a3cd86f2137de6ae474d89e3eb819e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122732"
---
# <a name="syshttp_endpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  HTTP プロトコルを使用するサーバー内で作成されたエンドポイントごとに 1 行のデータを保持します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**< 継承された列>**||[では、transact-sql&#41;&#40;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)から列を継承しています。|  
|**サイト**|**nvarchar(128**|Site = オプションで指定された、サイトのホストコンピューターの名前。|  
|**url_path**|**nvarchar(4000)**|PATH = オプションで指定された、この HTTP エンドポイントの URL のパスのみの部分。|  
|**is_clear_port_enabled**|**bit**|1 = クリアポートは、PORT = CLEAR オプションを使用して有効にします。|  
|**clear_port**|**int**|CLEAR PORT = オプションで指定されたポート番号です。<br /><br /> NULL = 指定されていません。|  
|**is_ssl_port_enabled**|**bit**|1 = SSL ポートは、PORT = SSL オプションを使用して有効にします。|  
|**ssl_port**|**int**|SSL PORT = オプションで指定されたポート番号値です。<br /><br /> NULL = 指定されていません。|  
|**is_anonymous_enabled**|**bit**|1 = 匿名アクセスは、AUTHENTICATION = ANONYMOUS オプションを使用して有効にします。|  
|**is_basic_auth_enabled**|**bit**|1 = 基本認証は、AUTHENTICATION = BASIC オプションを使用して有効にします。|  
|**is_digest_auth_enabled**|**bit**|1 = ダイジェスト認証は、AUTHENTICATION = DIGEST オプションを使用して有効になっています。|  
|**is_kerberos_auth_enabled**|**bit**|1 = 統合認証は、AUTHENTICATION = KERBEROS オプションを使用して有効になっています。|  
|**is_ntlm_auth_enabled**|**bit**|1 = 認証 = NTLM オプションを使用して統合認証を有効にします。|  
|**is_integrated_auth_enabled**|**bit**|1 = 統合認証は、AUTHENTICATION = INTEGRATED オプションを使用して有効にします。|  
|**authorization_realm**|**nvarchar(128**|HTTP ダイジェスト認証チャレンジの一部としてクライアントに返されるヒント。 AUTH REALM オプションの値です。<br /><br /> 指定されていない場合、または DIGEST 認証が有効になっていない場合、NULL です。|  
|**default_logon_domain**|**nvarchar(128**|基本認証を有効にした場合の既定のログインドメイン。 DEFAULT LOGON DOMAIN オプションの値です。<br /><br /> が指定されていない場合、または基本認証が有効になっていない場合は NULL になります。|  
|**is_compression_enabled**|**bit**|1 = COMPRESSION = ENABLED オプションが設定されています。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [エンドポイントのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
