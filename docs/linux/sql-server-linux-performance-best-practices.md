---
title: Linux 上の SQL Server のパフォーマンスのベスト プラクティス |Microsoft ドキュメント
description: このトピックでは、Linux で SQL Server 2017 を実行する場合の、パフォーマンスのベスト プラクティスとガイドラインを提供します。
author: rgward
ms.author: bobward
manager: craigg
ms.date: 09/14/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: a0e9c5dde8f5bc9ef2e8a7ac285a8152b0c34e9c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 のパフォーマンスについてのベスト プラクティスと構成ガイドライン

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このトピックでは、Linux 上の SQL Server に接続するデータベース アプリケーションのパフォーマンスを最大化するための、ベスト プラクティスと推奨事項を提供します。 これらの推奨事項は、Linux プラットフォームで実行されている場合に特化しています。 インデックスのデザインなどの、すべての一般的な SQL Server の推奨事項は引き続き適用されます。

次のガイドラインには、SQL Server と Linux のオペレーティング システムの両方を構成するための推奨事項が含まれています。

## <a name="sql-server-configuration"></a>SQL Server の構成

アプリケーションで最適なパフォーマンスを実現するために Linux に SQL Server をインストールした後、次の構成タスクを実行することをお勧めします。

### <a name="best-practices"></a>ベスト プラクティス

- **ノード および/または CPU に PROCESS AFFINITY を使用します**

   `ALTER SERVER CONFIGURATION`を使用して、 Linux オペレーティング システム上の SQL Server で使用しているすべての**NUMANODEs**および/または CPU  (一般的にはすべてのノードと CPU) に対して`PROCESS AFFINITY`を設定することをお勧めします。 プロセッサのアフィニティにより、効率的に Linux および SQL のスケジューリングの動作を維持することができます。 **NUMANODE**オプションを使用することが、最も簡単な方法です。 お使いのコンピューターに NUMA ノードが 1 つのみの場合でも、**PROCESS AFFINITY**を使用する必要があることにご注意ください。  **PROCESS AFFINITY**を設定する方法の詳細については、次のドキュメントを参照してください。[ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md)

- **複数の tempdb データ ファイルを構成します**

   Linux 上の SQL Server では複数の tempdb ファイルを構成するオプションを提供していないため、インストール後に複数の tempdb データ ファイルの作成を検討することをお勧めします。 詳細については、次の記事のガイダンスを参照してください。[SQL Server の tempdb データベース内の割り当ての競合を減らすための推奨事項](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d)

### <a name="advanced-configuration"></a>高度な構成

次の推奨事項は、Linux に SQL Server をインストールした後に実行することができる省略可能な構成設定です。 ワークロードの要件とLinux オペレーティング システムの構成に基づいて選択します。

- **mssql-conf でメモリの制限を設定します**

   Linux オペレーティング システムで、十分な空き物理メモリを確保するために、既定では、SQL Server プロセスは、物理メモリの 80% のみを使用します。 いくつかの大量の物理 RAM のシステムでは、20% はかなり大きい可能性があります。 たとえば、1 TB の RAM システムの既定の設定では、約 200 GB の RAM が未使用となります。 このような状況では、メモリ制限の値をより高く構成することができます。 **mssql conf**ツールおよび、SQL Server のメモリの設定 (MB 単位) を制御する [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit)のドキュメントを参照してください。

   この設定を変更する場合は、高すぎる値を設定しないように注意します。 十分なメモリが残っていない場合、Linux オペレーティング システムおよびその他の Linux アプリケーションで問題が発生する可能性があります。

## <a name="linux-os-configuration"></a>Linux OS の構成

次の Linux オペレーティング システム構成設定を使用して、SQL Server インストール環境のパフォーマンスを最大限にすることを検討してください。

### <a name="kernel-settings-for-high-performance"></a>高パフォーマンスのカーネル設定
これらは、SQL Server インストール環境の高パフォーマンスとスループットに関連する、Linux オペレーティング システムで推奨される設定です。 これらの設定を構成するプロセスについては Linux オペレーティング システムのドキュメントを参照してください。



> [!Note]
> Red Hat Enterprise Linux (RHEL) ユーザーの場合、スループットのパフォーマンス プロファイルは自動的に (C-States を除く)、これらの設定を構成します。

次の表は、CPU の設定に関する推奨事項を示します。

| 設定 | 値 | 詳細情報 |
|---|---|---|
| CPU 周波数ガバナー | パフォーマンス | **cpupower**コマンドを参照してください |
| ENERGY_PERF_BIAS | パフォーマンス | **x86_energy_perf_policy**コマンドを参照してください |
| min_perf_pct | 100 | intel p-state のドキュメントを参照してください |
| C-States | C1 Only | C-States が C1 のみに設定されていることを確認する方法については、Linux またはシステムのマニュアルを参照してください |

次の表は、ディスクの設定に関する推奨事項を示します。

| 設定 | 値 | 詳細情報 |
|---|---|---|
| ディスクの先行読み込み | 4096 | **blockdev**コマンドを参照してください |
| sysctl 設定 | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns 15000000 を =<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness=10 | **sysctl**コマンドを参照してください |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>マルチノード NUMA システムの自動 NUMA バランシングのカーネル設定

複数ノードの **NUMA**システムに SQL Server をインストールする場合、次の**kernel.numa_balancing** カーネル設定が既定で有効になります。 **NUMA**システム上でSQL Server が最高の効率で動作するように、複数ノードの NUMA システムで、自動 NUMA バランシングを無効にします。

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>カーネルの仮想アドレス空間の設定

既定の設定の**vm.max_map_count** (65536) はSQL Server インストール環境では十分な大きさではない可能性があります。 この値を (上限となる) 256K に変更します。

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>SQL Server データ ファイルとログ ファイルのファイル システム上の最後にアクセスされた日付/時刻を無効にする

SQL Server のデータおよびログ ファイルを格納するファイル システムでは、**noatime** 属性を使用します。 この属性を設定する方法は Linux のマニュアルを参照してください。

### <a name="leave-transparent-huge-pages-thp-enabled"></a>透過的な大きなページ (THP) を有効なままにしてください

多くの Linux のインストールでは、このオプションが既定で有効です。 最も一貫性のあるパフォーマンスの状態とするため、この構成オプションは有効にしておくことをお勧めします。

### <a name="swapfile"></a>スワップ ファイル

メモリ不足の問題を回避するため、スワップ ファイルが、正しく構成されていることを確認します。 スワップ ファイルを作成し適切なサイズを設定する方法については、Linux のドキュメントを参照してください。

### <a name="virtual-machines-and-dynamic-memory"></a>仮想マシンと動的メモリ

仮想マシンで SQL Server on Linux を実行している場合は、仮想マシン用に予約されたメモリの量を修正するオプションが選択されていることを確認します。 HYPER-V 動的メモリなどの機能を使用しないでください。

## <a name="next-steps"></a>次の手順

パフォーマンスを向上させる SQL Server 機能の詳細については、次を参照してください。[パフォーマンス機能の概要](sql-server-linux-performance-get-started.md)です。

Linux 上の SQL Server に関する詳細については、次を参照してください。 [Linux の SQL Server の概要](sql-server-linux-overview.md)です。
