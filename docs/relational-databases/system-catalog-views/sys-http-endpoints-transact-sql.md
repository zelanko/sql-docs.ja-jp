---
title: "sys.http_endpoints (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af5140f2389501a10a9228c2e133441f072c2efc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  HTTP プロトコルを使用するサーバー内で作成されたエンドポイントごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**< 継承された列 >**||列を継承[sys.endpoints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**サイト**|**nvarchar (128)**|SITE = オプションで指定された、サイトに対するホスト コンピューター名です。|  
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
|**authorization_realm**|**nvarchar (128)**|HTTP DIGEST 認証の試行の一部としてクライアントに返されるヒントです。 AUTH REALM オプションの値です。<br /><br /> 指定されていない場合、または DIGEST 認証が有効になっていない場合、NULL です。|  
|**default_logon_domain**|**nvarchar (128)**|BASIC 認証を有効にしている場合は、既定のログイン ドメインです。 DEFAULT LOGON DOMAIN オプションの値です。<br /><br /> 指定されていない場合、または BASIC 認証が有効になっていない場合、NULL です。|  
|**is_compression_enabled**|**bit**|1 = COMPRESSION = ENABLED オプションが設定されています。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [エンドポイントのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
