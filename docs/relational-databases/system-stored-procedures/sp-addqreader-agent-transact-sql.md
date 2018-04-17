---
title: sp_addqreader_agent (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_addqreader_agent_TSQL
- sp_addqreader_agent
helpviewer_keywords:
- sp_addqreader_agent
ms.assetid: dc9f591a-e67e-4ba8-bf47-defd5eda0822
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5487e162fed4879854006498a40e1bd308d759a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddqreaderagent-transact-sql"></a>sp_addqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したディストリビューターにキュー リーダー エージェントを追加します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されるか、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addqreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name'  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_login**=] **'***job_login***'**  
 用のログイン、[!INCLUDE[msCoName](../../includes/msconame-md.md)]エージェントを実行する Windows アカウントです。 *job_login*は**nvarchar (257)**、既定値はありません。 この Windows アカウントはディストリビューターへのエージェント接続で常に使用されます。  
  
 [ **@job_password**=] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 最大限のセキュリティを得るには、ログイン名とパスワードを実行時に指定します。  
  
 [ **@job_name**=] **'***job_name***'**  
 既存のエージェント ジョブの名前を指定します。 *job_name*は**sysname**既定値は NULL です。 このパラメーターは、新しく作成したジョブ (既定値) の代わりに既存のジョブを使ってエージェントを作成するときにだけ指定します。  
  
 [  **@frompublisher=** ] *frompublisher*  
 プロシージャがパブリッシャーで実行されているかどうかを指定します。 *frompublisher*は bit で、既定値は**0**します。 値**1**プロシージャがパブリッシャー側でパブリケーション データベースから実行されていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addqreader_agent**トランザクション レプリケーションで使用します。  
  
 **sp_addqreader_agent**キュー後に更新をサポートするディストリビューターで少なくとも 1 回実行する必要があります[sp_adddistributiondb](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)前に[sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)です。  
  
 実行するときに、キュー リーダー エージェント ジョブが削除された[sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)です。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_addqreader_agent**です。  
  
## <a name="see-also"></a>参照  
 [トランザクション パブリケーションに対するサブスクリプションの更新を有効にします。](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [レプリケーション スクリプトのアップグレード &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_changeqreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md)   
 [sp_helpqreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)  
  
  
