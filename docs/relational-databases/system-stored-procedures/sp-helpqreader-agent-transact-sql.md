---
title: sp_helpqreader_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 229442fed0defba9ebe39822a6184ba3b5d35644
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137555"
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
`[ @frompublisher = ] frompublisher` パブリッシャーまたはディストリビューターで、ストアド プロシージャを呼び出すかどうかを指定します。 *frompublisher*は bit で、既定値は 0 です。 **1**パブリッシャーで、ストアド プロシージャを呼び出すことを意味し、 **0**ディストリビューターからストアド プロシージャを呼び出すことを意味します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|エージェントの ID。|  
|**name**|**nvarchar(100)**|エージェントの名前。|  
|**job_id**|**uniqueidentifier**|エージェント ジョブの一意の ID。|  
|**job_login**|**nvarchar(512)**|形式で返されるディストリビューション エージェントを実行する Windows アカウントは、*ドメイン*\\*username*します。|  
|**job_password**|**sysname**|セキュリティ上の理由から、値の **\* \* \* \* \* \* \* \* \* \*** は常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpqreader_agent**はトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 ときに、値の*frompublisher*は**1**のメンバーだけ、 **sysadmin**固定サーバー ロールのメンバー、またはパブリッシャー、 **db_owner**パブリケーション データベースの固定データベース ロールが実行できる**sp_helpqreader_agent**します。 それ以外の場合のメンバーのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner** 、ディストリビューション データベースの固定データベース ロールが実行できる**sp_helpqreader_エージェント**します。  
  
## <a name="see-also"></a>関連項目  
 [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
