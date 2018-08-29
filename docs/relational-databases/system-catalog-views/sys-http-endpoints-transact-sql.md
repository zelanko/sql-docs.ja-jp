---
title: sys.http_endpoints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f27d3aa958625974fa6b11313cecb831f2308b1c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028600"
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  HTTP プロトコルを使用するサーバー内で作成されたエンドポイントごとに 1 行のデータを保持します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**< 継承された列 >**||列を継承[sys.endpoints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)します。|  
|**サイト**|**nvarchar(128)**|SITE = オプションで指定された、サイトに対するホスト コンピューター名です。|  
|**url_path**|**nvarchar (4000)**|PATH = オプションで指定された、この HTTP エンドポイントの URL のパスのみの部分です。|  
|**is_clear_port_enabled**|**bit**|1 = ポートの消去は、PORT = CLEAR オプションを使用して有効になっています。|  
|**clear_port**|**int**|CLEAR PORT = オプションで指定されたポート番号です。<br /><br /> NULL = 指定されていません。|  
|**is_ssl_port_enabled**|**bit**|1 = SSL ポートは、PORT = SSL オプションを使用して有効になっています。|  
|**ssl_port**|**int**|SSL PORT = オプションで指定されたポート番号値です。<br /><br /> NULL = 指定されていません。|  
|**is_anonymous_enabled**|**bit**|1 = 匿名アクセスは、AUTHENTICATION = ANONYMOUS オプションを使用して有効になっています。|  
|**is_basic_auth_enabled**|**bit**|1 = 基本認証は、AUTHENTICATION = BASIC オプションを使用して有効になっています。|  
|**is_digest_auth_enabled**|**bit**|1 = ダイジェスト認証は、AUTHENTICATION = DIGEST オプションを使用して有効になっています。|  
|**is_kerberos_auth_enabled**|**bit**|1 = 統合認証は、AUTHENTICATION = KERBEROS オプションを使用して有効になっています。|  
|**is_ntlm_auth_enabled**|**bit**|1 = 統合認証は、AUTHENTICATION = NTLM オプションを使用して有効になっています。|  
|**is_integrated_auth_enabled**|**bit**|1 = 統合認証は、AUTHENTICATION = INTEGRATED オプションを使用して有効になっています。|  
|**authorization_realm**|**nvarchar(128)**|HTTP DIGEST 認証の試行の一部としてクライアントに返されるヒントです。 AUTH REALM オプションの値です。<br /><br /> 指定されていない場合、または DIGEST 認証が有効になっていない場合、NULL です。|  
|**default_logon_domain**|**nvarchar(128)**|BASIC 認証を有効にしている場合は、既定のログイン ドメインです。 DEFAULT LOGON DOMAIN オプションの値です。<br /><br /> 指定されていない場合、または BASIC 認証が有効になっていない場合、NULL です。|  
|**is_compression_enabled**|**bit**|1 = COMPRESSION = ENABLED オプションが設定されています。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [エンドポイントのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
