---
title: sp_deletetracertokenhistory (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25f264f72042b6d26b3ebc5c677bc9ed4a981751
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トレーサー トークン レコードを削除、 [MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)と[MStracer_history &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md)システム テーブル。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。または、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_deletetracertokenhistory [ @publication = ] 'publication'   
    [ , [ @tracer_id = ] tracer_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 トレーサー トークンが挿入されたパブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@tracer_id=** ] *tracer_id*  
 削除するトレーサー トークンの ID です。 *tracer_id*は**int**既定値は NULL です。 場合**null**、パブリケーションに属するすべてのトレーサー トークンが削除されます。  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 終了日を指定します。それ以前にパブリケーションに挿入されたすべてのトレーサー トークンが削除されます。 *cutoff_date*は datetime で、既定値は NULL です。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 パブリッシャーの名前。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは、に対してのみ指定する必要があります以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**既定値は NULL です。 ストアド プロシージャがパブリッシャーで実行される場合、このパラメーターは無視されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_deletetracertokenhistory**トランザクション レプリケーションで使用します。  
  
 実行時に**sp_deletetracertokenhistory**のいずれかを指定することができますのみ*tracer_id*または*cutoff_date*です。 パラメーターを 2 つ指定するとエラーが発生します。  
  
 実行しないようにする場合**sp_deletetracertokenhistory**を削除するトレーサー トークン メタデータを定期的にスケジュールされた履歴のクリーンアップが発生すると、情報は削除されます。  
  
 トレーサー トークン Id を実行することで決定できます[sp_helptracertokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md)またはクエリを実行して、 [MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)システム テーブル。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**パブリケーション データベースの固定データベース ロールまたは**db_owner**固定データベースまたは**replmonitor**ディストリビューション データベース内のロールが実行できる**sp_deletetracertokenhistory**です。  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_helptracertokenhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)  
  
  
