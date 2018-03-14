---
title: "[サブスクリプションのプロパティ - パブリッシャー] | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.subproperties.publisher.f1
helpviewer_keywords:
- Subscription Properties dialog box
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbf57cb3f73b3f59130afd10492b248a16a9cf5f
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="subscription-properties---publisher"></a>[サブスクリプションのプロパティ - パブリッシャー]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  パブリッシャーの **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用すると、プッシュ サブスクリプションのプロパティを表示したり設定したりできます。 プル サブスクリプションのいくつかのプロパティを表示することもできますが、サブスクリプションの **[サブスクリプションのプロパティ]** ダイアログ ボックスではさらに多くのプロパティが表示され、プロパティを変更することができます。  
  
 **[サブスクリプションのプロパティ]** ダイアログ ボックスの各プロパティには説明が含まれています。 プロパティをクリックすると、ダイアログ ボックスの一番下に説明が表示されます。 このトピックではいくつかのプロパティについての追加情報を説明していますが、ほとんどのプロパティはプッシュ サブスクリプションについてのみパブリッシャーで表示されます。 プロパティは次のように分類されます。  
  
-   すべてのサブスクリプションに適用されるプロパティ。  
  
-   トランザクション サブスクリプションに適用されるプロパティ。  
  
-   マージ サブスクリプションに適用されるプロパティ。  
  
 読み取り専用として表示されているオプションの場合、サブスクリプションが作成されている場合にのみ設定できます。 サブスクリプションの新規作成ウィザードで使用することのできないオプションを設定する場合は、サブスクリプションをストアド プロシージャで作成します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 」および「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」を参照してください。  
  
## <a name="options-for-all-subscriptions"></a>すべてのサブスクリプションに対するオプション  
 **Security**  
 **[エージェント プロセス アカウント]** 行をクリックしてプロパティ ボタン (**[...]**) をクリックし、ディストリビューション エージェントまたはマージ エージェントがディストリビューターで実行されるアカウントを変更します。 ディストリビューション エージェントまたはマージ エージェントがサブスクライバーへの接続を作成するアカウントを変更するには、 **[サブスクライバー接続]**をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
 各エージェントに必要な権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="options-for-transactional-subscriptions"></a>トランザクション サブスクリプションに対するオプション  
 **[トランザクションのループを防ぐ]**  
 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを決定します。 このオプションは双方向トランザクション レプリケーションに対して使用します。 詳細については、「 [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)」を参照してください。  
  
 **[更新可能なサブスクリプション]**  
 サブスクライバーの変更がパブリッシャーにレプリケートされるかどうかを決定します。 変更は、キュー更新または即時更新を使用してレプリケートすることができます。 **[サブスクライバーの更新方法]** オプションでは、どの方法を使用するかを決定します。 詳細については、「 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
## <a name="options-for-merge-subscriptions"></a>マージ サブスクリプションに対するオプション  
 **[パーティション定義 (HOST_NAME)]**  
 パラメーター化されたフィルターを使用するパブリケーションの場合、マージ レプリケーションでは、同期化中に 2 つのシステム関数、 **SUSER_SNAME()** または **HOST_NAME()**のうちの 1 つ (フィルターが両方の関数を参照する場合は両方の関数) を評価して、サブスクライバーが受け取る必要のあるデータを決定します。 既定では、 **HOST_NAME()** は、マージ エージェントが実行されているコンピューターの名前を返しますが、この値はサブスクリプションの新規作成ウィザードで上書きすることができます。 パラメーター化されたフィルターと **HOST_NAME()**の上書きの詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
 **[サブスクリプションの種類]** と **[優先度]**  
 サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションであるかどうかを表示します (これは、サブスクリプションが作成された後では変更できません)。 サーバー サブスクリプションは、他のサブスクライバーへのデータの再パブリッシュと、競合解決方法の優先度の割り当てができます。  
  
 サブスクリプションの新規作成ウィザードでサーバーのサブスクリプションの種類を選択した場合、サブスクライバーには競合解決方法で使用される優先度が割り当てられます。  
  
 **[競合を対話的に解決する (対話的な解決をサポートするアーティクルに対してのみ適用されます)]**  
 インタラクティブ競合回避モジュールのユーザー インターフェイスを使用して、マージ同期中の競合を回避するかどうかを決定します。 これを行うには、 **[Windows 同期マネージャーを使用]** に **[有効化]**の値を設定する必要があります。 詳細については、「 [Interactive Conflict Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
