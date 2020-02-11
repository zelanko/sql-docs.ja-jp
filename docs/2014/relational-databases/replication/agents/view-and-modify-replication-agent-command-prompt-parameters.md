---
title: レプリケーションエージェントコマンドプロンプトパラメーターの表示および変更 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6e4327de10dd03b3ff8cf034ade64391d18d2a86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63192893"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a>レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する (SQL Server Management Studio)
  レプリケーション エージェントは、コマンド ライン パラメーターを使用できる実行可能ファイルです。 既定では、エージェントは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ジョブ ステップで実行されるため、これらのパラメーターは **[ジョブのプロパティ - \<Job>]** ダイアログ ボックスを使用して表示および変更できます。 このダイアログ ボックスは、 **の** [ジョブ] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] フォルダーおよびレプリケーション モニター内の **[エージェント]** タブからアクセスできます。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。  
  
> [!NOTE]  
>  エージェント パラメーターの変更は、エージェントの次回起動時に反映されます。 エージェントを継続して実行している場合は、そのエージェントを停止して再起動する必要があります。  
  
 パラメーターは直接変更することもできますが、エージェント プロファイルを使用して変更する方が一般的です。 詳細については、「 [Replication Agent Profiles](replication-agent-profiles.md)」を参照してください。  
  
 
  **[ジョブ]** フォルダーからエージェント ジョブにアクセスする場合は、次の表を使用して、各エージェントで使用できるエージェント ジョブ名とパラメーターを決定してください。  
  
|エージェント|ジョブ名|パラメーターの一覧の参照先|  
|-----------|--------------|------------------------------------|  
|スナップショット エージェント|**\<パブリッシャー>-\<\<パブリケーションデータベース>-パブリケーション>-\<整数>**|[レプリケーションスナップショットエージェント](replication-snapshot-agent.md)|  
|マージ パブリケーション パーティションに対するスナップショット エージェント|**Dyn_\<パブリッシャー>-\<\<パブリケーションデータベース>-パブリケーション>-\<GUID>**|[レプリケーションスナップショットエージェント](replication-snapshot-agent.md)|  
|ログ リーダー エージェント (Log Reader Agent)|**\<パブリッシャー>-\<パブリケーションデータベース>-\<整数>**|[レプリケーション ログ リーダー エージェント](replication-log-reader-agent.md)|  
|プル サブスクリプションに対するマージ エージェント|**\<パブリッシャー>-\<\<パブリケーションデータベース>-パブリケーション>-\<サブスクライバー>-\<subscriptiondatabase>-\<整数>**|[レプリケーションマージエージェント](replication-merge-agent.md)|  
|プッシュ サブスクリプションに対するマージ エージェント|**\<パブリッシャー>-\<\<パブリケーションデータベース>-パブリケーション>-\<サブスクライバー>-\<整数>**|[レプリケーションマージエージェント](replication-merge-agent.md)|  
|プッシュ サブスクリプションに対するディストリビューション エージェント|**\<\<\<パブリッシャー>-パブリケーションデータベース>-パブリケーション>-サブスクライバー>-\<整数>1 \<** <sup></sup>|[レプリケーション ディストリビューション エージェント](replication-distribution-agent.md)|  
|プル サブスクリプションに対するディストリビューション エージェント|**\<\<\<\<パブリッシャー>-\<パブリケーションデータベース>>-サブスクライバー>-subscriptiondatabase>-GUID>2 \<** <sup></sup>|[レプリケーション ディストリビューション エージェント](replication-distribution-agent.md)|  
|SQL Server 以外のサブスクライバーへのプッシュ サブスクリプションに対するディストリビューション エージェント|**\<パブリッシャー>-\<\<パブリケーションデータベース>-パブリケーション>-\<サブスクライバー>-\<整数>**|[レプリケーション ディストリビューション エージェント](replication-distribution-agent.md)|  
|キュー リーダー エージェント (Queue Reader Agent)|**[\<ディストリビューター>]。\<整数>**|[レプリケーションキューリーダーエージェント](replication-queue-reader-agent.md)|  
  
 <sup>1</sup> Oracle パブリケーションに対するプッシュサブスクリプションの場合は** \<\<** 、パブリッシャー ** \<>-\<パブリケーションデータベース**ではなくパブリッシャーの>>>  
  
 <sup>2</sup> Oracle パブリケーションに対するプルサブスクリプションの場合は** \<\<** 、パブリッシャー ** \<>\<-パブリケーションデータベース**ではなく、パブリッシャーの>> になり>  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a>Management Studio からレプリケーション エージェント コマンド ライン パラメーターを表示または変更するには  
  
1.  
  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]で適切なコンピューターに接続して、サーバー ノードを展開します。  
  
    -   プル サブスクリプションに対するディストリビューション エージェントとマージ エージェントの場合は、サブスクライバーに接続します。  
  
    -   その他のエージェントの場合は、ディストリビューターに接続します。  
  
2.  
  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  
  **[ジョブのプロパティ - **Job>]** ダイアログ ボックスの \<[ステップ]** ページで、ステップ **[エージェントを実行します]** を選択し、**[編集]** をクリックします。  
  
5.  
  **[ジョブ ステップのプロパティ - エージェントを実行します]** ダイアログ ボックスで、 **[コマンド]** フィールドを編集します。  
  
6.  両方のダイアログ ボックスで **[OK]** をクリックします。  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a>レプリケーション モニターからディストリビューション エージェントとマージ エージェントのコマンド ライン パラメーターを表示および変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  
  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。  
  
4.  [ **Subscription \< SubscriptionName>** ] ウィンドウで、[ **Action**] をクリックし、[ ** \<agentname> Job Properties**] をクリックします。  
  
5.  
  **[ジョブのプロパティ - **Job>]** ダイアログ ボックスの \<[ステップ]** ページで、ステップ **[エージェントを実行します]** を選択し、**[編集]** をクリックします。  
  
6.  
  **[ジョブ ステップのプロパティ - エージェントを実行します]** ダイアログ ボックスで、 **[コマンド]** フィールドを編集します。  
  
7.  両方のダイアログ ボックスで **[OK]** をクリックします。  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a>レプリケーション モニターからスナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントのコマンド ライン パラメーターを表示および変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  
  **[エージェント]** タブをクリックします。  
  
3.  グリッド内のエージェントを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  
  **[ジョブのプロパティ - **Job>]** ダイアログ ボックスの \<[ステップ]** ページで、ステップ **[エージェントを実行します]** を選択し、**[編集]** をクリックします。  
  
5.  
  **[ジョブ ステップのプロパティ - エージェントを実行します]** ダイアログ ボックスで、 **[コマンド]** フィールドを編集します。  
  
6.  両方のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーションエージェントの管理](replication-agent-administration.md)   
 [レプリケーションエージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)   
 [レプリケーションエージェントの概要](replication-agents-overview.md)  
  
  
