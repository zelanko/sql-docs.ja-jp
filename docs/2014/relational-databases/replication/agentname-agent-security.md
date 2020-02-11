---
title: "\n  &lt;AgentName&gt; エージェント セキュリティ | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d77f8d6acb449bc9aa2298dbcba9782fd7bc07e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62722054"
---
# <a name="ltagentnamegt-agent-security"></a>
  &lt;AgentName&gt; エージェント セキュリティ
  [ ** \<Agentname> エージェントのセキュリティ**] ページでは、ディストリビューションエージェント (トランザクションレプリケーションおよびスナップショットレプリケーションの場合) またはマージエージェント (マージレプリケーションの場合) を実行し、レプリケーショントポロジ内のコンピューターに接続する際に使用するアカウントを指定できます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 
  **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスまたは **[マージ エージェント セキュリティ]** ダイアログ ボックスにアクセスするには、各サブスクライバーの行でプロパティ ボタン ( **[...]** ) をクリックします。 ダイアログ ボックスの **[ヘルプ]** をクリックすると、エージェントによって使用されるアカウントに必要な権限の詳細を参照できます。  
  
 ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。  
  
 **サブスクライバーのエージェント**  
 各サブスクライバーの名前です。  
  
 **ディストリビューターへの接続**  
 トランザクション レプリケーションおよびスナップショット レプリケーションに表示されます。 ディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュ サブスクリプションの場合、ローカル接続はディストリビューターへの接続となるため、フィールドには常に **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** が表示されます。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、**[ログイン '\<Login>' を使用する]**、**['\<Domain>\\<Login\>' の権限を借用する]**、**['\<Computer>\\<Login\>' の権限を借用する]** のうちの 1 つが表示されます。 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
 **パブリッシャー & ディストリビューターへの接続**  
 マージ レプリケーションの場合に表示されます。 パブリッシャーおよびディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュ サブスクリプションの場合、ローカル接続はパブリッシャーおよびディストリビューターへの接続となるため、フィールドには常に **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** が表示されます。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、**[ログイン '\<Login>' を使用する]**、**['\<Domain>\\<Login\>' の権限を借用する]**、**['\<Computer>\\<Login\>' の権限を借用する]** のうちの 1 つが表示されます。 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
 **サブスクライバーへの接続**  
 サブスクライバーに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プル サブスクリプションの場合、ローカル接続はサブスクライバーへの接続となるため、フィールドには常に **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** が表示されます。  
  
-   プッシュ サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、**[ログイン '\<Login>' を使用する]**、**['\<Domain>\\<Login\>' の権限を借用する]**、**['\<Computer>\\<Login\>' の権限を借用する]** のうちの 1 つが表示されます。 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
 [レプリケーションでのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [レプリケーションエージェントのセキュリティモデル](security/replication-agent-security-model.md)   
 [SQL Server レプリケーションのセキュリティ](security/view-and-modify-replication-security-settings.md)  
  
  
