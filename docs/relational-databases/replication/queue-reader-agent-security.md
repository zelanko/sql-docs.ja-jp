---
title: "[キュー リーダー エージェントのセキュリティ] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.security.QRA.f1"
helpviewer_keywords: 
  - "[キュー リーダー エージェントのセキュリティ] ダイアログ ボックス"
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [キュー リーダー エージェントのセキュリティ]
   **キュー リーダー エージェントのセキュリティ** ] ダイアログ ボックスでは、指定することができます、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントをキュー リーダー エージェントが実行され、ディストリビューターへのローカル接続を作成します。 エージェントで指定されたアカウントを使用してパブリッシャーに接続、 **パブリッシャーのプロパティ** ] ダイアログ ボックス (から利用可能な **ディストリビューターのプロパティ** ] ダイアログ ボックス) は、エージェント、ディストリビューション エージェントと同じコンテキストを使用して、サブスクリプションのサブスクライバーに接続します。 詳細については、次を参照してください。 [ビューとレプリケーションのセキュリティ設定の変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)です。  
  
 アカウントは、適切なパスワードが指定された有効なアカウントである必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## オプション  
 **[プロセス アカウント]**  
 ディストリビューターでキュー リーダー エージェントを実行するための Windows アカウントを入力します。 最小値にする必要があります。 を指定する Windows アカウントのメンバーである、 **db_owner** ディストリビューション データベースの固定データベース ロール。  
  
 **パスワード** と **パスワードの確認入力**  
 Windows アカウントのパスワードを入力します。  
  
## 参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  