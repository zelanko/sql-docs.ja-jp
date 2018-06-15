---
title: sys.remote_service_bindings (TRANSACT-SQL) |Microsoft ドキュメント
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
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b51b1ad09e3b1dd3252178e45934fafa46d4e688
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33181518"
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リモート サービス バインドごとに 1 行のデータを格納するカタログ ビューです。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|リモート サービス バインドの名前。 Null を許容しません。|  
|**remote_service_binding_id**|**int**|リモート サービス バインドの ID。 Null を許容しません。|  
|**principal_id**|**int**|リモート サービス バインドを所有しているデータベース プリンシパルの ID。 NULL 値は許可されます。|  
|**remote_service_name**|**nvarchar (256)**|バインドが適用されるリモート サービスの名前。 NULL 値は許可されます。|  
|**service_contract_id**|**int**|バインドが適用されるコントラクトの ID。 値 0 は、このバインドがサービスのすべてのコントラクトに適用されることを表すワイルドカードです。 Null を許容しません。|  
|**remote_principal_id**|**int**|リモート サービス バインドに指定されているユーザーの ID。 Service Broker では、このユーザーが所有する証明書を使用して、指定したコントラクトに基づき、指定したサービスと通信します。 NULL 値は許可されます。|  
|**is_anonymous_on**|**bit**|リモート サービス バインドで ANONYMOUS セキュリティを使用します。 メッセージ交換を開始するユーザーの識別情報は、対象サービスに提供されません。 Null を許容しません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
  
