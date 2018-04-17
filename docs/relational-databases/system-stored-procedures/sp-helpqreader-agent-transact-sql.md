---
title: sp_helpqreader_agent (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0e7aeb2448ff44ef39a638ea61c64b72f0a7d123
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpqreaderagent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キュー リーダー エージェントのプロパティを返します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。またはパブリッシャー側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@frompublisher=** ] *frompublisher*  
 ストアド プロシージャをパブリッシャー側とディストリビューター側のどちらで呼び出すかを指定します。 *frompublisher*は bit で、既定値は 0 です。 **1** 、パブリッシャーからストアド プロシージャを呼び出すことを意味し、 **0**ディストリビューターからストアド プロシージャを呼び出すことを意味します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|エージェントの ID です。|  
|**name**|**nvarchar(100)**|エージェントの名前。|  
|**job_id**|**uniqueidentifier**|エージェント ジョブの一意な ID。|  
|**job_login**|**nvarchar(512)**|形式で返される、ディストリビューション エージェントを実行する Windows アカウントは、*ドメイン*\\*username*です。|  
|**job_password**|**sysname**|セキュリティ上の理由の値**\* \* \* \* \* \* \* \* \* \***は常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpqreader_agent**トランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 ときの値*frompublisher*は**1**のメンバーにのみ、 **sysadmin**のメンバーまたはパブリッシャーの固定サーバー ロール、 **db_owner**、パブリケーション データベースの固定データベース ロールが実行できる**sp_helpqreader_agent**です。 それ以外の場合のメンバーにのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner**ディストリビューション データベースの固定データベース ロールが実行できる**sp_helpqreader_エージェント**です。  
  
## <a name="see-also"></a>参照  
 [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
