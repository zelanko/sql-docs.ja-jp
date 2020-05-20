---
title: Always On 可用性グループでの運用上の問題の Always On ポリシー (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], policies
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 090ad6a9651a01532af528f5f78316eeadb9798d
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922011"
---
# <a name="always-on-policies-for-operational-issues-with-always-on-availability-groups-sql-server"></a>AlwaysOn 可用性グループでの運用上の問題のポリシー ベースの管理 (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の正常性モデルは、定義済みポリシー ベースの管理 (PBM) ポリシーのセットを評価します。 これらのポリシーを使用すると、可用性グループとその可用性レプリカおよびデータベースの正常性を [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]で表示できます。  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a>用語と定義  
 AlwaysOn の定義済みのポリシー  
 一連の組み込みポリシーを使用して、データベース管理者は可用性グループとその可用性レプリカおよびデータベースが AlwaysOn ポリシーで定義されている状態に適合しているかどうかをチェックできます。  
  
 [AlwaysOn 可用性グループ](always-on-availability-groups-sql-server.md)高可用性とディザスターリカバリーのためのソリューションであり、データベースミラーリングに代わるエンタープライズレベルの選択肢を提供します。  
  
 可用性グループ  
 ひとまとまりでフェールオーバーされる個別のユーザー データベースのセット ( *可用性データベース*) のコンテナー。  
  
 可用性レプリカ  
 可用性グループのインスタンス化。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の特定のインスタンスによってホストされ、可用性グループに属する各可用性データベースのローカル コピーを保持します。 可用性グループには、2 種類の可用性レプリカ ( *プライマリ レプリカ* と 1 ～ 4 つの *セカンダリ レプリカ*) があります。 可用性グループの可用性レプリカをホストするサーバー インスタンスは、同じ Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の別のノードにある必要があります。  
  
 可用性データベース  
 可用性グループに属しているデータベース。 可用性データベースごとに、可用性グループは 1 個の読み取り/書き込み可能なコピー ( *プライマリ データベース*) と 1 ～ 4 個の読み取り専用コピー (*セカンダリ データベース*) を管理します。  
  
 AlwaysOn ダッシュボード  
 可用性グループの正常性をひとめで確認できるビューを提供する [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ダッシュボード。 詳細については、このトピックの「 [AlwaysOn ダッシュボード](#Dashboard)」を参照してください。  
  
##  <a name="predefined-policies-and-issues"></a><a name="AlwaysOnPBM"></a>定義済みのポリシーと問題点  
 次の表は、定義済みのポリシーをまとめたものです。  
  
|ポリシー名|問題|別**<sup>*</sup>**|ファセット|  
|-----------------|-----------|------------------------------|-----------|  
|WSFC クラスターの状態|[WSFC クラスターサービスはオフライン](wsfc-cluster-service-is-offline.md)です。|重要|SQL Server のインスタンス|  
|可用性グループのオンライン状態|[可用性グループはオフライン](availability-group-is-offline.md)です。|重要|可用性グループ|  
|可用性グループの自動フェールオーバーの準備|[可用性グループで自動フェールオーバーの準備ができていません](availability-group-is-not-ready-for-automatic-failover.md)。|重要|可用性グループ|  
|可用性レプリカのデータ同期状態|[一部の可用性レプリカがデータを同期していません](some-availability-replicas-are-not-synchronizing-data.md)。|警告|可用性グループ|  
|同期レプリカのデータの同期状態|[一部の同期レプリカが同期されていません](some-synchronous-replicas-are-not-synchronized.md)。|警告|可用性グループ|  
|可用性レプリカのロールの状態|[一部の可用性レプリカに正常なロールがありません](some-availability-replicas-do-not-have-a-healthy-role.md)。|警告|可用性グループ|  
|可用性レプリカの接続状態|[一部の可用性レプリカが切断され](some-availability-replicas-are-disconnected.md)ています。|警告|可用性グループ|  
|可用性レプリカのロールの状態|[可用性レプリカに正常なロールがありません](availability-replica-does-not-have-a-healthy-role.md)。|重要|可用性レプリカ|  
|可用性レプリカの接続状態|[可用性レプリカが切断され](availability-replica-is-disconnected.md)ています。|重要|可用性レプリカ|  
|可用性レプリカの参加状態|[可用性レプリカが参加していません](availability-replica-is-not-joined.md)。|警告|可用性レプリカ|  
|可用性レプリカのデータの同期状態|[一部の可用性データベースのデータ同期状態が正常ではありません](data-synchronization-state-of-some-availability-database-is-not-healthy.md)。|警告|可用性レプリカ|  
|可用性データベースの中断状態|[可用性データベースが中断され](availability-database-is-suspended.md)ています。|警告|可用性データベース|  
|可用性データベースの参加状態|[セカンダリデータベースが参加していません](secondary-database-is-not-joined.md)。|警告|可用性データベース|  
|可用性データベースのデータ同期状態|[可用性データベースのデータ同期状態が正常ではありません](data-synchronization-state-of-availability-database-is-not-healthy.md)。|警告|可用性データベース|  
  
> [!IMPORTANT]  
>  **<sup>*</sup>** AlwaysOn ポリシーの場合、カテゴリ名は Id として使用されます。 AlwaysOn カテゴリの名前を変更すると、正常性評価の機能を使用できなくなります。 このため、AlwaysOn カテゴリの名前は変更しないでください。  
  
##  <a name="alwayson-dashboard"></a><a name="Dashboard"></a>AlwaysOn ダッシュボード  
 AlwaysOn ダッシュボードには、可用性グループの正常性をひとめで確認できるビューが用意されています。 AlwaysOn ダッシュボードには、次の機能が含まれています。  
  
-   指定された可用性グループ、その可用性レプリカ、およびそのデータベースの詳細情報を簡単に表示できます。  
  
-   主要な状態が視覚的に表示され、データベース管理者は運用上の意思決定を迅速に行うことができます。  
  
-   トラブルシューティング シナリオの開始ポイントを提供します。  
  
-   特定の運用上の問題点について、 **[ポリシー評価の結果]** ダイアログ ボックスに、特定の AlwaysOn 正常性ポリシーの違反に関する情報と、修復のヘルプへのリンクを示します。  
  
-   AlwaysOn 固有の問題の前のイベントを表示する正常性拡張イベント ビューアーを提供します。  
  
-   可用性グループのフェールオーバーで特定の問題を修復できる場合、リンクの開始ポイントである[可用性グループのフェールオーバー ウィザード](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)を提供します。 データベース管理者は、このウィザードを使用して手動フェールオーバー プロセスを実行します。  
  
##  <a name="extending-the-alwayson-health-model"></a><a name="ExtendHealthModel"></a>AlwaysOn 正常性モデルの拡張  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の正常性モデルを拡張するには、独自のユーザー定義のポリシーを作成し、監視するオブジェクトの種類に基づいて特定のカテゴリに分類します。  いくつかの設定を変更した後、独自のユーザー定義のポリシーおよび AlwaysOn の定義済みのポリシーが、AlwaysOn ダッシュボードによって自動的に評価されます。  
  
 ユーザー定義ポリシーでは、AlwaysOn の定義済みポリシーで使用されているものを含め、使用可能なすべての PBM ファセットを使用できます (このトピックの「[定義済みのポリシーと問題点](#AlwaysOnPBM)」を参照してください)。 サーバーのファセットは、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の正常性状態の監視用に、`IsHadrEnabled` プロパティおよび `HadrManagerStatus` プロパティを提供します。 サーバーのファセットは、WSFC クラスター構成の監視用に、`ClusterQuorumType` プロパティおよび `ClusterQuorumState` プロパティも提供します。  
  
 詳細については、「[AlwaysOn の正常性モデル: パート 2: 正常性モデルの拡張](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)」を参照してください (SQL Server AlwaysOn チームのブログ)。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [AlwaysOn ポリシーを使用して、可用性グループ &#40;SQL Server の正常性を表示&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [WSFC の強制クォーラムによる災害復旧 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [クォーラムを使用せずに WSFC クラスターを強制的に起動する](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [可用性グループ &#40;SQL Server の強制手動フェールオーバーを実行&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> 関連コンテンツ  
  
-   [AlwaysOn の正常性モデル: パート 1: 正常性モデルのアーキテクチャ](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [AlwaysOn の正常性モデル: パート 2: 正常性モデルの拡張](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ (SQL Server)](always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループ &#40;SQL Server の管理&#41;](administration-of-an-availability-group-sql-server.md)   
 [可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
