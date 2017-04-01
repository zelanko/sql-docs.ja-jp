---
title: "パブリケーション情報、[すべてのサブスクリプション] (マージ パブリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.merge.f1"
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# パブリケーション情報、[すべてのサブスクリプション] (マージ パブリケーション)
   **すべてのサブスクリプション** ] タブが選択されているマージ パブリケーションに対するすべてのサブスクリプションに関する情報を表示します。  
  
## オプション  
 サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。  
  
-   **[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。  
  
-   **[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。  
  
-   **[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **[表示]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。 たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。  
  
 **[状態]**  
 各サブスクリプションの状態です。これは、マージ エージェントの状態により決定されます。  
  
 既定では、サブスクリプション情報を含むグリッドが並べ替えられます、 **ステータス** 列 (で、並べ替えて、 **パフォーマンス** 、該当する状態のサブスクリプションの列)。 表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。  
  
-   [エラー]  
  
-   [パフォーマンス クリティカル] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [長期マージ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [まもなく期限切れ/期限切れ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [初期化されていないサブスクリプション] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [失敗したコマンドの再試行]  
  
-   [同期中]  
  
-   [同期されていません]  
  
 特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。 たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]**と表示されます。  
  
 状態値 **パフォーマンス クリティカル**, 、**長期マージ**, 、**まもなく期限切れ/期限切れ**, 、および **初期化されていないサブスクリプション** 警告します。 警告が表示される、 **ステータス** 列は、エージェントが同期している場合にも表示されます。 たとえば、状態がある可能性があります **同期中]、[パフォーマンス クリティカル**します。  
  
 状態値 **まもなく期限切れ/期限切れ** と **長期マージ** しきい値が設定されている場合にのみ表示されることができます。 状態値 **パフォーマンス クリティカル** 同じ接続の種類 (ダイヤルアップまたは LAN) によるサブスクリプションの 5 つの同期後にのみ表示することができます。 パフォーマンスの測定としきい値の設定については、次を参照してください。 [レプリケーション モニターを使用してパフォーマンスを監視する](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) と [しきい値の設定とレプリケーション モニターで警告](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)します。  
  
 **サブスクリプション**  
 サブスクリプションごとに、フォームでの名前:*SubscriberName: SubscriptionDatabaseName*します。  
  
 **表示名**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 各サブスクリプションの説明です。 説明を入力、 **サブスクリプションのプロパティ** ] ダイアログ ボックスで指定された、または、 **@description** のパラメーター [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) または [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)します。 多くの場合、この説明は "表示名"、つまりサブスクリプションの通称として使用されます。  
  
 **パフォーマンス**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 各サブスクリプションのパフォーマンス評価です。これはレプリケーション モニターにより取得された、最新の配信率の計測結果に基づいています。 パフォーマンス評価は、接続の種類が同じ (ダイヤルアップまたは LAN) パブリケーションに対するサブスクリプションの履歴の平均パフォーマンスと、個々のサブスクリプションのパフォーマンスを比較することで決定されます。 レプリケーション モニターには、50 以上の変更を伴う同期がそれぞれ同じ種類の接続により 5 回行われた後で、値が表示されます。 50 以上の変更を伴う同期が 5 回未満の場合、または最新の同期における変更が 50 未満の場合には、この列は空白になります。  
  
> [!NOTE]  
>  パフォーマンスに表示される接続の種類に基づいて、 **接続** 列です。 したがっては高いパフォーマンス サブスクリプションよりも低速接続経由で最初のサブスクリプションが同期されている場合に表示する配信単価の低いサブスクリプションことです。  
  
 パフォーマンス評価は、次のいずれかの値になります。  
  
-   [非常に良い]  
  
-   [良い]  
  
-   [普通]  
  
-   悪い  
  
 パフォーマンス評価の定義方法と、パフォーマンスのしきい値を設定する方法の詳細については、次を参照してください。 [レプリケーション モニターを使用してパフォーマンスを監視する](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)です。  
  
 **[配信率]**  
 マージ エージェントにより 1 秒間に処理される行数です。  
  
 **[最後の同期]**  
 マージ エージェントが最後に実行された時刻です。 この同期では変更が処理されていることも、処理されていないこともあります。 同期が進行中の場合、進行状況を示すパーセント値が表示されます。  
  
 **Duration**  
 最後の同期中におけるマージ エージェントの実行時間です。 マージ エージェントが現在同期中の場合、これは経過時間を表します。マージ エージェントが以前に同期された場合、これは合計時間を表します。  
  
 **接続**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 サブスクライバーとパブリッシャーの接続の種類です。 指定できる値は **LAN**, 、**ダイヤルアップ**, 、および **インターネット**します。  **インターネット** サブスクリプションは、Web 同期を使用している場合、値が表示されます。  
  
## 参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [情報を表示し、サブスクリプションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [マージ レプリケーションの Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  