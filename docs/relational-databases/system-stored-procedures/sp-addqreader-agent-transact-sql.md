---
title: sp_addqreader_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqreader_agent_TSQL
- sp_addqreader_agent
helpviewer_keywords:
- sp_addqreader_agent
ms.assetid: dc9f591a-e67e-4ba8-bf47-defd5eda0822
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5ce192a0d3510f6034ff223f6573bf1e058516e9
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494324"
---
# <a name="spaddqreaderagent-transact-sql"></a>sp_addqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のディストリビューターに対するキュー リーダー エージェントを追加します。 このストアド プロシージャは、ディストリビューターのディストリビューション データベースで、またはパブリケーション データベースに対して、パブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addqreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name'  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>引数  
`[ @job_login = ] 'job_login'` 用のログイン、[!INCLUDE[msCoName](../../includes/msconame-md.md)]エージェントを実行する Windows アカウントします。 *job_login*は**nvarchar (257)**、既定値はありません。 この Windows アカウントは常に、ディストリビューターへのエージェント接続で使用します。  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password* は **sysname** 、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルでは、認証情報を格納しないでください。 安全性を高めるためには、ログイン名とパスワードを実行時に指定する必要があります。  
  
`[ @job_name = ] 'job_name'` 既存のエージェント ジョブの名前です。 *job_name* は **sysname** 既定値は NULL です。 新しく作成されたジョブ (既定値) の代わりに、既存のジョブを使用して、エージェントが作成されたときにのみこのパラメーターを指定します。  
  
`[ @frompublisher = ] frompublisher` プロシージャがパブリッシャーで実行されているかどうかを指定します。 *frompublisher*は bit で、既定値は、 **0**します。 値**1**プロシージャがパブリッシャーのパブリケーション データベースから実行されていることを意味します。  
  
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
  
  
