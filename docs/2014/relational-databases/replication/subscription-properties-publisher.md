---
title: '[サブスクリプションのプロパティ - パブリッシャー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subproperties.publisher.f1
helpviewer_keywords:
- Subscription Properties dialog box
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5213c07fcdf84db3297ae5737d1d8726f4355257
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794444"
---
# <a name="subscription-properties---publisher"></a>[サブスクリプションのプロパティ - パブリッシャー]
  パブリッシャーの **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用すると、プッシュ サブスクリプションのプロパティを表示したり設定したりできます。 プル サブスクリプションのいくつかのプロパティを表示することもできますが、サブスクリプションの **[サブスクリプションのプロパティ]** ダイアログ ボックスではさらに多くのプロパティが表示され、プロパティを変更することができます。  
  
 **[サブスクリプションのプロパティ]** ダイアログ ボックスの各プロパティには説明が含まれています。 プロパティをクリックすると、ダイアログ ボックスの一番下に説明が表示されます。 このトピックではいくつかのプロパティについての追加情報を説明していますが、ほとんどのプロパティはプッシュ サブスクリプションについてのみパブリッシャーで表示されます。 プロパティは次のように分類されます。  
  
-   すべてのサブスクリプションに適用されるプロパティ。  
  
-   トランザクション サブスクリプションに適用されるプロパティ。  
  
-   マージ サブスクリプションに適用されるプロパティ。  
  
 読み取り専用として表示されているオプションの場合、サブスクリプションが作成されている場合にのみ設定できます。 サブスクリプションの新規作成ウィザードで使用することのできないオプションを設定する場合は、サブスクリプションをストアド プロシージャで作成します。 詳細については、「 [Create a Pull Subscription](create-a-pull-subscription.md) 」および「 [Create a Push Subscription](create-a-push-subscription.md)」を参照してください。  
  
## <a name="options-for-all-subscriptions"></a>すべてのサブスクリプションに対するオプション  
 **Security**  
 **[エージェント プロセス アカウント]** 行をクリックしてプロパティ ボタン (**[...]**) をクリックし、ディストリビューション エージェントまたはマージ エージェントがディストリビューターで実行されるアカウントを変更します。 ディストリビューション エージェントまたはマージ エージェントがサブスクライバーへの接続を作成するアカウントを変更するには、 **[サブスクライバー接続]** をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
 各エージェントに必要な権限の詳細については、「 [Replication Agent Security Model](security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="options-for-transactional-subscriptions"></a>トランザクション サブスクリプションに対するオプション  
 **[トランザクションのループを防ぐ]**  
 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを決定します。 このオプションは双方向トランザクション レプリケーションに対して使用します。 詳細については、「 [Bidirectional Transactional Replication](transactional/bidirectional-transactional-replication.md)」を参照してください。  
  
 **[更新可能なサブスクリプション]**  
 サブスクライバーの変更がパブリッシャーにレプリケートされるかどうかを決定します。 変更は、キュー更新または即時更新を使用してレプリケートすることができます。 **[サブスクライバーの更新方法]** オプションでは、どの方法を使用するかを決定します。 詳細については、「 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
## <a name="options-for-merge-subscriptions"></a>マージ サブスクリプションに対するオプション  
 **[パーティション定義 (HOST_NAME)]**  
 パラメーター化されたフィルターを使用するパブリケーションで、マージ レプリケーションは、2 つのシステム関数 (または両方のフィルターが両方の関数を参照している場合) のいずれかをサブスクライバーが受け取るデータを決定する同期中に評価します。**SUSER_SNAME()** または**HOST_NAME()** します。 既定では、**HOST_NAME()** は、マージ エージェントが実行されているコンピューターの名前を返しますが、この値はサブスクリプションの新規作成ウィザードでオーバーライドすることができます。 パラメーター化されたフィルターと **HOST_NAME()** のオーバーライドの詳細については、「[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
 **[サブスクリプションの種類]** と **[優先度]**  
 サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションであるかどうかを表示します (これは、サブスクリプションが作成された後では変更できません)。 サーバー サブスクリプションは、他のサブスクライバーへのデータの再パブリッシュと、競合解決方法の優先度の割り当てができます。  
  
 サブスクリプションの新規作成ウィザードでサーバーのサブスクリプションの種類を選択した場合、サブスクライバーには競合解決方法で使用される優先度が割り当てられます。  
  
 **[競合を対話的に解決する (対話的な解決をサポートするアーティクルに対してのみ適用されます)]**  
 インタラクティブ競合回避モジュールのユーザー インターフェイスを使用して、マージ同期中の競合を回避するかどうかを決定します。 これを行うには、 **[Windows 同期マネージャーを使用]** に **[有効化]** の値を設定する必要があります。 詳細については、「 [Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
