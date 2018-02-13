---
title: "ワークロードの管理 (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/12/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69063b1a-a8f3-453a-83ab-afbe7eb4f463
caps.latest.revision: 
ms.openlocfilehash: 738818a49491fbf8f8df491cac2f10ebdeedf3bf
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="workload-management"></a>ワークロードの管理
SQL Server PDW のワークロードの管理機能には、ユーザーと管理者はあらかじめ設定されているメモリ、および同時実行の構成への要求を割り当てることができるようにします。 すべての要求を永久に不足せずに必要な適切なリソースへの要求を許可することで、一貫性のある、または混合、ワークロードのパフォーマンスを向上させるためにワークロードの管理を使用します。  
  
たとえば、SQL Server PDW でワークロードの管理方法を使用することができます。  
  
-   大量の読み込みジョブにリソースを割り当てます。  
  
-   列ストア インデックスを構築するための他のリソースを指定します。  
  
-   低速なハッシュ結合してより多くのメモリが必要がある場合のトラブルシューティングを行うしより多くのメモリを指定します。  
  
## <a name="Basics"></a>ワークロード管理の基礎  
  
### <a name="key-terms"></a>主な用語  
ワークロードの管理  
*ワークロード管理*理解し、同時要求の最適なパフォーマンスを実現するためにシステム リソースの使用率を調整する機能です。  
  
リソース クラス  
SQL Server PDW では*リソース クラス*はメモリと同時実行についての事前割り当ての制限のある組み込みのサーバー ロール。 SQL Server PDW では、要求を送信したログインのリソース クラス サーバー ロールのメンバーシップに基づいて要求にリソースを割り当てます。  
  
コンピューティング ノードでは、リソース クラスの実装は、SQL Server ではリソース ガバナー機能を使用します。 リソース ガバナーに関する詳細については、次を参照してください。[リソース ガバナー](http://msdn.microsoft.com/en-us/library/bb933866(v=sql.11).aspx) msdn です。  
  
### <a name="understand-current-resource-utilization"></a>現在のリソース使用率を理解します。  
現在実行中の要求のシステム リソースの使用率を理解するには、SQL Server PDW の動的管理ビューを使用します。 たとえば、Dmv を使用するより多くのメモリでの実行速度の遅い大規模なハッシュ結合を得ることがかどうかを理解します。  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>リソース割り当てを調整します。  
リソース使用率を調整するには、するには、要求を送信しているログインのリソース クラスのメンバーシップを変更します。 リソース クラスのサーバー ロールの名前は**mediumrc**、 **largerc**、および**xlargerc**です。 中程度大きくて特大のリソース割り当てをそれぞれ表しているとします。  
  
たとえば、大量の要求にシステム リソースを割り当てるに、ログインを追加する要求を送信する、 **largerc**サーバーの役割です。 次の ALTER SERVER ROLE ステートメントは、ログイン Anna を largerc サーバーの役割を追加します。  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="RC"></a>リソース クラスの説明  
次の表は、リソースのクラスと、システム リソースの割り当てについて説明します。  
  
|リソース クラス|要求の重要度|最大メモリ使用量 *|同時実行スロット (最大 32 =)|Description|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|既定値 (default)|Medium|400 MB|1|既定では、各ログインに少量のメモリ、およびその要求のリソースを同時実行は許可されています。<br /><br />リソース クラスには、ログインを追加するときに、新しいクラスが優先されます。 すべてのリソース クラスからのログインが削除されると、ログインは、既定のリソース割り当てに戻ります。|  
|MediumRC|Medium|1200 MB|3|メディア リソースのクラスが必要な要求の例:<br /><br />持つ大規模な CTAS 操作はハッシュ結合です。<br /><br />多くのメモリをディスクにキャッシュを回避する必要のある操作を選択します。<br /><br />クラスター化列ストア インデックスにデータを読み込んでいます。<br /><br />ビルド、再構築、および 10 ~ 15 列を含む小さいテーブルのクラスター化列ストア インデックスを再構成します。|  
|largerc|High|2.8 GB|7|サイズの大きいリソースのクラスが必要な要求の例:<br /><br />大きなハッシュ結合または大規模な ORDER BY 句または GROUP BY 句など、大量の集計を含む非常に大きな CTAS 操作です。<br /><br />ハッシュ結合などの操作または GROUP BY または ORDER BY 句などの集計の非常に大量のメモリを必要とする操作を選択します。<br /><br />クラスター化列ストア インデックスにデータを読み込んでいます。<br /><br />ビルド、再構築、および 10 ~ 15 列を含む小さいテーブルのクラスター化列ストア インデックスを再構成します。|  
|xlargerc|High|8.4 GB|22|特大リソース クラスは、実行時に余分なサイズの大きいリソースの消費量が必要になる要求します。|  
  
<sup>*</sup>最大メモリ使用量は概数です。  
  
### <a name="request-importance"></a>要求の重要度  
要求の重要度は、要求にコンピューティング ノードで実行されている SQL Server は、CPU 時間にマップされます。  優先度の高い要求には、多くの CPU 時間が表示されます。  
  
### <a name="maximum-memory-usage"></a>最大メモリ使用量  
最大メモリ使用量は、要求が各処理領域内で使用できる使用可能なメモリの最大量です。 たとえば mediumrc 要求は、各配布内で処理を 1200 MB までを使用できます。 これは、データは、いくつかの分布のほとんどの作業を実行する必要があるようにするために傾斜いないことを確認することも重要です。  
  
### <a name="concurrency-slots"></a>同時実行スロット  
1、3、7、および 22 の同時実行スロットの割り当ての目的は、大規模なプロセスが実行されている場合は、小さなプロセスをブロックすることがなく、同時に実行する大きなおよび小規模の両方のプロセスを許可します。  たとえば、SQL Server PDW では、1 特大要求 (22 スロット)、および実行する 1 のサイズの大きい要求 (7)、スロット 1 の中の要求 (3 つのスロット)、同時に 32 の同時実行スロットの最大値を割り当てることができます。  
  
同時実行要求に最大 32 の同時実行スロットの割り当ての例:  
  
-   28 スロット 4 の大規模なを =  
  
-   30 個のスロット 10 メディアを =  
  
-   32 個のスロット 32 の既定値 =  
  
-   32 個のスロット 1 極大サイズ + 1 の大規模な + 1 のメディアを =  
  
-   32 個のスロット = 2 の大きい + 4 のメディアと 6 つの既定値  
  
SQL Server PDW に 6 つの大きな要求が送信され、してから、10 個の既定の要求を送信します。 SQL Server PDW では、次のように優先順位で要求の処理は。  
  
-   メモリが使用可能になるように 4 つの大きな要求の処理を開始する 28 の同時実行スロットを割り当て、キューに 2 つの大きな要求を保持します。  
  
-   4 つの既定の要求の処理を開始する 4 つの同時実行スロットを割り当てるし、待機キューに 6 つの既定の要求を保持します。  
  
要求が完了し、同時実行スロットが利用可能になる、SQL Server PDW では使用可能なリソースと優先順位に従って残りの要求を割り当てます。 たとえば、スロットが開いて 7 の同時実行が存在する場合、大量の要求を待機しているが 7 のスロットの中の要求を待機しているよりも優先します。  6 つのスロットが開く場合は SQL Server PDW は 6 つ以上の既定のサイズ要求を割り当てます。 ただし、メモリと同時実行スロットする必要がありますすべて使用可能な SQL Server PDW の実行要求を許可する前にします。  
  
各リソースのクラス内で、要求は、先入れ先出し (FIFO) 順で最初に実行されます。  
  
## <a name="GeneralRemarks"></a>全般的な解説  
ログインが 1 つ以上のリソース クラスのメンバーである場合は、最も多くのリソースを持つクラスが優先されます。  
  
ログインの追加またはリソースのクラスから削除されるとき、変更ですぐに有効です。 将来のすべての要求実行しているまたは待機されている現在の要求は影響しません。 ログインは、切断して、変更が発生するために再接続する必要はありません。  
  
各ログインのリソース クラスの設定は、個々 のステートメントと操作、およびセッションが適用されます。  
  
SQL Server PDW では、ステートメントが実行される、前に、要求のために必要な同時実行スロットを取得しようとします。 十分な同時実行スロットを取得できない、SQL Server PDW では要求を待機しているのに-を実行する状態に移動します。 要求に既に割り当てられていたすべてのリソース システムがシステムに返されます。  
  
SQL ステートメントの多くは、常に既定のリソース割り当てを必要し、そのため、リソース クラスによって制御されていません。 たとえば、CREATE LOGIN のみ、リソースの量が少ない必要があります、CREATE LOGIN を呼び出してログインのメンバーである場合でも、既定のリソースを割り当てられて、リソース クラスです。  たとえば、Anna largerc リソース クラスのメンバーである場合、CREATE LOGIN ステートメントを送信するユーザーは、CREATE LOGIN ステートメントが既定のリソースの数で実行されます。  
  
SQL ステートメントおよびリソース クラスによって管理される操作:  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   ALTER TABLE REBUILD  
  
-   CREATE CLUSTERED INDEX  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS SELECT  
  
-   CREATE REMOTE TABLE AS SELECT  
  
-   データを読み込むと**dwloader**です。  
  
-   INSERT-SELECT  
  
-   UPDATE  
  
-   DELETE  
  
-   データベースの復元より多くのコンピューティング ノードでアプライアンスに復元するときにします。  
  
-   DMV 専用のクエリを除外するを選択します。  
  
## <a name="Limits"></a>制限事項と制約事項  
リソース クラスは、メモリと同時実行制御の割り当てを制御します。  入力/出力操作の管理を行わない。  
  
## <a name="Metadata"></a>メタデータ  
リソース クラス、およびリソース クラスのメンバーに関する情報を含む Dmv。  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
要求および必要なリソースの状態に関する情報を含む Dmv:  
  
-   [sys.dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys.dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
コンピューティング ノードで、SQL Server の Dmv から公開されている関連するシステム ビューです。 参照してください[SQL Server の動的管理ビュー](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) MSDN でこれらの Dmv へのリンク。  
  
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
  
## <a name="RelatedTasks"></a>関連タスク  
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
  
