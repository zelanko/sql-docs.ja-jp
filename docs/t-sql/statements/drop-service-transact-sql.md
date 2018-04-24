---
title: DROP SERVICE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP_SERVICE_TSQL
- DROP SERVICE
dev_langs:
- TSQL
helpviewer_keywords:
- deleting services
- services [Service Broker], removing
- dropping services
- DROP SERVICE statement
- removing services
ms.assetid: 2351bba7-0f2a-4cda-b3b2-6a88b8747c53
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86cb7cdbc579a6086a9992a5092bb061a3a62fa7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="drop-service-transact-sql"></a>DROP SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のサービスを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP SERVICE service_name  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *service_name*  
 削除するサービスの名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
## <a name="remarks"></a>Remarks  
 サービスがメッセージ交換の優先度で参照されている場合、そのサービスは削除できません。  
  
 サービスを削除すると、そのサービスへのすべてのメッセージが、サービスで使用されるキューから削除されます。 メッセージ交換でサービスが使用されている場合は、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってリモート側にエラーが送信されます。  
  
## <a name="permissions"></a>アクセス許可  
 サービスを削除する権限は、既定では、サービスの所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、サービス `//Adventure-Works.com/Expenses` を削除します。  
  
```  
DROP SERVICE [//Adventure-Works.com/Expenses] ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [ALTER SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-service-transact-sql.md)   
 [CREATE SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/create-service-transact-sql.md)   
 [DROP BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
