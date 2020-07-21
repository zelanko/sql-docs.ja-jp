---
title: '&lt;AgentName&gt; エージェント セキュリティ | Microsoft Docs'
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
ms.openlocfilehash: 75d4cccdb867716cf16490b4662edec4d5856fe6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016776"
---
# <a name="ltagentnamegt-agent-security"></a>&lt;AgentName&gt; エージェント セキュリティ
  [ ** \<AgentName> エージェントセキュリティ**] ページでは、ディストリビューションエージェント (トランザクションレプリケーションおよびスナップショットレプリケーションの場合) またはマージエージェント (マージレプリケーションの場合) を実行し、レプリケーショントポロジ内のコンピューターに接続する際に使用するアカウントを指定できます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスまたは **[マージ エージェント セキュリティ]** ダイアログ ボックスにアクセスするには、各サブスクライバーの行でプロパティ ボタン ( **[...]** ) をクリックします。 ダイアログ ボックスの **[ヘルプ]** をクリックすると、エージェントによって使用されるアカウントに必要な権限の詳細を参照できます。  
  
 ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。  
  
 **[サブスクライバーのエージェント]**  
 各サブスクライバーの名前です。  
  
 **[ディストリビューターへの接続]**  
 トランザクション レプリケーションおよびスナップショット レプリケーションに表示されます。 ディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュサブスクリプションの場合、ローカル接続はディストリビューターへの接続であるため、このフィールドには常に、プッシュサブスクリプションの場合は **" \<Domain> \\<login \> ** " または**impersonate ' \<Computer> \\<login \> '** と表示されます。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには次のいずれかが表示されます。 **Use login ' \<Login> '**、 **impersonate ' \<Domain> \\<login \> '** 、または**impersonate ' \<Computer> \\<login \> '**。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
 **[パブリッシャーおよびディストリビューターへの接続]**  
 マージ レプリケーションの場合に表示されます。 パブリッシャーおよびディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュサブスクリプションの場合、ローカル接続はパブリッシャーおよびディストリビューターへの接続であるため、このフィールドには常に、プッシュサブスクリプションの場合は **" \<Domain> \\<login \> ** " または**impersonate ' \<Computer> \\<login \> '** と表示されます。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには次のいずれかが表示されます。 **Use login ' \<Login> '**、 **impersonate ' \<Domain> \\<login \> '** 、または**impersonate ' \<Computer> \\<login \> '**。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
 **[サブスクライバーへの接続]**  
 サブスクライバーに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プルサブスクリプションの場合、ローカル接続はサブスクライバーへの接続であるため、このフィールドには常に、プッシュサブスクリプションの場合は **" \<Domain> \\<login \> ** " または**impersonate ' \<Computer> \\<login \> '** と表示されます。  
  
-   プッシュ サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには次のいずれかが表示されます。 **Use login ' \<Login> '**、 **impersonate ' \<Domain> \\<login \> '** 、または**impersonate ' \<Computer> \\<login \> '**。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
 [レプリケーションでのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)   
 [SQL Server レプリケーションのセキュリティ](security/view-and-modify-replication-security-settings.md)  
  
  
