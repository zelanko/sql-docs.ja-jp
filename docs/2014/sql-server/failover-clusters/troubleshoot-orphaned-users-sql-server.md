---
title: 孤立ユーザーのトラブルシューティング (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97bef9ba2298766539d6b852bb41bb89c716c829
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072729"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a>孤立ユーザーのトラブルシューティング (SQL Server)
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにログインするには、有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインがプリンシパルに提供されている必要があります。 このログインは、プリンシパルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できるかどうかを確認する認証プロセスで使用されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバー インスタンス上のログインは、 **sys.server_principals**カタログ ビューおよび**sys.syslogins**互換性ビューです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップされているデータベース ユーザーを使用して個々のデータベースにアクセスします。 このルールには次の 2 つの例外があります。  
  
-   guest アカウント  
  
     このアカウントがデータベースで有効になっていると、データベース ユーザーにマップされていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインはゲスト ユーザーとしてデータベースにアクセスできます。  
  
-   Microsoft Windows グループのメンバー  
  
     Windows ユーザーから作成した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、Windows ユーザーが属しているグループがデータベースのユーザーである場合にデータベースにアクセスできます。  
  
 データベース ユーザーへの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのマップに関する情報は、データベース内に格納されます。 これには、データベース ユーザーの名前および対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの SID が含まれます。 データベース内での承認には、このデータベース ユーザーの権限を使用します。  
  
 対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが未定義のデータベース ユーザー、またはサーバー インスタンスで適切に定義されていないデータベース ユーザーは、インスタンスにログインできません。 このようなユーザーは、そのサーバー インスタンスのデータベースの *孤立ユーザー* と呼ばれます。 データベース ユーザーは、対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが削除された場合に孤立状態になることがあります。 また、データベースを復元したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにアタッチした場合も、孤立状態になることがあります。 孤立状態は、データベース ユーザーが新しいサーバー インスタンスに存在しない SID にマップされると発生する場合があります。  
  
> [!NOTE]  
>  A[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン順番がない、対応するデータベース ユーザーしない限り、データベースにアクセスできない**ゲスト**そのデータベースで有効にします。 データベース ユーザー アカウントを作成する方法の詳細については、次を参照してください。 [CREATE USER &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)です。  
  
## <a name="to-detect-orphaned-users"></a>孤立ユーザーを検出するには  
 孤立ユーザーを検出するには、次の Transact-SQL ステートメントを実行します。  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 現在のデータベース内で、どの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにもリンクされていないユーザーとそのセキュリティ識別子 (SID) が出力されます。 詳細については、次を参照してください。 [sp_change_users_login &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)です。  
  
> [!NOTE]  
>  **sp_change_users_login**では使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows から作成されたログインします。  
  
## <a name="to-resolve-an-orphaned-user"></a>孤立ユーザーを解決するには  
 孤立ユーザーを解決するには、次の手順を実行します。  
  
1.  次のコマンドで指定されたサーバーのログイン アカウントを再リンク *< login_name >* で指定されたデータベース ユーザーに *< database_user >* です。  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     詳細については、次を参照してください。 [sp_change_users_login &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)です。  
  
2.  前の手順のコードを実行すると、ユーザーがデータベースにアクセスできるようになります。 ユーザーは、のパスワードを変更できる、 *< login_name >* ログイン アカウントを使用して、 **sp_password**ストアド プロシージャを次のようにします。  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  ALTER ANY LOGIN 権限を持つログインだけが、他のユーザーのログイン パスワードを変更できます。 ただし、 **sysadmin** ロール メンバーのパスワードを変更できるのは、 **sysadmin** ロールのメンバーだけです。  
  
    > [!NOTE]  
    >  **sp_password**は使用できません[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows アカウントです。 Windows ネットワーク アカウントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するユーザーは Windows によって認証されるので、このようなユーザーのパスワードは Windows でしか変更できません。  
  
     詳細については、次を参照してください。 [sp_password &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)です。  
  
## <a name="see-also"></a>参照  
 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)   
 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)   
 [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)   
 [sys.syslogins &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
