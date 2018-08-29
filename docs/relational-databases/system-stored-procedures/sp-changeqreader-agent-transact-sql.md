---
title: sp_changeqreader_agent (TRANSACT-SQL) |Microsoft Docs
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
- sp_changeqreader_agent_TSQL
- sp_changeqreader_agent
helpviewer_keywords:
- sp_changeqreader_agent
ms.assetid: d3fe79c5-31ef-4565-bf38-b476b5fb16f7
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 82b799ed8fab4a782a89f15dab779020d63a28f4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034597"
---
# <a name="spchangeqreaderagent-transact-sql"></a>sp_changeqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キュー リーダー エージェントのセキュリティのプロパティを変更します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されるか、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changeqreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_login**=] **'***job_login***'**  
 用のログイン、[!INCLUDE[msCoName](../../includes/msconame-md.md)]エージェントを実行する Windows アカウントします。 *job_login*は**nvarchar (257)**、既定値は NULL です。  
  
 [ **@job_password**=] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値は NULL です。  
  
 [  **@frompublisher=** ] *frompublisher*  
 プロシージャをパブリッシャー側で実行するかどうかを指定します。 *frompublisher*は bit で、既定値は、 **0**します。 値**1**プロシージャがパブリッシャーのパブリケーション データベースから実行されていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changeqreader_agent**はトランザクション レプリケーションで使用します。  
  
 **sp_changeqreader_agent**キュー リーダー エージェントを実行する Windows アカウントを変更するために使用します。 既存の Windows ログインのパスワードを変更するか、新しい Windows ログインとパスワードを指定できます。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_changeqreader_agent**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addqreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
  
