---
title: "Linux 上の SQL Server のパフォーマンスのベスト プラクティス |Microsoft ドキュメント"
description: "このトピックでは、Linux で SQL Server 2017 を実行するパフォーマンスのベスト プラクティスとガイドラインを提供します。"
author: rgward
ms.author: bobward
manager: craigg
ms.date: 09/14/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 565ede5c15f6e4e34a7a5cbbdcd6fa7d145c8ff5
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-2017-on-linux"></a>パフォーマンスのベスト プラクティスと Linux 上の SQL Server 2017 の構成ガイドライン

このトピックでは、ベスト プラクティスと推奨事項を Linux に SQL Server に接続するデータベース アプリケーションのパフォーマンスを最大化を提供します。 これらの推奨事項は、Linux プラットフォームで実行されているに固有です。 インデックスのデザインなどに、すべての標準 SQL Server 勧告が引き続き適用されます。

次のガイドラインには、SQL Server と Linux のオペレーティング システムの両方を構成するための推奨事項が含まれています。

## <a name="sql-server-configuration"></a>SQL Server の構成

アプリケーションに最適なパフォーマンスを実現するために Linux に SQL Server をインストールした後、次の構成タスクを実行することをお勧めします。

### <a name="best-practices"></a>ベスト プラクティス

- **ノード、またはその両方の Cpu プロセス関係を使用します。**

   使用することをお勧め`ALTER SERVER CONFIGURATION`を設定する`PROCESS AFFINITY`すべてに対して、 **NUMANODEs** Cpu 使用している SQL Server (一般的にこれはすべてのノードと Cpu) の Linux オペレーティング システム上またはします。 プロセッサのアフィニティにより、効率的な Linux および SQL のスケジュール設定の動作を維持できます。 使用して、 **NUMANODE**オプションは、最も簡単な方法です。 ただし、使用する必要があります**プロセス関係**お使いのコンピューターに 1 つの NUMA ノードのみがある場合でもです。  参照してください、 [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md)を設定する方法の詳細についてはドキュメント**プロセス関係**です。

- **複数の tempdb データ ファイルを構成します。**

   Linux オペレーティング システム上の SQL Server が複数の tempdb ファイルを構成するオプションを提供していないために、インストール後に複数の tempdb データ ファイルの作成を検討することをお勧めします。 詳細については、記事のガイダンスを参照してください。[を SQL Server tempdb データベース内の割り当ての競合を減らすために推奨事項](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d)です。

### <a name="advanced-configuration"></a>高度な構成

次の推奨事項は、Linux に SQL Server のインストール後に実行することを選択するオプションの構成設定です。 これらのオプションは、ワークロードと構成、Linux オペレーティング システムの要件に基づいています。

- **Mssql conf メモリの制限を設定します。**

   十分な空き物理メモリの Linux オペレーティング システムがあることを確認するには、するためには、SQL Server プロセスは、既定では、物理メモリの 80% だけを使用します。 どの大量物理 RAM の 20% の可能性があります、一部のシステムの数が多い。 たとえば、システムでは 1 TB の RAM の既定の設定はのままに約 200 GB の RAM 未使用。 このような状況では、値を大きくメモリ制限を構成することができます。 ドキュメントを参照して、 **mssql conf**ツールおよび[memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit)メモリ (mb 単位) で SQL Server に表示を制御する設定。

   この設定を変更する場合は、高すぎるこの値を設定しないように注意します。 十分なメモリが残っていない場合、Linux オペレーティング システムおよびその他の Linux アプリケーションの問題が発生する可能性があります。

## <a name="linux-os-configuration"></a>Linux OS の構成

SQL Server のインストールのパフォーマンスを最高のエクスペリエンスに次の Linux オペレーティング システム構成設定を使用してください。

### <a name="kernel-settings-for-high-performance"></a>高パフォーマンスのカーネル設定
これらは、推奨される Linux オペレーティング システムの設定を [高] に関連するパフォーマンスと、SQL Server インストールのスループット。 これらの設定を構成するプロセスの Linux オペレーティング システムのドキュメントを参照してください。



> [!Note]
> Red Hat Enterprise Linux (RHEL) ユーザーの場合、スループットのパフォーマンス プロファイルは自動的に (を除く C 状態を)、これらの設定を構成します。

次の表は、CPU の設定に関する推奨事項を示します。

| 設定 | [値] | 詳細情報 |
|---|---|---|
| CPU 頻度ガバナー | パフォーマンス | 参照してください、 **cpupower**コマンド |
| ENERGY_PERF_BIAS | パフォーマンス | 参照してください、 **x86_energy_perf_policy**コマンド |
| min_perf_pct | 100 | Intel p 状態で、ドキュメントをご覧ください。 |
| C 状態 | C1 のみ | C 状態に設定されている C1 のみを確保する方法の Linux またはシステムのマニュアルを参照してください。 |

次の表は、ディスクの設定に関する推奨事項を示します。

| 設定 | [値] | 詳細情報 |
|---|---|---|
| ディスク先行 | 4096 | 参照してください、 **blockdev**コマンド |
| sysctl 設定 | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness=10 | 参照してください、 **sysctl**コマンド |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>分散マルチノード NUMA システムのカーネル設定自動 numa

複数のノードに SQL Server をインストールする場合**NUMA**システムの場合、次**kernel.numa_balancing**カーネル設定が既定で有効にします。 SQL Server の効率を最大で動作するように、 **NUMA**システム、分散 NUMA システムの複数のノードを無効にする自動 numa:

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>カーネルの仮想アドレス空間の設定

既定の設定の**vm.max_map_count** (これは 65536) できない可能性があります、SQL Server インストールに必要な大きさです。 256 K にする (上限) この値を変更します。

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>最後にアクセスされる日付/時刻ファイル システム上の SQL Server データ ファイルとログ ファイルを無効にします。

使用して、 **noatime**およびログ ファイルの SQL Server データの格納に使用される任意のファイル システムの属性です。 この属性を設定する方法の Linux のマニュアルを参照してください。

### <a name="leave-transparent-huge-pages-thp-enabled"></a>透過的な大きなページ (THP) 有効なままにしてください。

Linux の多くのインストールは、既定は、このオプションが必要です。 一貫性のある最もパフォーマンスの状態はこの構成オプションを有効になっているをお勧めします。

### <a name="swapfile"></a>スワップ ファイル

メモリ不足の問題を回避するスワップ ファイルが正しく構成されていることを確認します。 作成し、スワップ ファイルの適切なサイズの方法について、Linux のドキュメントを参照してください。

### <a name="virtual-machines-and-dynamic-memory"></a>仮想マシンと動的メモリ

を実行している SQL Server on Linux 仮想マシンの場合は、仮想マシン用に予約されたメモリの量を修正するオプションを選択することを確認します。 HYPER-V 動的メモリなどの機能を使用しません。

## <a name="next-steps"></a>次の手順

パフォーマンスを向上させる SQL Server 機能の詳細については、次を参照してください。[パフォーマンス機能の概要](sql-server-linux-performance-get-started.md)です。

Linux 上の SQL Server に関する詳細については、次を参照してください。 [Linux に SQL Server の概要](sql-server-linux-overview.md)です。
