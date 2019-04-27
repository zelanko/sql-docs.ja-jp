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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639128"
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このカタログ ビューには、リモート サービス バインドごとに 1 行が含まれています。 
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|このリモート サービス バインドの名前です。 Null を許容しません。|  
|**remote_service_binding_id**|**int**|このリモート サービス バインドの ID。 Null を許容しません。|  
|**principal_id**|**int**|このリモート サービス バインドを所有するデータベース プリンシパルの ID。 NULL 値を許容します。|  
|**remote_service_name**|**nvarchar (256)**|このバインドが適用されるリモート サービスの名前。 NULL 値を許容します。|  
|**service_contract_id**|**int**|このバインドが適用されているコントラクトの ID。 値 0 は、サービスのすべてのコントラクトにこのバインドが適用されることを意味するワイルドカードです。 Null を許容しません。|  
|**remote_principal_id**|**int**|リモート サービス バインドで指定されたユーザーの ID。 Service Broker では、このユーザーが所有する証明書を使用して、指定したコントラクトに基づき、指定したサービスと通信します。 NULL 値を許容します。|  
|**is_anonymous_on**|**bit**|このリモート サービス バインドでは、匿名セキュリティを使用します。 対象サービスには、メッセージ交換を開始したユーザーの id が指定されていません。 Null を許容しません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
