---
title: sp_changelogreader_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
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
- sp_changelogreader_agent
- sp_changelogreader_agent_TSQL
helpviewer_keywords:
- sp_changelogreader_agent
ms.assetid: 929b2fa7-1267-41d0-8b69-e9ab26a62c0f
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 24e2c08d56ffa85e2b6825cfbd73057014b8249c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087574"
---
# <a name="spchangelogreaderagent-transact-sql"></a>sp_changelogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  ログ リーダー エージェントのセキュリティ プロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changelogreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_login**=] **'***job_login***'**  
 エージェントを実行するアカウントのログインです。 *job_login*は**nvarchar (257)**、既定値は NULL です。 Azure SQL Database マネージ インスタンス、SQL Server アカウントを使用します。 *これ以外は変更できません*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*  
  
 [ **@job_password**=] **'***job_password***'**  
 エージェントを実行するアカウントのパスワードです。 *job_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 パブリッシャーへの接続時にエージェントが使用するセキュリティ モードを指定します。 *publisher_security_mode*は**smallint**、既定値は NULL です。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、および**1** Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [ **@publisher_login**=] **'***publisher_login***'**  
 パブリッシャーへの接続時に使用するログインを指定します。 *publisher_login*は**sysname**、既定値は NULL です。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login* null と*publisher_security_mode*は**1**で指定した Windows アカウント*job_login*ときに使用されますパブリッシャーに接続します。  
  
 [ **@publisher_password**=] **'***publisher_password***'**  
 パブリッシャーへの接続時に使用するパスワードを指定します。 *publisher_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [ **@publisher**=] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。 このパラメーターは SQL Server 以外のパブリッシャーに対してのみサポートされます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changelogreader_agent**はトランザクション レプリケーションで使用します。  
  
 **sp_changelogreader_agent**ログ リーダー エージェントを実行する Windows アカウントを変更するために使用します。 既存の Windows ログインのパスワードを変更するか、新しい Windows ログインとパスワードを指定できます。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changelogreader_agent**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_helplogreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)   
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
