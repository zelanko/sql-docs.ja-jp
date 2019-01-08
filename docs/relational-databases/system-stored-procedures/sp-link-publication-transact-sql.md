---
title: sp_link_publication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_link_publication_TSQL
- sp_link_publication
helpviewer_keywords:
- sp_link_publication
ms.assetid: 1945ed24-f9f1-4af6-94ca-16d8e864706e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c713b4efcfd37c245f340769a4725b0792d7528b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210056"
---
# <a name="splinkpublication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャーへの接続時に即時更新サブスクリプションの同期トリガーが使用する、構成およびセキュリティ情報を設定します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
> [!IMPORTANT]
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
> 
> [!IMPORTANT]
>  サブスクライバーが実行されている場合、特定の条件下でこのストアド プロシージャが失敗することができます[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 またはそれ以降、および発行元は、以前のバージョンを実行します。 このシナリオでストアド プロシージャが失敗する場合は、パブリッシャーを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 以降にアップグレードしてください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_link_publication [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'   
        , [ @publication = ] 'publication'   
        , [ @security_mode = ] security_mode  
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ]'password' ]  
    [ , [ @distributor = ] 'distributor' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher**=] **'***パブリッシャー***'**  
 リンクするパブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db**=] **'***publisher_db***'**  
 リンクするパブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication**=] **'***パブリケーション***'**  
 リンクするパブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@security_mode**=] *security_mode*  
 サブスクライバーが即時更新のためにリモートのパブリッシャーに接続するときに使用するセキュリティ モードです。 *security_mode*は**int**、これらの値のいずれかを指定できます。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
|値|説明|  
|-----------|-----------------|  
|**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]としてこのストアド プロシージャで指定されたログインを使用して認証*ログイン*と*パスワード*します。<br /><br /> 注:前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このオプションを使用して動的なリモート プロシージャ コール (RPC) を指定していました。|  
|**1**|サブスクライバーで変更を行っているユーザーのセキュリティ コンテキスト ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証または Windows 認証) を使用します。<br /><br /> 注:パブリッシャー側でも、十分な権限を持つこのアカウントが必要です。 Windows 認証を使用する場合は、セキュリティ アカウントの委任がサポートされる必要があります。|  
|**2**|使用して作成、既存のユーザー定義リンク サーバー ログイン**sp_link_publication**します。|  
  
 [ **@login**=] **'***ログイン***'**  
 ログインを指定します。 *login* のデータ型は **sysname** で、既定値は NULL です。 このパラメーターである必要があるときに指定された*security_mode*は**0**します。  
  
 [ **@password**=] **'***パスワード***'**  
 パスワードです。 *パスワード*は**sysname**、既定値は NULL です。 このパラメーターである必要があるときに指定された*security_mode*は**0**します。  
  
 [  **@distributor=** ] **'***ディストリビューター***'**  
 ディストリビューターの名前です。 *ディストリビューター*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_link_publication**トランザクション レプリケーションで即時更新サブスクリプションによって使用されます。  
  
 **sp_link_publication**プッシュとプルの両方のサブスクリプションに使用できます。 サブスクリプション作成前、または作成後に呼び出すことができます。 エントリが挿入または更新、 [MSsubscription_properties &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md)システム テーブル。  
  
 プッシュ サブスクリプションの場合、エントリをクリーンアップできますによって[sp_subscription_cleanup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)します。 プル サブスクリプションの場合、エントリをクリーンアップできますによって[sp_droppullsubscription &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)または[sp_subscription_cleanup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)します。 呼び出すこともできます**sp_link_publication**でエントリをクリアする NULL パスワードを使用して、 [MSsubscription_properties &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md)セキュリティ関連のシステム テーブル。  
  
 即時更新サブスクライバーがパブリッシャーに接続するときに使用する既定のモードでは、Windows 認証を使っての接続は許可されません。 Windows 認証のモードを使って接続するには、パブリッシャーに対してリンク サーバーを設定する必要があり、即時更新サブスクライバーは、サブクライバを更新するときにこの接続を使用する必要があります。 これが必要です、 **sp_link_publication**併用して実行する*security_mode* = **2**します。 Windows 認証を使用する場合は、セキュリティ アカウントの委任がサポートされる必要があります。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_link_publication**します。  
  
## <a name="see-also"></a>参照  
 [sp_droppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
