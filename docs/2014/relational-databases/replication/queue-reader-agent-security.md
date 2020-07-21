---
title: '[キュー リーダー エージェントのセキュリティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22a5e5751184b626ab1af86f01782a42028b5ced
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049079"
---
# <a name="queue-reader-agent-security"></a>[キュー リーダー エージェントのセキュリティ]
  **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスを使用すると、キュー リーダー エージェントを実行したり、ディストリビューターへのローカル接続を行ったりするための [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。 エージェントは、( **[ディストリビューターのプロパティ]** ダイアログ ボックスから呼び出される) **[パブリッシャーのプロパティ]** ダイアログ ボックスで指定されたアカウントを使用してパブリッシャーに接続します。エージェントは、同じコンテキストを使用して、サブスクリプションのディストリビューション エージェントとしてサブスクライバーに接続します。 詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 アカウントは、適切なパスワードが指定された有効なアカウントである必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## <a name="options"></a>オプション  
 **[プロセス アカウント]**  
 ディストリビューターでキュー リーダー エージェントを実行するための Windows アカウントを入力します。 指定した Windows アカウントは少なくともディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
 **[パスワード]** と **[パスワードの確認入力]**  
 Windows アカウントのパスワードを入力します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションでのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](agents/replication-agents-overview.md)   
 [レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)  
  
  
