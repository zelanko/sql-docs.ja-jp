---
title: sp_helpqreader_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7689cb7c31415b34abdc2320f47c754e9f749e44
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702292"
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
 ストアド プロシージャをパブリッシャー側とディストリビューター側のどちらで呼び出すかを指定します。 *frompublisher*は bit で、既定値は 0 です。 **1**パブリッシャーで、ストアド プロシージャを呼び出すことを意味し、 **0**ディストリビューターからストアド プロシージャを呼び出すことを意味します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|エージェントの ID。|  
|**name**|**nvarchar(100)**|エージェントの名前。|  
|**job_id**|**uniqueidentifier**|エージェント ジョブの一意な ID。|  
|**job_login**|**nvarchar(512)**|形式で返されるディストリビューション エージェントを実行する Windows アカウントは、*ドメイン*\\*username*します。|  
|**job_password**|**sysname**|セキュリティ上の理由から、値の**\* \* \* \* \* \* \* \* \* \*** は常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpqreader_agent**はトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 ときに、値の*frompublisher*は**1**のメンバーだけ、 **sysadmin**固定サーバー ロールのメンバー、またはパブリッシャー、 **db_owner**パブリケーション データベースの固定データベース ロールが実行できる**sp_helpqreader_agent**します。 それ以外の場合のメンバーのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner** 、ディストリビューション データベースの固定データベース ロールが実行できる**sp_helpqreader_エージェント**します。  
  
## <a name="see-also"></a>参照  
 [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
