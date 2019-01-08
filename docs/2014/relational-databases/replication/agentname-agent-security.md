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
manager: craigg
ms.openlocfilehash: 25dc706689ec136a5423de8051fecd3c6071d5bc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762384"
---
# <a name="ltagentnamegt-agent-security"></a>&lt;AgentName&gt; エージェント セキュリティ
  **[\<AgentName> エージェント セキュリティ]** ページを使用すると、ディストリビューション エージェント (トランザクション レプリケーションおよびスナップショット レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) が実行されるアカウントを指定し、レプリケーション トポロジ内のコンピューターへの接続を作成することができます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスまたは **[マージ エージェント セキュリティ]** ダイアログ ボックスにアクセスするには、各サブスクライバーの行でプロパティ ボタン ( **[...]** ) をクリックします。 ダイアログ ボックスの **[ヘルプ]** をクリックすると、エージェントによって使用されるアカウントに必要な権限の詳細を参照できます。  
  
 ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。  
  
 **[サブスクライバーのエージェント]**  
 各サブスクライバーの名前です。  
  
 **[ディストリビューターへの接続]**  
 トランザクション レプリケーションおよびスナップショット レプリケーションに表示されます。 ディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュ サブスクリプションの場合、ローカル接続は、ディストリビューターへの接続をこのフィールドは常に表示されます。**Impersonate '\<ドメイン >\\< ログイン\>'** または**Impersonate '\<コンピューター >\\< ログイン\>'** プッシュサブスクリプション。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、次のいずれかが表示されます。**ログインを使用 '\<Login >'**、 **Impersonate'\<ドメイン >\\< ログイン\>'** または**Impersonate'\<コンピューター >\\< ログイン\>'** します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
 **[パブリッシャーおよびディストリビューターへの接続]**  
 マージ レプリケーションの場合に表示されます。 パブリッシャーおよびディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュ サブスクリプションでは、ローカルの接続は、このフィールドは常に表示するためにパブリッシャーおよびディストリビューターへの接続は。**Impersonate '\<ドメイン >\\< ログイン\>'** または**Impersonate '\<コンピューター >\\< ログイン\>'** プッシュサブスクリプション。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、次のいずれかが表示されます。**ログインを使用 '\<Login >'**、 **Impersonate'\<ドメイン >\\< ログイン\>'** または**Impersonate'\<コンピューター >\\< ログイン\>'** します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
 **[サブスクライバーへの接続]**  
 サブスクライバーに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プル サブスクリプションの場合は、ローカルの接続は、このフィールドは常に表示するために、サブスクライバーへの接続は。**Impersonate '\<ドメイン >\\< ログイン\>'** または**Impersonate '\<コンピューター >\\< ログイン\>'** プッシュサブスクリプション。  
  
-   プッシュ サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、次のいずれかが表示されます。**ログインを使用 '\<Login >'**、 **Impersonate'\<ドメイン >\\< ログイン\>'** または**Impersonate'\<コンピューター >\\< ログイン\>'** します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
 [レプリケーションのログインとパスワードの管理](security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)   
 [セキュリティと保護 &#40;レプリケーション&#41;](security/security-and-protection-replication.md)  
  
  
