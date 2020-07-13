---
title: 孤立ユーザーのトラブルシューティング (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5df714d818949b921ff2236e50d58913eab0e0db
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062563"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a>孤立ユーザーのトラブルシューティング (SQL Server)
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにログインするには、有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインがプリンシパルに提供されている必要があります。 このログインは、プリンシパルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できるかどうかを確認する認証プロセスで使用されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーインスタンス上のログインは、 **server_principals**カタログビューおよび**sys.sysログイン**互換性ビューに表示されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップされているデータベース ユーザーを使用して個々のデータベースにアクセスします。 このルールには次の 2 つの例外があります。  
  
-   guest アカウント  
  
     このアカウントがデータベースで有効になっていると、データベース ユーザーにマップされていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインはゲスト ユーザーとしてデータベースにアクセスできます。  
  
-   Microsoft Windows グループのメンバー  
  
     Windows ユーザーから作成した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、Windows ユーザーが属しているグループがデータベースのユーザーである場合にデータベースにアクセスできます。  
  
 データベース ユーザーへの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのマップに関する情報は、データベース内に格納されます。 これには、データベース ユーザーの名前および対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの SID が含まれます。 データベース内での承認には、このデータベース ユーザーの権限を使用します。  
  
 対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが未定義のデータベース ユーザー、またはサーバー インスタンスで適切に定義されていないデータベース ユーザーは、インスタンスにログインできません。 このようなユーザーは、そのサーバー インスタンスのデータベースの *孤立ユーザー* と呼ばれます。 データベース ユーザーは、対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが削除された場合に孤立状態になることがあります。 また、データベースを復元したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにアタッチした場合も、孤立状態になることがあります。 孤立状態は、データベース ユーザーが新しいサーバー インスタンスに存在しない SID にマップされると発生する場合があります。  
  
> [!NOTE]  
>  ログインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] そのデータベースで**guest**が有効になっていない限り、対応するデータベースユーザーがないデータベースにはアクセスできません。 データベースユーザーアカウントの作成の詳細については、「 [CREATE user &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。  
  
## <a name="to-detect-orphaned-users"></a>孤立ユーザーを検出するには  
 孤立ユーザーを検出するには、次の Transact-SQL ステートメントを実行します。  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 現在のデータベース内で、どの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにもリンクされていないユーザーとそのセキュリティ識別子 (SID) が出力されます。 詳細については、「 [sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)」を参照してください。  
  
> [!NOTE]  
>  **sp_change_users_login**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows から作成されたログインでは使用できません。  
  
## <a name="to-resolve-an-orphaned-user"></a>孤立ユーザーを解決するには  
 孤立ユーザーを解決するには、次の手順を実行します。  
  
1.  次のコマンドは、 *<login_name>* で指定されたサーバーログインアカウントを、 *<database_user>* で指定されたデータベースユーザーとエディットコンティニュします。  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     詳細については、「 [sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)」を参照してください。  
  
2.  前の手順のコードを実行すると、ユーザーがデータベースにアクセスできるようになります。 次のように、ユーザーは**sp_password**ストアドプロシージャを使用して、 *<login_name>* ログインアカウントのパスワードを変更できます。  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  ALTER ANY LOGIN 権限を持つログインだけが、他のユーザーのログイン パスワードを変更できます。 ただし、 **sysadmin** ロール メンバーのパスワードを変更できるのは、 **sysadmin** ロールのメンバーだけです。  
  
    > [!NOTE]  
    >  **sp_password**は、Windows アカウントには使用できません [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。 Windows ネットワーク アカウントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するユーザーは Windows によって認証されるので、このようなユーザーのパスワードは Windows でしか変更できません。  
  
     詳細については、「 [sp_password &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ユーザー &#40;Transact-sql&#41;の作成](/sql/t-sql/statements/create-user-transact-sql)   
 [Transact-sql&#41;&#40;ログインの作成](/sql/t-sql/statements/create-login-transact-sql)   
 [sp_change_users_login &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)   
 [sp_addlogin &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [sp_grantlogin &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [sp_password &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)   
 [sys.sysユーザー &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)   
 [Transact-sql&#41;&#40;のログインのsys.sys](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
