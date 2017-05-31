---
title: "[ログ リーダー エージェントのセキュリティ] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 67f7bfd9eb599250b951f4365d3d6efe6e943a31
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="log-reader-agent-security"></a>[ログ リーダー エージェントのセキュリティ]
  **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスを使用すると、次の指定ができます。  
  
-   ログ リーダー エージェントをディストリビューターで実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウント。 エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。  
  
-   ログ リーダー エージェントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーへの接続を作成するコンテキスト。 接続は、Windows アカウントを借用して作成されるか、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストで作成されます。  
  
    > [!NOTE]  
    >  パブリッシャーおよびディストリビューターが同じコンピューター上にある場合でも、ログ リーダー エージェントはパブリッシャーへの接続を作成します。 ログ リーダー エージェントはディストリビューターへの接続も作成します。これらの接続は必ず、エージェントが実行される Windows アカウントを借用して作成されます。  
  
     Oracle パブリッシャーの場合、ログ リーダー エージェントがパブリッシャーに接続するコンテキストを **[パブリッシャーのプロパティ]** ダイアログ ボックス ( **[ディストリビューターのプロパティ]** ダイアログ ボックスから使用可能) で指定します。 詳細については、「[レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## <a name="options"></a>オプション  
 **Process account**  
 ログ リーダー エージェントをディストリビューターで実行する Windows アカウントを入力します。 指定した Windows アカウントは少なくともディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
 **[パスワード]** と **[パスワードの確認入力]**  
 Windows アカウントのパスワードを入力します。  
  
 **[パブリッシャーに接続]**  
 ログ リーダー エージェントがパブリッシャーに接続するのに **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用する必要があるか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用する必要があるかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
 接続に使用される Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、少なくとも、パブリケーション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
