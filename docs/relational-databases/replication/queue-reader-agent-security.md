---
title: "[キュー リーダー エージェントのセキュリティ] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.security.QRA.f1
helpviewer_keywords: Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
caps.latest.revision: "21"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79c2a826056a05b5a2e35806f5b45cf44e95f609
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="queue-reader-agent-security"></a>[キュー リーダー エージェントのセキュリティ]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスを使用すると、キュー リーダー エージェントを実行したり、ディストリビューターへのローカル接続を行ったりするための [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。 エージェントは、( **[ディストリビューターのプロパティ]** ダイアログ ボックスから呼び出される) **[パブリッシャーのプロパティ]** ダイアログ ボックスで指定されたアカウントを使用してパブリッシャーに接続します。エージェントは、同じコンテキストを使用して、サブスクリプションのディストリビューション エージェントとしてサブスクライバーに接続します。 詳細については、「[レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 アカウントは、適切なパスワードが指定された有効なアカウントである必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## <a name="options"></a>および  
 **[プロセス アカウント]**  
 ディストリビューターでキュー リーダー エージェントを実行するための Windows アカウントを入力します。 指定した Windows アカウントは少なくともディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
 **[パスワード]** と **[パスワードの確認入力]**  
 Windows アカウントのパスワードを入力します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
