---
title: sp_addlogreader_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addlogreader_agent
- sp_addlogreader_agent_TSQL
helpviewer_keywords:
- sp_addlogreader_agent
ms.assetid: d83096b9-96ee-4789-bde0-940d4765b9ed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6fdec3ada9bec27f6ecca2ea6a888d01640f6edb
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210841"
---
# <a name="spaddlogreaderagent-transact-sql"></a>sp_addlogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースにログ リーダー エージェントを追加します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addlogreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_login**=] **'**_job_login_**'**  
 エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウント用のログインを指定します。 *job_login*は**nvarchar (257)** 既定値は NULL です。 この Windows アカウントはディストリビューターへのエージェント接続で常に使用されます。  
  
> [!NOTE]
>  非[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、こので指定されたのと同じログインをする必要があります[sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)します。  
  
 [ **@job_password**=] **'**_job_password_**'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**既定値は NULL です。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 最大限のセキュリティを得るには、ログイン名とパスワードを実行時に指定します。  
  
 [ **@job_name**=] **'**_job_name_**'**  
 既存のエージェント ジョブの名前を指定します。 *job_name*は**sysname**既定値は NULL です。 このパラメーターは、新しく作成したジョブ (既定値) の代わりに既存のジョブを使ってエージェントを起動するときにだけ指定します。  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 パブリッシャーへの接続時にエージェントが使用するセキュリティ モードを指定します。 *publisher_security_mode*は**smallint**、既定値は**1**します。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、および**1** Windows 認証を指定します。 値**0**を指定する必要があります以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [ **@publisher_login**=] **'**_publisher_login_**'**  
 パブリッシャーへの接続時に使用するログインを指定します。 *publisher_login*は**sysname**、既定値は NULL です。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login* null と*publisher_security_mode*は**1**で指定した Windows アカウント*job_login*使用されますときに、パブリッシャーに接続します。  
  
 [ **@publisher_password**=] **'**_publisher_password_**'**  
 パブリッシャーへの接続時に使用するパスワードを指定します。 *publisher_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 最大限のセキュリティを得るには、ログイン名とパスワードを実行時に指定します。  
  
 [ **@publisher**=] **'**_パブリッシャー_**'**  
 以外の名前を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーの場合はこのパラメーターを指定しないでください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addlogreader_agent**はトランザクション レプリケーションで使用します。  
  
 実行する必要があります**sp_addlogreader_agent**のこのバージョンへのレプリケーションの有効化されたデータベースをアップグレードした場合は、ログ リーダー エージェントを追加する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーションを作成、データベースを使用する前にします。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addlogreader_agent**します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addlogreader-agent-tr_1.sql)]  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changelogreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
