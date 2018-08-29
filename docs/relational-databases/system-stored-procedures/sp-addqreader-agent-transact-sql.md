---
title: sp_addqreader_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3e67683fe75f555b58acf09cb2b1bee939d7151
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034713"
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
 用のログイン、[!INCLUDE[msCoName](../../includes/msconame-md.md)]エージェントを実行する Windows アカウントします。 *job_login*は**nvarchar (257)**、既定値はありません。 この Windows アカウントはディストリビューターへのエージェント接続で常に使用されます。  
  
 [ **@job_password**=] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 最大限のセキュリティを得るには、ログイン名とパスワードを実行時に指定します。  
  
 [ **@job_name**=] **'***job_name***'**  
 既存のエージェント ジョブの名前を指定します。 *job_name*は**sysname**既定値は NULL です。 このパラメーターは、新しく作成したジョブ (既定値) の代わりに既存のジョブを使ってエージェントを作成するときにだけ指定します。  
  
 [  **@frompublisher=** ] *frompublisher*  
 プロシージャがパブリッシャーで実行されているかどうかを指定します。 *frompublisher*は bit で、既定値は、 **0**します。 値**1**プロシージャがパブリッシャーのパブリケーション データベースから実行されていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addqreader_agent**はトランザクション レプリケーションで使用します。  
  
 **sp_addqreader_agent**キュー後に更新をサポートするディストリビューターで少なくとも 1 回実行する必要があります[sp_adddistributiondb](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)する前に[sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)します。  
  
 実行すると、キュー リーダー エージェント ジョブが削除[sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_addqreader_agent**します。  
  
## <a name="see-also"></a>参照  
 [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [レプリケーション スクリプトのアップグレード &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_changeqreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md)   
 [sp_helpqreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)  
  
  
