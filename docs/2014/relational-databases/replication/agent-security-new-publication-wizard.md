---
title: '[エージェント セキュリティ] (パブリケーションの新規作成ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 555aa4e49887000354e5d31ff5d039a5f0ac75eb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63259159"
---
# <a name="agent-security-new-publication-wizard"></a>[エージェント セキュリティ] (パブリケーションの新規作成ウィザード)
  
  **[エージェント セキュリティ]** ページを使用すると、次のエージェントを実行したり、レプリケーション トポロジ内のコンピューターに接続したりする際のアカウントを指定できます。  
  
-   すべてのパブリケーションに対応する、スナップショット エージェント。  
  
-   すべてのトランザクション パブリケーションに対応する、ログ リーダー エージェント。  
  
-   更新可能なサブスクリプションを許容するトランザクション パブリケーションに対応する、キュー リーダー エージェント。 
  [パブリケーションの種類][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで **[更新可能なサブスクリプションを含むトランザクション パブリケーション]** を指定した場合、使用する更新可能なサブスクリプションの種類に関係なく、このエージェント向けの **** エージェント ジョブが作成されます。 更新可能なサブスクリプションの詳細については、「 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
 エージェントで必要とされる権限と、レプリケーションのセキュリティに関する推奨事項については、「 [Replication Agent Security Model](security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](security/replication-security-best-practices.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **スナップショット エージェント**  
 すべてのパブリケーションで表示されます。 
  **[セキュリティ設定]** をクリックすると、 **[スナップショット エージェントのセキュリティ]** ダイアログ ボックスでセキュリティ設定を指定できます。  
  
 スナップショット エージェントで使用されるアカウントに必要な権限の詳細については、 **[スナップショット エージェントのセキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックしてください。  
  
 **ログ リーダー エージェント**  
 すべてのトランザクション パブリケーションで表示されます。 
  **[セキュリティ設定]** をクリックすると、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスでセキュリティ設定を指定できます。  
  
 ログ リーダー エージェントで使用されるアカウントに必要な権限の詳細については、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックしてください。  
  
> [!NOTE]  
>  トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。 データベースにトランザクション パブリケーションが既に存在している場合、セキュリティ設定は読み取り専用になります。 セキュリティ設定は **[パブリケーションのプロパティ]** ダイアログ ボックスを使用して変更できますが、この変更はデータベース内のすべてのトランザクション パブリケーションに反映されます。  
  
 **キュー リーダー エージェント**  
 更新可能なサブスクリプションを許容するトランザクション パブリケーションで表示されます。 
  **[セキュリティ設定]** をクリックすると、 **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスでセキュリティ設定を指定できます。 このウィザードが完了すると、キュー更新サブスクリプションを作成するかどうかには関係なく、キュー リーダー エージェント ジョブが作成されます。 キュー更新サブスクリプションを作成しない場合には、このジョブを無効にできます。 ジョブ ( *[\<Publisher>] という形式の名前) を右クリックし\<ます。整数>*)[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント**ジョブ**] フォルダーで、[**無効**] をクリックします。  
  
 キュー リーダー エージェントで使用されるアカウントに必要な権限の詳細については、 **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックしてください。  
  
> [!NOTE]  
>  ディストリビューション データベース (および、それを使用するすべてのパブリッシャー) には、それぞれに対応するキュー リーダー エージェントが 1 つずつ存在します。 指定されたディストリビューション データベースを使用するパブリッシャーのいずれかに、キュー更新サブスクリプションを許容するトランザクション パブリケーションが既に存在する場合、セキュリティ設定は読み取り専用になります。 
  **[ディストリビューターのプロパティ]** ダイアログ ボックスで、キュー リーダー エージェントの実行と接続に使用されるアカウントを変更できますが、この変更はディストリビューション データベースを使用するすべてのパブリッシャーのパブリケーションに反映されます。  
  
## <a name="see-also"></a>参照  
 [パブリケーションを作成する](publish/create-a-publication.md)   
 [トランザクションパブリケーションに対する更新可能なサブスクリプションの作成](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)   
 [パブリケーションのプロパティの表示および変更](publish/view-and-modify-publication-properties.md)   
 [レプリケーションでのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [データとデータベースオブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)   
 [レプリケーションエージェントの概要](agents/replication-agents-overview.md)  
  
  
