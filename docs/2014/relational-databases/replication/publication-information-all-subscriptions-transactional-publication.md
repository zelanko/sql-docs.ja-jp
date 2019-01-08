---
title: パブリケーション情報、[すべてのサブスクリプション] (トランザクション パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.tran.f1
ms.assetid: 7073350c-f667-4f70-88e9-152c9a1b08dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a1383a7cd470e162a2c25a121fea7455ea381c06
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762084"
---
# <a name="publication-information-all-subscriptions-transactional-publication"></a>パブリケーション情報、[すべてのサブスクリプション]\(トランザクション パブリケーション)
  **[すべてのサブスクリプション]** タブには、選択したトランザクション パブリケーションに対するすべてのサブスクリプションの情報が表示されます。  
  
## <a name="options"></a>および  
 サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **並べ替え**:1 つ以上の列で並べ替え、**列の並べ替え** ダイアログ ボックス。  
  
-   **表示する列を選択**:列の表示とその表示順序を選択、**列の選択** ダイアログ ボックス。  
  
-   **フィルター**:列の値に基づいてグリッドの行をフィルター選択、**フィルター設定** ダイアログ ボックス。  
  
-   **フィルターのクリア**:グリッドのすべてのフィルター設定をオフにします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **[表示]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。 たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。  
  
 **[状態]**  
 各サブスクリプションの状態です。これは、ディストリビューション エージェントまたはログ リーダー エージェントの状態により決まります (より優先度の高い状態が表示されます。キュー更新サブスクリプションが使用されている場合、この状態はキュー リーダー エージェントによって決まる場合もあります)。  
  
 既定では、サブスクリプションの情報を表示するグリッドは **[状態]** 列の順序で並べられています (同じ状態のサブスクリプションは、 **[パフォーマンス]** 列の順序で並べられています)。 表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。  
  
-   [エラー]  
  
-   [パフォーマンス クリティカル] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [まもなく期限切れ/期限切れ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [初期化されていないサブスクリプション] \([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [失敗したコマンドの再試行]  
  
-   停止中  
  
-   実行中  
  
 特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。 たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。  
  
 状態値 **[パフォーマンス クリティカル]**、 **[まもなく期限切れ/期限切れ]**、および **[初期化されていないサブスクリプション]** は警告です。 警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。 たとえば、 **[実行中]、[パフォーマンス クリティカル]** という形で状態が表示されます。  
  
 状態値 **[パフォーマンス クリティカル]** および **[まもなく期限切れ/期限切れ]** は、しきい値が設定されている場合のみ表示されます。 パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。  
  
 **サブスクリプション**  
 サブスクリプションごとに、フォームでの名前。*SubscriberName:SubscriptionDatabaseName*します。  
  
 **[パフォーマンス]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 各サブスクリプションのパフォーマンス評価は、レプリケーション モニターにより取得され、履歴パフォーマンスに反映されていない、最も新しい計測値に基づいています。 パフォーマンスは、パフォーマンスしきい値が定義されているパブリケーションへのサブスクリプションについてのみ計測されます。パブリケーションにパフォーマンスしきい値が定義されていない場合、この列には **[有効になっていません]** と表示されます。 パフォーマンス評価は、次のいずれかの値になります。  
  
-   [非常に良い]  
  
-   [良い]  
  
-   [普通]  
  
-   悪い  
  
-   重大  
  
 パフォーマンスが [重大] の場合、 **[状態]** 列に **[パフォーマンス クリティカル]** と表示されます。 パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。  
  
 **[待機時間]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 トランザクションがパブリッシャー側でコミットされたときから、サブスクライバー側で対応するトランザクションがコミットされるまでに経過した時間の平均値です。 表示される待機時間は、レプリケーション モニターにより取得された最新の計測値に基づいています。 待機時間の計測の詳細については、「[トランザクション レプリケーションの待機時間の計測および接続の検証](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](monitor/start-the-replication-monitor.md)   
 [サブスクリプションの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [レプリケーションの監視](monitoring-replication.md)  
  
  
