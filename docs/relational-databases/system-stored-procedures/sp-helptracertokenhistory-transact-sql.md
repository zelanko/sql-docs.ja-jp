---
title: sp_helptracertokenhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c8e45803bc10d47ef042acebf0650ea183f61
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048284"
---
# <a name="sphelptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたトレーサー トークンの詳細な待機時間情報を、各サブスクライバーに対して 1 行ずつ返します。 このストアド プロシージャは、パブリケーション データベースに対して、パブリッシャーまたはディストリビューターのディストリビューション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` トレーサー トークンが挿入されたパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @tracer_id = ] tracer_id` におけるトレーサー トークンの id、 [MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)テーブルの履歴の情報が返されます。 *tracer_id*は**int**、既定値はありません。  
  
`[ @publisher = ] 'publisher'` パブリッシャーの名前。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]
>  このパラメーターは、に対してのみ指定する必要があります以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
`[ @publisher_db = ] 'publisher_db'` パブリケーション データベースの名前。 *publisher_db*は**sysname**既定値は NULL です。 ストアド プロシージャがパブリッシャーで実行される場合、このパラメーターは無視されます。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**bigint**|トレーサー トークン レコードをパブリッシャー側でコミットされると、ディストリビューター側でコミットされるまでの秒数。|  
|**サブスクライバー**|**sysname**|トレーサー トークンを受信したサブスクライバーの名前です。|  
|**@subscriber_db**|**sysname**|トレーサー トークン レコードが挿入されたサブスクリプション データベースの名前。|  
|**subscriber_latency**|**bigint**|トレーサー トークン レコードをディストリビューターでコミットされると、サブスクライバーでコミットされるまでの秒数。|  
|**overall_latency**|**bigint**|トレーサー トークン レコードをパブリッシャーとサブスクライバーでコミットされるトークンのレコードでコミットされるまでの秒数。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helptracertokenhistory**はトランザクション レプリケーションで使用します。  
  
 実行[sp_helptracertokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) 、パブリケーションのトレーサー トークンの一覧を取得します。  
  
 NULL の結果セット内の値は、待機時間の統計を計算することはできませんを意味します。 トレーサー トークンが、ディストリビューターまたはサブスクライバーのいずれかで受信されていないためにです。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロール、 **db_owner** 、パブリケーション データベースの固定データベース ロールまたは**db_owner**固定データベースまたは**replmonitor**ディストリビューション データベース内のロールが実行できる**sp_helptracertokenhistory**します。  
  
## <a name="see-also"></a>関連項目  
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
