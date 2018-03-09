---
title: "sp_changereplicationserverpasswords (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fcd1cbfd5532703196e47d06f920ef7cfa81f019
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spchangereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  保存されたパスワードを変更、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントまたは[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション トポロジ内のサーバーに接続するときに、レプリケーション エージェントによって使用されるログインです。 通常は、サーバーで実行中のエージェントがすべて同じログインまたはアカウントを使用している場合でも、個々のエージェントごとにパスワードを変更する必要があります。 このストアド プロシージャにより、サーバーで実行中のすべてのレプリケーション エージェントが使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインまたは Windows アカウントのすべてのインスタンスに対するパスワードを変更することができます。 このストアド プロシージャは、レプリケーション トポロジ内の任意のサーバー側で master データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@login_type**  =] *login_type*  
 与えられた資格情報の認証の種類を指定します。 *login_type*は**tinyint**、既定値はありません。  
  
 **1** = Windows 統合認証  
  
 **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証  
  
 [  **@login**  =] **'***ログイン***'**  
 Windows アカウントの名前を指定または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインを変更します。 *ログイン*は**nvarchar (257)**、既定値はありません  
  
 [  **@password**  =] **'***パスワード***'**  
 新しいパスワードを格納する、指定された*ログイン*です。 *パスワード*は**sysname**、既定値はありません。  
  
> [!NOTE]  
>  レプリケーション パスワードを変更したら、そのパスワードを使用する各エージェントを停止して再起動し、エージェントに対して変更を反映させる必要があります。  
  
 [  **@server**  =] **'***サーバー***'**  
 保存パスワードを変更するサーバー接続を指定します。 *サーバー*は**sysname**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**ディストリビューター**|ディストリビューターへのすべてのエージェント接続です。|  
|**パブリッシャー**|パブリッシャーへのすべてのエージェント接続です。|  
|**サブスクライバー**|サブスクライバーへのすべてのエージェント接続です。|  
|**%**(既定値)|レプリケーション トポロジ内のすべてのサーバーへのすべてのエージェント接続です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changereplicationserverpasswords**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_changereplicationserverpasswords**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
