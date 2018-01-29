---
title: "KILL QUERY NOTIFICATION SUBSCRIPTION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION
- KILL_QUERY_NOTIFICATION_SUBSCRIPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION statement
- removing subscriptions
- subscriptions [SQL Server query notifications], stopping
- query notifications [SQL Server], subscriptions
ms.assetid: 8aeadf51-286c-4748-bef2-d25858b250bf
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9cec802ec4402716a8d24f7720664e4db856ca1a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="kill-query-notification-subscription-transact-sql"></a>KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスからクエリ通知サブスクリプションを削除します。 このステートメントでは、特定のサブスクリプションまたはすべてのサブスクリプションを削除できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
KILL QUERY NOTIFICATION SUBSCRIPTION   
   { ALL | subscription_id }  
```  
  
## <a name="arguments"></a>引数  
 ALL  
 インスタンス内のすべてのサブスクリプションを削除します。  
  
 *subscription_id*  
 サブスクリプション id でサブスクリプションを削除*subscription_id*です。  
  
## <a name="remarks"></a>解説  
 KILL QUERY NOTIFICATION SUBSCRIPTION ステートメントでクエリ通知サブスクリプションを削除する際、通知メッセージは生成されません。  
  
 *subscription_id*動的管理ビューで示すように、サブスクリプションの id は、 [sys.dm_qn_subscriptions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md).  
  
 指定したサブスクリプション ID が存在しない場合は、エラーが発生します。  
  
## <a name="permissions"></a>権限  
 このステートメントを実行するアクセス許可がのメンバーに制限されます、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-removing-all-query-notification-subscriptions-in-the-instance"></a>A. インスタンス内のすべてのクエリ通知サブスクリプションを削除する  
 次の例では、インスタンス内のすべてのクエリ通知サブスクリプションを削除します。  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION ALL ;  
```  
  
### <a name="b-removing-a-single-query-notification-subscription"></a>B. 1 つのクエリ通知サブスクリプションを削除する  
 次の例では、サブスクリプション ID が `73` のクエリ通知サブスクリプションを削除します。  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION 73 ;  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_qn_subscriptions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  
