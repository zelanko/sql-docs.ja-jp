---
title: "[サブスクリプションのプロパティ - パブリッシャー] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subproperties.publisher.f1"
helpviewer_keywords: 
  - "[サブスクリプションのプロパティ] ダイアログ ボックス"
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# [サブスクリプションのプロパティ - パブリッシャー]
   **サブスクリプションのプロパティ** 、パブリッシャー側でのダイアログ ボックスでは、表示し、プッシュ サブスクリプションのプロパティを設定することができます。 プル サブスクリプションの場合は、いくつかのプロパティを表示することもできますが、 **サブスクリプション プロパティ** 、サブスクライバーでのダイアログ ボックスが追加のプロパティを表示し、により、プロパティを変更します。  
  
 内の各プロパティ、 **サブスクリプションのプロパティ** ] ダイアログ ボックスに説明が含まれます。 プロパティをクリックすると、ダイアログ ボックスの一番下に説明が表示されます。 このトピックではいくつかのプロパティについての追加情報を説明していますが、ほとんどのプロパティはプッシュ サブスクリプションについてのみパブリッシャーで表示されます。 プロパティは次のように分類されます。  
  
-   すべてのサブスクリプションに適用されるプロパティ。  
  
-   トランザクション サブスクリプションに適用されるプロパティ。  
  
-   マージ サブスクリプションに適用されるプロパティ。  
  
 読み取り専用として表示されているオプションの場合、サブスクリプションが作成されている場合にのみ設定できます。 サブスクリプションの新規作成ウィザードで使用することのできないオプションを設定する場合は、サブスクリプションをストアド プロシージャで作成します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 」および「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」を参照してください。  
  
## すべてのサブスクリプションに対するオプション  
 **セキュリティ**  
 クリックして、 **エージェント プロセス アカウント** 行を [プロパティ] ボタンをクリックして (**...**)、ディストリビューション エージェントまたはマージ エージェントをディストリビューターで実行するアカウントを変更します。 ディストリビューション エージェントまたはマージ エージェントが接続を作成し、サブスクライバーにアカウントを変更する] をクリックして **サブスクライバー接続**, 、[プロパティ] ボタンをクリックして (**...**)。  
  
 各エージェントに必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
## トランザクション サブスクリプションに対するオプション  
 **[トランザクションのループを防ぐ]**  
 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを決定します。 このオプションは双方向トランザクション レプリケーションに対して使用します。 詳細については、次を参照してください。 [双方向トランザクション レプリケーション](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)します。  
  
 **[更新可能なサブスクリプション]**  
 サブスクライバーの変更がパブリッシャーにレプリケートされるかどうかを決定します。 変更は、キュー更新または即時更新を使用してレプリケートすることができます。 オプション **サブスクライバーの更新方法** メソッドを使用して決定します。 詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
## マージ サブスクリプションに対するオプション  
 **[パーティション定義 (HOST_NAME)]**  
 マージ レプリケーションの 2 つのシステム関数 (または両方のフィルターがどちらの関数を参照している場合) のいずれかの評価をサブスクライバーが受け取るデータを特定の同期中に使用するパブリケーションにパラメーター化されたフィルターの: **SUSER_SNAME()** または **HOST_NAME()**します。 既定では、 **HOST_NAME()** 、マージ エージェントが実行されているがサブスクリプションの新規作成ウィザードでこの値を上書きするコンピューターの名前を返します。 詳細については、パラメーター化フィルターをオーバーライドする **HOST_NAME()**, を参照してください [パラメーター化された行フィルター](../../relational-databases/replication/merge/parameterized-row-filters.md)します。  
  
 **サブスクリプションの種類** と **優先順位**  
 サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションであるかどうかを表示します (これは、サブスクリプションが作成された後では変更できません)。 サーバー サブスクリプションは、他のサブスクライバーへのデータの再パブリッシュと、競合解決方法の優先度の割り当てができます。  
  
 サブスクリプションの新規作成ウィザードでサーバーのサブスクリプションの種類を選択した場合、サブスクライバーには競合解決方法で使用される優先度が割り当てられます。  
  
 **[競合を対話的に解決する (対話的な解決をサポートするアーティクルに対してのみ適用されます)]**  
 インタラクティブ競合回避モジュールのユーザー インターフェイスを使用して、マージ同期中の競合を回避するかどうかを決定します。 値が必要です **を有効にする** の **Windows 同期マネージャーを使用して**します。 詳細については、「 [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md)」を参照してください。  
  
## 参照  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  