---
title: sys.remote_service_bindings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 2a0b326eef888ebf36fded7ae4ab95fe9f1b6bc0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785200"
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リモート サービス バインドごとに 1 行のデータを格納するカタログ ビューです。 
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|リモート サービス バインドの名前。 Null を許容しません。|  
|**remote_service_binding_id**|**int**|リモート サービス バインドの ID。 Null を許容しません。|  
|**principal_id**|**int**|リモート サービス バインドを所有しているデータベース プリンシパルの ID。 NULL 値は許可されます。|  
|**remote_service_name**|**nvarchar (256)**|バインドが適用されるリモート サービスの名前。 NULL 値は許可されます。|  
|**service_contract_id**|**int**|バインドが適用されるコントラクトの ID。 値 0 は、このバインドがサービスのすべてのコントラクトに適用されることを表すワイルドカードです。 Null を許容しません。|  
|**remote_principal_id**|**int**|リモート サービス バインドに指定されているユーザーの ID。 Service Broker では、このユーザーが所有する証明書を使用して、指定したコントラクトに基づき、指定したサービスと通信します。 NULL 値は許可されます。|  
|**is_anonymous_on**|**bit**|リモート サービス バインドで ANONYMOUS セキュリティを使用します。 メッセージ交換を開始するユーザーの識別情報は、対象サービスに提供されません。 Null を許容しません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
