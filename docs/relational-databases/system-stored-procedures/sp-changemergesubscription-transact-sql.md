---
title: sp_changemergesubscription (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergesubscription_TSQL
- sp_changemergesubscription
helpviewer_keywords:
- sp_changemergesubscription
ms.assetid: fd820f35-c189-4e2d-884d-b60c1c469f58
author: stevestein
ms.author: sstein
ms.openlocfilehash: c205bab104bd81eda3e7d14dc30844352caa7f66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124870"
---
# <a name="sp_changemergesubscription-transact-sql"></a>sp_changemergesubscription (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージのプッシュ サブスクリプションについて、選択したプロパティを変更します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベースエンジン &#40;SQL Server 構成マネージャー&#41;への暗号化接続の有効化](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changemergesubscription [ [ @publication= ] 'publication' ]  
    [ , [ @subscriber= ] 'subscriber'  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`変更するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値は NULL です。 変更できるのは既存のパブリケーションだけであり、識別子の規則に従う必要があります。  
  
`[ @subscriber = ] 'subscriber'`サブスクライバーの名前を指定します。 *サブスクライバー*の**sysname**,、既定値は NULL です。  
  
`[ @subscriber_db = ] 'subscriber_db'`サブスクリプションデータベースの名前を指定します。 *subscriber_db*は**sysname**,、既定値は NULL です。  
  
`[ @property = ] 'property'`指定したパブリケーションの変更対象となるプロパティを指定します。 *プロパティ*は**sysname**,、テーブル内のいずれかの値を指定できます。  
  
`[ @value = ] 'value'`指定した*プロパティ*の新しい値を指定します。 *値*は**nvarchar (255)**,、テーブル内の値のいずれかを指定することができます。  
  
|プロパティ|値|[説明]|  
|--------------|-----------|-----------------|  
|**記述**||マージ サブスクリプションの説明。|  
|**的**||サブスクリプションの優先度です。 既定の競合回避モジュールでは、競合が検出された場合に優先される優先順位を使用します。|  
|**merge_job_login**||エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのログイン。|  
|**merge_job_password**||エージェントを実行する Windows アカウントのパスワード。|  
|**publisher_security_mode**|**1**|パブリッシャーに接続するときに Windows 認証を使用。|  
||**0**|パブリッシャー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続するときに認証を使用します。|  
|**publisher_login**||パブリッシャーでのログイン名。|  
|**publisher_password**||指定されたパブリッシャーログインの強力なパスワード。|  
|**subscriber_security_mode**|**1**|サブスクライバーに接続するときに Windows 認証を使用。|  
||**0**|サブスクライバー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続時に認証を使用します。|  
|**subscriber_login**||サブスクライバーでのログイン名。|  
|**subscriber_password**||指定されたサブスクライバーログインの強力なパスワード。|  
|**sync_type**|**自動**|パブリッシュされたテーブルのスキーマと初期データは、最初にサブスクライバーに転送されます。|  
||**存在**|サブスクライバーには、パブリッシュされたテーブルのスキーマと初期データが既にあります。システムテーブルとデータは常に転送されます。|  
|**use_interactive_resolver**|**本来**|対話的に競合を回避できるすべてのアーティクルについて、対話的に競合を解決できるようにします。|  
||**false**|既定の競合回避モジュールまたはカスタム競合回避モジュールを使用して自動的に競合を解決します。|  
|NULL (既定値)|NULL (既定値)||  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changemergesubscription**は、マージレプリケーションで使用します。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_changemergesubscription**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_addmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
