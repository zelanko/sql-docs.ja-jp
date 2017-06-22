---
title: "SQL Server フェールオーバー クラスター インスタンスのアップグレード | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
caps.latest.revision: 47
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 060f7bbbcd12d1b41f4c527fb1c1dff34b666134
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="upgrade-a-sql-server-failover-cluster-instance"></a>SQL Server フェールオーバー クラスター インスタンスのアップグレード
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターを、新しい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]バージョン、新しい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービス パック、または累積更新プログラムにアップグレードするか、新しい Windows サービス パックや累積更新プログラムを、すべてのフェールオーバー クラスター ノードに個別にインストールして、ダウンタイムを、単一の手動フェールオーバー (元のプライマリにフェールバックする場合は、2 回の手動フェールオーバー) に制限できます。  
  
 フェールオーバー クラスターの Windows オペレーティング システムのアップグレードは、Windows Server 2012 R2 より前のオペレーティング システムではサポートされません。 Windows Server 2012 R2 で実行されているクラスター ノードのアップグレードについては、「 [Cluster Operating System Rolling Upgrade (クラスター オペレーティング システムのローリング アップグレード)](https://technet.microsoft.com/en-us/library/dn850430.aspx)」を参照してください  
  
 サポートの詳細は、次のとおりです。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アップグレードがサポートされています。 各フェールオーバー クラスター ノードでコマンド プロンプトからアップグレードを実行するか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップ UI を使用して各クラスター ノードをアップグレードできます。  詳細については、「 [SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md) 」および「 [コマンド プロンプトからの SQL Server 2016 のインストール](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。  
  
-   次のシナリオは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アップグレードではサポートされていません。  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスからフェールオーバー クラスターにはアップグレードできません。  
  
    -   フェールオーバー クラスターに機能を追加することはできません。 たとえば、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のみの既存のフェールオーバー クラスターに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を追加することはできません。  
  
    -   フェールオーバー クラスター ノードからスタンドアロン インスタンスへのダウングレード。  
  
    -   フェールオーバー クラスターのエディションの変更は、特定のシナリオに制限されています。 詳細については、「 [サポートされているバージョンとエディションのアップグレード](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」をご覧ください。  
  
-   フェールオーバー クラスターのアップグレードにおけるダウンタイムは、フェールオーバー時間およびアップグレード スクリプトの実行に必要な時間のみです。 次のフェールオーバー クラスターのローリング アップグレード プロセスに従い、さらに、すべてのノードですべての前提条件を満たしてから、アップグレード プロセスを開始することで、ダウンタイムを最小限に抑えることができます。 メモリ最適化テーブルを使用している場合、SQL Server 2014 をアップグレードすると、余分な時間がかかることがあります。 詳細については、「 [Plan and Test the Database Engine Upgrade Plan](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 作業を開始する前に、次の重要な情報を確認してください。  
  
-   [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md): 自分のバージョンの Windows オペレーティング システムと SQL Server から SQL Server 2016 にアップグレードできることを確認します。 たとえば、SQL Server 2005 フェールオーバー クラスタリング インスタンスから [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] には直接アップグレードできません。また、Windows Server 2003 で実行されているフェールオーバー クラスターをアップグレードすることもできません。  
  
-   [Choose a Database Engine Upgrade Method](../../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md): サポートされるバージョンとエディションのアップグレードに基づいて、適切なアップグレードの方法と手順を選択します。また、自分の環境にインストールされているその他のコンポーネントに基づいて、正しい順序でコンポーネントをアップグレードします。  
  
-   [データベース エンジンのアップグレード計画の策定およびテスト](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md): リリース ノート、アップグレードに関する既知の問題、アップグレード前のチェックリストを確認して、アップグレードの計画を作成およびテストします。  
  
-   [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md): [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]をインストールするためのソフトウェア要件を確認します。 その他のソフトウェアが必要な場合は、ダウンタイムを最小限に抑えるために、アップグレード プロセスを開始する前に、各ノードにソフトウェアをインストールします。  
  
## <a name="performing-a-rolling-upgrade-or-update"></a>ローリング アップグレードまたは更新の実行  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターを [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]にアップグレードするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップを使用して、フェールオーバー クラスター ノードをパッシブ ノードから 1 つずつアップグレードします。 各ノードをアップグレードする場合、ノードはフェールオーバー クラスターの実行可能な所有者から除外されます。 予期しないフェールオーバーが発生した場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップによりクラスター リソース グループの所有権がアップグレード済みのノードに移動するまで、アップグレード済みのノードはフェールオーバーに関与しません。  
  
 既定では、アップグレード済みのノードにフェールオーバーする時期は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップにより自動的に決まります。 決定の際に基準になるのは、フェールオーバー クラスター インスタンス内のノード総数、およびアップグレード済みのノード数です。 ノード総数の半数以上がアップグレード済みの場合、次のノードでアップグレードする際、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップにより、アップグレード済みのノードにフェールオーバーが発生します。 アップグレード済みのノードにフェールオーバーする際、クラスター グループはアップグレード済みのノードに移動します。 すべてのアップグレード済みノードは実行可能な所有者の一覧に格納され、まだアップグレードされていないすべてのノードは実行可能な所有者の一覧から削除されます。 残りの各ノードをアップグレードする場合、ノードはフェールオーバー クラスターの実行可能な所有者に追加されます。  
  
 ダウンタイムでのこのプロセス結果は、1 回のフェールオーバー時間、および全フェールオーバー クラスター アップグレード時のデータベース アップグレード スクリプトの実行時間に限定されます。  
  
 アップグレード プロセス中にクラスター ノードのフェールオーバーの動作を制御するには、コマンド プロンプトでアップグレード操作を実行して、/FAILOVERCLUSTERROLLOWNERSHIP パラメーターを使用します。 詳細については、「 [コマンド プロンプトからの SQL Server 2016 のインストール](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インストール ウィザードを使用した SQL Server 2016 へのアップグレード &#40;セットアップ&#41;](../../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)   
 [コマンド プロンプトからの SQL Server 2016 のインストール](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)  
  
  

