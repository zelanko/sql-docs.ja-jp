---
title: "sys.soap_endpoints (TRANSACT-SQL) |Microsoft ドキュメント"
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
- soap_endpoints_TSQL
- sys.soap_endpoints
- soap_endpoints
- sys.soap_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.soap_endpoints catalog view
ms.assetid: f50dcbfc-02ed-4a19-9c07-c78a5a1b3224
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 38bc05ab3d49716f2c4fc484098c4ff838bc634e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syssoapendpoints-transact-sql"></a>sys.soap_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 SOAP 型ペイロードを扱うサーバーのエンドポイントごとに 1 行のデータを格納します。 このビューの各行は、同じ行に対応**endpoint_id**で、 **sys.http_endpoints**カタログ ビューに、HTTP 構成メタデータ。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**< 継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.endpoints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**is_sql_language_enabled**|**bit**|1 は、BATCHES = ENABLED オプションが指定されていることを示します。エンドポイントでアドホック SQL バッチが許可されます。|  
|**wsdl_generator_procedure**|**nvarchar (776)**|このメソッドを実装するストアド プロシージャの、3 つの要素で構成される名前。<br /><br /> メソッドの名前は、3 つの要素で構成する必要があります。 1 つの要素、2 つの要素、または 4 つの要素で構成される名前は許可されません。|  
|**default_database**|**sysname**|DATABASE = オプションで指定される、既定のデータベースの名前。<br /><br /> NULL = DEFAULT が指定されています。|  
|**default_namespace**|**nvarchar (384)**|NAMESPACE = オプションで指定される、既定の名前空間。DEFAULT が指定されている場合は 'http://tempuri.org' になります。|  
|**default_result_schema**|**tinyint**|SCHEMA = オプションの既定値。<br /><br /> 0 = NONE<br /><br /> 1 = STANDARD|  
|**default_result_schema_desc**|**nvarchar (60)**|SCHEMA = オプションの既定値の説明。<br /><br /> なし<br /><br /> STANDARD|  
|**is_xml_charset_enforced**|**bit**|0 は、CHARACTER_SET = SQL オプションが指定されていることを示します。<br /><br /> 1 は、CHARACTER_SET = XML オプションが指定されていることを示します。|  
|**is_session_enabled**|**bit**|0 は、SESSION = DISABLE オプションが指定されていることを示します。<br /><br /> 1 は、SESSION = ENABLED オプションが指定されていることを示します。|  
|**session_timeout**|**int**|SESSION_TIMEOUT オプションで指定された値。|  
|**login_type**|**nvarchar (60)**|エンドポイントで許可される認証の種類。<br /><br /> WINDOWS<br /><br /> MIXED|  
|**header_limit**|**int**|SOAP ヘッダーの最大許容サイズ。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エンドポイントのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
