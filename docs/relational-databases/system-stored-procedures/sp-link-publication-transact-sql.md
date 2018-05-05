---
title: sp_link_publication (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_link_publication_TSQL
- sp_link_publication
helpviewer_keywords:
- sp_link_publication
ms.assetid: 1945ed24-f9f1-4af6-94ca-16d8e864706e
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 17e1b051fed32e78cd18cc634b7688245ecb0972
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="splinkpublication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャーへの接続時に即時更新サブスクリプションの同期トリガーが使用する、構成およびセキュリティ情報を設定します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
> [!IMPORTANT]  
>  特定の状況では、このストアド プロシージャは失敗する場合は、サブスクライバーが実行されている[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 以降、およびパブリッシャーは、以前のバージョンを実行します。 このシナリオでは、ストアド プロシージャが失敗した場合、アップグレードのパブリッシャーから[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Service Pack 1 またはそれ以降。  
  
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
|**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]としてこのストアド プロシージャで指定されたログインを持つ認証*ログイン*と*パスワード*です。<br /><br /> 注: 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、動的なリモート プロシージャ コール (RPC) を指定するには、このオプションが使用されました。|  
|**1**|セキュリティ コンテキストを使用 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証または Windows 認証)、サブスクライバーの変更を行うユーザーのです。<br /><br /> 注: このアカウントは、十分な特権を持つパブリッシャーの存在も必要があります。 Windows 認証を使用する場合は、セキュリティ アカウントの委任がサポートされる必要があります。|  
|**2**|使用して作成、既存のユーザー定義リンク サーバー ログイン**sp_link_publication**です。|  
  
 [ **@login**=] **'***ログイン***'**  
 ログインを指定します。 *login* のデータ型は **sysname** で、既定値は NULL です。 このパラメーターを指定する必要がある時に指定された*security_mode*は**0**します。  
  
 [ **@password**=] **'***パスワード***'**  
 パスワードです。 *パスワード*は**sysname**、既定値は NULL です。 このパラメーターを指定する必要がある時に指定された*security_mode*は**0**します。  
  
 [  **@distributor=** ] **'***ディストリビューター***'**  
 ディストリビューターの名前です。 *ディストリビューター*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_link_publication**はトランザクション レプリケーションで即時更新サブスクリプションによって使用されます。  
  
 **sp_link_publication**プッシュとプルは両方のサブスクリプションに使用することができます。 サブスクリプション作成前、または作成後に呼び出すことができます。 エントリが挿入または更新、 [MSsubscription_properties &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md)システム テーブル。  
  
 プッシュ サブスクリプションの場合、エントリ クリーンアップできますによって[sp_subscription_cleanup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)です。 プル サブスクリプションの場合、エントリ クリーンアップできますによって[sp_droppullsubscription &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)または[sp_subscription_cleanup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)です。 呼び出すこともできます**sp_link_publication**内のエントリをクリアする NULL パスワードで、 [MSsubscription_properties &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md)セキュリティ関連のシステム テーブル。  
  
 即時更新サブスクライバーがパブリッシャーに接続するときに使用する既定のモードでは、Windows 認証を使っての接続は許可されません。 Windows 認証のモードを使って接続するには、パブリッシャーに対してリンク サーバーを設定する必要があり、即時更新サブスクライバーは、サブクライバを更新するときにこの接続を使用する必要があります。 これは、必要があります、 **sp_link_publication**で実行する*security_mode* = **2**です。 Windows 認証を使用する場合は、セキュリティ アカウントの委任がサポートされる必要があります。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_link_publication**です。  
  
## <a name="see-also"></a>参照  
 [sp_droppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
