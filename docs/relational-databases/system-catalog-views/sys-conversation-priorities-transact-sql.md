---
title: sys.conversation_priorities (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- conversation_priorities_TSQL
- conversation_priorities
- sys.conversation_priorities_TSQL
- sys.conversation_priorities
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], priorities
- Service Broker, conversations
- sys.conversation_priorities catalog view
ms.assetid: 7cbb9171-3310-4aae-8458-755c882d6462
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b20095d55f3e8b8e16814bf1146c4b516eab9d8f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysconversationpriorities-transact-sql"></a>sys.conversation_priorities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに作成されたメッセージ交換の優先度ごとに 1 行のデータを格納します。この行の内容を次の表に示します。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Priority_id|**int**|メッセージ交換の優先度を一意に識別する番号。 Null を許容しません。|  
|name|**sysname**|メッセージ交換の優先度の名前。 Null を許容しません。|  
|service_contract_id|**int**|メッセージ交換の優先度に指定されているコントラクトの識別子。 この列は、sys.service_contracts の service_contract_id 列に結合できます。 NULL 値は許可されます。|  
|local_service_id|**int**|メッセージ交換の優先度のローカル サービスとして指定されているサービスの識別子。 この列は、sys.services の service_id 列に結合できます。 NULL 値は許可されます。|  
|remote_service_name|**nvarchar (256)**|メッセージ交換の優先度のリモート サービスとして指定されているサービスの名前。 NULL 値は許可されます。|  
|priority|**tinyint**|このメッセージ交換の優先度で指定されている優先順位。 Null を許容しません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 次の例では、結合を使用してコントラクト名とローカル サービス名を表示することで、メッセージ交換の優先度を一覧表示します。  
  
```  
SELECT scp.name AS priority_name,  
       ssc.name AS contract_name,  
       ssvc.name AS local_service_name,  
       scp.remote_service_name,  
       scp.priority AS priority_level  
FROM sys.conversation_priorities AS scp  
    INNER JOIN sys.service_contracts AS ssc  
       ON scp.service_contract_id = ssc.service_contract_id  
    INNER JOIN sys.services AS ssvc  
       ON scp.local_service_id = ssvc.service_id  
ORDER BY priority_name, contract_name,  
         local_service_name, remote_service_name;  
  
```  
  
## <a name="see-also"></a>参照  
 [ALTER BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [DROP BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [sys.services &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-services-transact-sql.md)   
 [sys.service_contracts &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-service-contracts-transact-sql.md)  
  
  
