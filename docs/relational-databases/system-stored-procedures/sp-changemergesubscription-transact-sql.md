---
title: sp_changemergesubscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
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
f1_keywords:
- sp_changemergesubscription_TSQL
- sp_changemergesubscription
helpviewer_keywords:
- sp_changemergesubscription
ms.assetid: fd820f35-c189-4e2d-884d-b60c1c469f58
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eda4f52de6d6b072f8250a00dcff82623badb43c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spchangemergesubscription-transact-sql"></a>sp_changemergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージのプッシュ サブスクリプションについて、選択したプロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changemergesubscription [ [ @publication= ] 'publication' ]  
    [ , [ @subscriber= ] 'subscriber'  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 変更するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は NULL です。 変更できるのは既存のパブリケーションだけであり、識別子の規則に従う必要があります。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_db=**] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値は NULL です。  
  
 [  **@property=**] **'***プロパティ***'**  
 指定したパブリケーションを変更するプロパティです。 *プロパティ*は**sysname**テーブル内の値のいずれかを指定できます。  
  
 [  **@value=**] **'***値***'**  
 指定された新しい値は、*プロパティ*です。 *値*は**nvarchar (255)**テーブル内の値のいずれかを指定できます。  
  
|プロパティ|値|Description|  
|--------------|-----------|-----------------|  
|**説明**||マージ サブスクリプションの説明。|  
|**priority**||サブスクリプションの優先度。 優先度は、競合の検出時、既定の競合回避モジュールによって実行される操作を選択する場合に使用されます。|  
|**merge_job_login**||エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのログイン。|  
|**merge_job_password**||エージェントを実行する Windows アカウントのパスワード。|  
|**publisher_security_mode**|**1**|パブリッシャーに接続するときに Windows 認証を使用。|  
||**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーに接続するときに認証します。|  
|**publisher_login**||パブリッシャーでのログイン名。|  
|**publisher_password**||指定したパブリッシャー ログインに対する複雑なパスワード。|  
|**subscriber_security_mode**|**1**|サブスクライバーに接続するときに Windows 認証を使用。|  
||**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーに接続するときに認証します。|  
|**subscriber_login**||サブスクライバーでのログイン名。|  
|**subscriber_password**||指定したサブスクライバー ログインに対する複雑なパスワード。|  
|**sync_type**|**自動**|パブリッシュされたテーブルのスキーマと初期データが、最初にサブスクライバーに転送されます。|  
||**[なし]**|サブスクライバーには、パブリッシュされたテーブルに関するスキーマと初期データがあります。システム テーブルとデータが常に転送されます。|  
|**use_interactive_resolver**|**true**|対話的に競合を回避できるすべてのアーティクルについて、対話的に競合を解決できるようにします。|  
||**false**|既定の競合回避モジュールまたはカスタム競合回避モジュールを使用して自動的に競合を解決します。|  
|NULL (既定値)|NULL (既定値)||  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changemergesubscription**はマージ レプリケーションで使用します。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changemergesubscription**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
