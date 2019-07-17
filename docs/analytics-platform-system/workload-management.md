---
title: Analytics Platform System でのワークロード管理 |Microsoft Docs
description: Analytics Platform System でワークロードの管理。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: adc3928e1b7464d93970d280af6acf303ebc6d16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959747"
---
# <a name="workload-management-in-analytics-platform-system"></a>Analytics Platform System でのワークロード管理

SQL Server PDW のワークロード管理機能は、ユーザーと管理者は、メモリと同時実行の構成を事前設定する要求を割り当てることを許可します。 すべての要求を枯渇させて永久になく、適切なリソースをさせることが要求を許可することで、一貫性のある、または混合、ワークロードのパフォーマンスを向上させるために、ワークロード管理を使用します。  
  
たとえば、SQL Server PDW のワークロード管理機能を操作できます。  
  
-   リソースを読み込みジョブの数が多いを割り当てます。  
  
-   列ストア インデックスを構築するための他のリソースを指定します。  
  
-   低速なハッシュ結合してより多くのメモリが必要がある場合のトラブルシューティングを行うしより多くのメモリを提供します。  
  
## <a name="Basics"></a>ワークロード管理の基礎  
  
### <a name="key-terms"></a>主な用語  
ワークロード管理  
*ワークロード管理*を理解し、同時要求の最適なパフォーマンスを実現するためにシステム リソースの使用率を調整できることです。  
  
リソース クラス  
SQL Server PDW で、*リソース クラス*メモリおよび同時実行の事前割り当て済みの制限のある組み込みのサーバーの役割です。 SQL Server PDW は、要求を送信したログインのリソース クラスのサーバー ロール メンバーシップに基づいて要求にリソースを割り当てます。  
  
コンピューティング ノードでは、リソース クラスの実装は、SQL Server でのリソース ガバナー機能を使用します。 リソース ガバナーに関する詳細については、次を参照してください。[リソース ガバナー](../relational-databases/resource-governor/resource-governor.md) msdn です。  
  
### <a name="understand-current-resource-utilization"></a>現在のリソース使用率を理解します。  
現在実行中の要求のシステム リソースの使用率を理解するには、SQL Server PDW の動的管理ビューを使用します。 たとえばより多くのメモリで実行速度の遅い大規模なハッシュ結合も役立つようなかどうかを理解するのに Dmv を使用することができます。  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>リソース割り当てを調整します。  
リソース使用率を調整するのには、要求を送信しているログインのリソース クラスのメンバーシップを変更します。 リソース クラスのサーバー ロールの名前は**mediumrc**、 **largerc**、および**xlargerc**します。 中規模、大規模、および超大規模なリソース割り当てをそれぞれ表します。  
  
たとえば、大量の要求にシステム リソースを割り当てるへの要求を送信しているログインを追加、 **largerc**サーバーの役割。 次の ALTER SERVER ROLE ステートメントは、Anna のログインを largerc サーバーの役割に追加します。  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="RC"></a>リソース クラスの説明  
次の表では、リソース クラスと、システム リソースの割り当てについて説明します。  
  
|リソース クラス|要求の重要度|最大メモリ使用量 *|同時実行スロット (最大 32 =)|説明|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|既定値 (default)|Medium|400 MB|1|既定では、各ログインは少量のメモリ、およびその要求のリソースを同時実行を許可します。<br /><br />リソース クラスには、ログインを追加するときに、新しいクラスが優先されます。 すべてのリソース クラスのログインが削除されると、ログインは、既定のリソース割り当てに戻ります。|  
|MediumRC|Medium|1200 MB|3|中規模リソース クラスが必要になる要求の例:<br /><br />CTAS の操作を持つ大規模なハッシュ結合です。<br /><br />ディスクにキャッシュを回避するためにより多くのメモリを必要とする操作を選択します。<br /><br />クラスター化列ストア インデックスにデータを読み込んでいます。<br /><br />ビルド、リビルド、および 10 ~ 15 列を含む小さなテーブルにクラスター化列ストア インデックスを再構成します。|  
|Largerc|高|2.8 GB|7|サイズの大きいリソース クラスが必要になる要求の例:<br /><br />膨大なハッシュ結合、または大規模な ORDER BY または GROUP BY 句などの大量の集計を含めることが非常に大きな CTAS 操作。<br /><br />ハッシュ結合などの操作または ORDER BY または GROUP BY 句などの集計の非常に大量のメモリを必要とする操作を選択します。<br /><br />クラスター化列ストア インデックスにデータを読み込んでいます。<br /><br />ビルド、リビルド、および 10 ~ 15 列を含む小さなテーブルにクラスター化列ストア インデックスを再構成します。|  
|xlargerc|高|8.4 GB|22|超大規模なリソース クラスは、実行時に超大規模なリソースの消費量が必要になる要求です。|  
  
<sup>*</sup>最大メモリ使用量は、簡略化したものです。  
  
### <a name="request-importance"></a>要求の重要度  
要求の重要度は、要求に、コンピューティング ノードで実行される、SQL Server は、CPU 時間の量にマップされます。  優先順位の高い要求には、多くの CPU 時間が表示されます。  
  
### <a name="maximum-memory-usage"></a>最大メモリ使用量  
最大メモリ使用量は、要求が各処理領域内で使用できる使用可能なメモリの最大量です。 たとえば mediumrc 要求では、各配布内で処理を 1200 MB を使用できます。 ほとんどの作業を実行するいくつかのディストリビューションを回避するためにデータがスキューしないことを確認することも重要です。  
  
### <a name="concurrency-slots"></a>同時実行スロット  
1、3、7、および 22 の同時実行スロットの割り当ての目標は、大小のプロセスが大規模なプロセスを実行するときに、小規模なプロセスをブロックすることがなく、同時に実行できるようにすること。  たとえば、SQL Server PDW は 1 超大規模な要求 (22 スロット)、1 つの大きな要求 (7 スロット)、および中規模の 1 つの要求 (3 つのスロット) を同時に実行する 32 の同時実行スロットの最大値を割り当てることができます。  
  
同時実行要求に最大 32 個の同時実行スロットの割り当ての例:  
  
-   28 スロット 4 の大規模なを =  
  
-   30 個のスロット 10 メディアを =  
  
-   32 個のスロット = 32 既定  
  
-   32 個のスロット = 極大サイズ 1 + 1 の大規模な + 1 のメディア  
  
-   32 個のスロット 2 の大きな + 4 のメディア + 6 既定を =  
  
SQL Server の PDW に 6 つの大規模な要求が送信され、既定の 10 件の要求を送信し、あるとします。 SQL Server PDW では、次のように優先順位に従って要求を処理は。  
  
-   メモリが使用可能になるように 4 つの大規模な要求の処理を開始する 28 の同時実行スロットを割り当てるし、2 つの大規模な要求をキューに保持します。  
  
-   4 つの既定の要求の処理を開始する 4 つの同時実行スロットを割り当て、待機キューに 6 つの既定の要求を保持します。  
  
要求が完了し、同時実行スロットが利用可能になる、SQL Server PDW では使用可能なリソースと優先順位に従って残りの要求を割り当てます。 たとえば、7 の同時実行スロットの開きがある場合は、大規模な要求を待機している必要があります 7 スロットが中程度の要求を待機するよりも、高い優先順位。  6 つのスロットが開く場合は SQL Server PDW は 6 以上既定サイズの要求を割り当てます。 ただし、メモリおよび同時実行スロットできる必要がありますすべて SQL Server PDW は、要求を実行する前にします。  
  
各リソース クラス内では、要求は、先入れ先出し (FIFO) 順で最初に実行します。  
  
## <a name="GeneralRemarks"></a>全般的な解説  
ログインが 1 つ以上のリソース クラスのメンバーである場合は、ほとんどのリソースを使用して、クラスが優先されます。  
  
ログインが追加またはリソースのクラスから削除されるときに、変更は; 将来のすべての要求をすぐに有効実行中または待機している現在の要求は影響しません。 ログインは、切断して、変更が発生するために再接続する必要はありません。  
  
ログインごとに、リソース クラスの設定は、個々 のステートメントと、操作して、セッションが適用されます。  
  
SQL Server PDW のステートメントを実行する前に、要求のために必要な同時実行スロットを取得しようとします。 十分な同時実行スロットを取得できない場合は SQL Server PDW は、要求を待機しているをする--実行状態に移動します。 要求に既に割り当てられていたすべてのリソース システムがシステムに返されます。  
  
ほとんどの SQL ステートメントでは、常に既定のリソース割り当てを必要し、そのため、リソース クラスによって制御されていません。 たとえば、CREATE LOGIN はのみ少量のリソースの必要があり、CREATE LOGIN を呼び出してログインのリソース クラスのメンバーである場合でも、既定のリソースが割り当てられます。  たとえば、Anna largerc のリソース クラスのメンバーである、彼女は、CREATE LOGIN ステートメントを送信する場合は、CREATE LOGIN ステートメントは、リソースの既定の数で実行されます。  
  
SQL ステートメントとリソース クラスによって管理される操作:  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   ALTER テーブルの再構築  
  
-   CREATE CLUSTERED INDEX  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS を選択します  
  
-   REMOTE TABLE AS SELECT を作成します。  
  
-   データを読み込む**dwloader**します。  
  
-   INSERT-SELECT  
  
-   UPDATE  
  
-   Del  
  
-   RESTORE DATABASE より多くのコンピューティング ノードを備えたアプライアンスに復元するときにします。  
  
-   DMV 専用のクエリを除外するを選択します。  
  
## <a name="Limits"></a>制限事項と制約事項  
リソース クラスでは、メモリおよび同時実行の割り当てによって制御されます。  入力/出力操作の管理を行わない。  
  
## <a name="Metadata"></a>メタデータ  
リソース クラスとリソース クラスのメンバーに関する情報が含まれている Dmv。  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
要求および必要なリソースの状態に関する情報が含まれている Dmv:  
  
-   [sys.dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys.dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
コンピューティング ノード上の SQL Server Dmv から公開されている関連するシステム ビュー。 参照してください[SQL Server の動的管理ビュー](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)これらの Dmv msdn へのリンク。  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys.dm_pdw_nodes_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys.dm_pdw_nodws_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_exec_sessions  
  
-   sys.dm_pdw_nodes_exec_requests  
  
-   sys.dm_pdw_nodes_exec_query_memory_grants  
  
-   sys.dm_pdw_nodes_exec_query_resource_semaphores  
  
-   sys.dm_pdw_nodes_os_memory_brokers  
  
-   sys.dm_pdw_nodes_os_memory_cache_entries  
  
-   sys.dm_pdw_nodes_exec_cached_plans  
  
## <a name="RelatedTasks"></a>関連するタスク  
[ワークロードの管理タスク](workload-management-tasks.md)  
  
<!-- MISSING LINKS
See the Workload Management section of [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md) for the following tasks:  
  
1.  Find the number of active requests for each resource group.  
  
2.  Determine if my requests need more memory  
  
3.  Determine if there are a high number of query optimizations or suboptimal plan generations.  
  
4.  Determine Average CPU time per request in each resource pool to date  
  
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
