---
title: SQL Server on Linux のパフォーマンスに関するベスト プラクティス
description: この記事では、SQL Server on Linux の実行に関するパフォーマンスのベスト プラクティスとガイドラインを提供します。
author: tejasaks
ms.author: tejasaks
ms.reviewer: vanto
ms.date: 12/11/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 89b8a7c087fb87ed911be640126ec81021b045a7
ms.sourcegitcommit: 2991ad5324601c8618739915aec9b184a8a49c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323513"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>パフォーマンスのベスト プラクティスと SQL Server on Linux の構成ガイドライン

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

この記事では、SQL Server on Linux に接続するデータベース アプリケーションのパフォーマンスを最大化するためのベスト プラクティスと推奨事項について説明します。 これらの推奨事項は、Linux プラットフォームでの実行に固有のものです。 インデックスの設計など、通常の SQL Server の推奨事項はすべて引き続き適用されます。

次のガイドラインには、SQL Server と Linux オペレーティング システム (OS) の両方を構成する場合の推奨事項が含まれています。

## <a name="linux-os-configuration"></a>Linux OS の構成

SQL Server のインストールで最適なパフォーマンスを得るために、次の Linux OS の構成設定を使用することを検討してください。

### <a name="storage-configuration-recommendation"></a>ストレージの構成に関する推奨事項

#### <a name="use-storage-subsystem-with-appropriate-iops-throughput-and-redundancy"></a>適切な IOPS、スループット、冗長性を備えた記憶域サブシステムを使用する

データ、トランザクション ログ、およびその他の関連ファイル (インメモリ OLTP のチェックポイント ファイルなど) をホストする記憶域サブシステムでは、平均とピークのワークロードの両方を適切に管理できる必要があります。 通常、オンプレミス環境では、ストレージ ベンダーにより、適切な IOPS、スループット、冗長性を確保するために複数のディスクでストライピングする適切なハードウェア RAID 構成がサポートされます。 しかし、これはストレージ ベンダーや、さまざまなアーキテクチャを備えたストレージ オファリングによって異なる場合があります。

Azure Virtual Machines にデプロイされた SQL Server on Linux については、適切な IOPS とスループットの要件が確実に満たされるようにソフトウェア RAID の使用を検討してください。 Azure Virtual Machines で SQL Server を構成する場合は、同様のストレージに関する考慮事項について、次の記事を参照してください。[SQL Server VM のストレージの構成](https://docs.microsoft.com/azure/azure-sql/virtual-machines/windows/storage-configuration)

以下は、Azure Virtual Machines 上の Linux でソフトウェア RAID を作成する方法の例です。 以下に例を示しますが、データ、トランザクション ログ、tempdb IO の要件に基づくボリュームに必要なスループットと IOPS に応じて適切な数のデータ ディスクを使用する必要があります。 この例では、8 つのデータ ディスクが Azure 仮想マシンに接続されています。つまり、データ ファイルのホスト用に 4 つ、トランザクション ログ用に 2 つ、tempdb ワークロード用に 2 つです。

```bash
# To locate the devices (for example /dev/sdc) for RAID creation, use the lsblk command
# For Data volume, using 4 devices, in RAID 5 configuration with 8KB stripes
mdadm --create --verbose /dev/md0 --level=raid5 --chunk=8K --raid-devices=4 /dev/sdc /dev/sdd /dev/sde /dev/sdf

# For Log volume, using 2 devices in RAID 10 configuration with 64KB stripes
mdadm --create --verbose /dev/md1 --level=raid10 --chunk=64K --raid-devices=2 /dev/sdg /dev/sdh

# For tempdb volume, using 2 devices in RAID 0 configuration with 64KB stripes
mdadm --create --verbose /dev/md2 --level=raid0 --chunk=64K --raid-devices=2 /dev/sdi /dev/sdj
```

#### <a name="file-system-configuration-recommendation"></a>ファイル システムの構成に関する推奨事項

SQL Server により、データベース、トランザクション ログ、SQL Server 内のインメモリ OLTP のチェックポイント ファイルなどの追加ファイルをホストするための EXT4 と XFS の両方のファイル システムがサポートされます。 Microsoft では、SQL Server のデータ ファイルとトランザクション ログ ファイルをホストするために XFS ファイル システムを使用することをお勧めしています。

```bash
# Formatting the volume with XFS filesystem
mkfs.xfs /dev/md0 -f -L datavolume
mkfs.xfs /dev/md1 -f -L logvolume
mkfs.xfs /dev/md2 -f -L tempdb
```

> [!NOTE]
> XFS ボリュームの作成および書式設定を行うときに、大文字と小文字を区別しないように XFS ファイル システムを構成することができます。 これは Linux エコシステムでよく使用される構成ではありませんが、互換性の理由で使用できます。
>
> 例: mkfs.xfs /dev/md0 -f -n version=ci -L datavolume
>
> この例では、大文字と小文字を区別しないように XFS ファイルシステムを構成するために、`-n version=ci` パラメーターが使用されています。

##### <a name="persistent-memory-filesystem-recommendation"></a>永続メモリ ファイル システムに関する推奨事項

永続メモリ デバイスでのファイル システムの構成の場合、基になるファイル システムのブロック割り当てを 2 MB にする必要があります。 このトピックの詳細については、「[技術的な考慮事項](sql-server-linux-configure-pmem.md#technical-considerations)」の記事を参照してください。

#### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>ファイル システム上で SQL Server のデータ ファイルとログ ファイルについて最終アクセス日時を無効にする

再起動後にシステムに接続されているドライブが確実に自動で再マウントされるように、それらを `/etc/fstab` ファイルに追加する必要があります。 ドライブを参照する場合に、デバイス名 (`/dev/sdc1` など) だけでなく、UUID (汎用一意識別子) を `/etc/fstab` で使用することも強くお勧めします。

SQL Server のデータおよびログ ファイルを格納するために使用される任意のファイル システムで、**noatime** 属性を使用することを強くお勧めします。 この属性を設定する方法については、Linux のドキュメントを参照してください。 Azure 仮想マシンにマウントされているボリュームに対して、**noatime** オプションを有効にする方法の例を以下に示します。

*_/etc/fstab_* のマウント ポイント エントリ

```bash
UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" /data1 xfs,rw,attr2,noatime 0 0
```

上の例では、UUID は _*_blkid_*_ コマンドを使用して見つけることができるデバイスを表します。

#### <a name="sql-server-and-forced-unit-access-fua-io-subsystem-capability"></a>SQL Server と強制ユニット アクセス (FUA) I/O サブシステム機能

サポートされている Linux ディストリビューションには、データの持続性を提供する FUA I/O サブシステム機能をサポートするバージョンがあります。 SQL Server では FUA 機能を使用して、SQL Server のワークロードに対して非常に効率的で信頼性の高い I/O を提供します。 Linux ディストリビューションによる FUA サポートと SQL Server へのその影響について詳しくは、次のブログを参照してください: [SQL Server On Linux: 強制ユニット アクセス (FUA) の内部構造](https://bobsql.com/sql-server-on-linux-forced-unit-access-fua-internals/)

SUSE Linux Enterprise Server 12 SP5 および Red Hat Enterprise Linux 8.0 以降では、I/O サブシステムで FUA 機能がサポートされています。 SQL Server 2017 CU6 以降または SQL Server 2019 を使う場合は、SQL Server による FUA でのハイ パフォーマンスで効率的な I/O 実装に対して、次の構成を使用する必要があります。

次の条件が満たされている場合は、以下に一覧表示されている推奨構成を使用します。

- SQL Server 2017 CU6 以降、または SQL Server 2019 の使用
- FUA 機能をサポートする Linux ディストリビューションとバージョン (Red Hat Enterprise Linux 8.0 以上、または SUSE Linux Enterprise Server 12 SP5) の使用
- FUA 機能をサポートし、そのために構成されている記憶域サブシステムやハードウェア上

推奨構成: 

1. 起動時のパラメーターとしてトレース フラグ 3979 を有効にします
2. *mssql-conf* を使用して、`control.writethrough = 1` と `control.alternatewritethrough = 0` を構成します

上記の条件を満たさない他のほぼすべての構成については、次のように構成することをお勧めします。

1. 確実にトレース フラグ 3979 が起動時のパラメーターとして有効になっていないことを認識したうえで、トレース フラグ 3982 を起動時のパラメーターとして有効にします (Linux エコシステムの SQL Server に対する既定値)
2. **mssql-conf** を使用して、`control.writethrough = 1` と `control.alternatewritethrough = 1` を構成します

### <a name="kernel-and-cpu-settings-for-high-performance"></a>ハイ パフォーマンスのためのカーネルおよび CPU の設定

以下のセクションでは、SQL Server インストールのハイ パフォーマンスとスループットに関する推奨される Linux OS 設定について説明します。 これらの設定を構成するプロセスについては、Linux OS のドキュメントを参照してください。 説明に従って [**_Tuned_*](https://tuned-project.org) を使用すると、以下で説明する多くの CPU とカーネルを構成するのに役立ちます。

#### <a name="using-__tuned__-to-configure-kernel-settings"></a>_*_Tuned_*_ を使用してカーネル設定を構成する

Red Hat Enterprise Linux (RHEL) のユーザーの場合、[Tuned](https://tuned-project.org) スループットパフォーマンス プロファイルで、(C-States を除く) 一部のカーネルおよび CPU 設定が自動的に構成されます。 RHEL 8.0 以降、*mssql* という名前の _*_Tuned_*_ プロファイルは Red Hat と共に共同開発されたものであり、これにより、SQL Server ワークロードのより詳細な Linux のパフォーマンス関連の調整が提供されます。 このプロファイルには、RHEL のスループット パフォーマンス プロファイルが含まれており、このプロファイルを使用しない他の Linux ディストリビューションおよび RHEL リリースについて確認できるように、定義を以下に示します。

SUSE Linux Enterprise Server 12 SP5、Ubuntu 18.04、Red Hat Enterprise Linux 7.x の場合は、**_Tuned_*パッケージを手動でインストールできます。以下の説明のとおり、これを使用して* mssql** プロファイルを作成および構成することができます。

##### <a name="proposed-linux-settings-using-a-tuned-mssql-profile"></a>Tuned mssql プロファイルを使用した Linux 設定の提案

```bash
#
# A Tuned configuration for SQL Server on Linux
#

[main]
summary=Optimize for Microsoft SQL Server
include=throughput-performance

[cpu]
force_latency=5

[sysctl]
vm.swappiness = 1
vm.dirty_background_ratio = 3
vm.dirty_ratio = 80
vm.dirty_expire_centisecs = 500
vm.dirty_writeback_centisecs = 100
vm.transparent_hugepages=always
# For multi-instance SQL deployments, use
# vm.transparent_hugepages=madvise
vm.max_map_count=1600000
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048576
kernel.numa_balancing=0
kernel.sched_latency_ns = 60000000
kernel.sched_migration_cost_ns = 500000
kernel.sched_min_granularity_ns = 15000000
kernel.sched_wakeup_granularity_ns = 2000000
```

この Tuned プロファイルを有効にするには、これらの定義を `/usr/lib/tuned/mssql` フォルダー以下の **tuned.conf** ファイルに保存し、次のコマンドを使用して、そのプロファイルを有効にします。

```bash
chmod +x /usr/lib/tuned/mssql/tuned.conf
tuned-adm profile mssql
```

次のコマンドを使用して有効になっていることを確認します。

```bash
tuned-adm active
```

または

```bash
tuned-adm list
```

#### <a name="cpu-settings-recommendation"></a>CPU 設定に関する推奨事項

次の表に、CPU 設定に関する推奨事項を示します。

| 設定 | 値 | 詳細情報 |
|---|---|---|
| CPU 周波数ガバナー | パフォーマンス | **cpupower** コマンドを参照してください |
| ENERGY_PERF_BIAS | パフォーマンス | **x86_energy_perf_policy** コマンドを参照してください |
| min_perf_pct | 100 | intel p-state に関するドキュメントを参照してください |
| C-States | C1 のみ | C-States が C1 のみに確実に設定する方法については、Linux またはシステムのドキュメントを参照してください |

前述のとおり、**_Tuned_ *を使用すると、CPU 周波数ガバナー、ENERGY_PERF_BIAS、および min_perf_pct の設定が適切に自動で構成されます。これは、* mssql** プロファイルのベースとして、スループットパフォーマンス プロファイルが使用されているためです。 C-States パラメーターは、Linux またはシステム ディストリビューターによって提供されるドキュメントに従って手動で構成する必要があります。

#### <a name="disk-settings-recommendations"></a>ディスク設定に関する推奨事項

次の表に、ディスク設定に関する推奨事項を示します。

| 設定 | 値 | 詳細情報 |
|---|---|---|
| ディスク `readahead` | 4096 | `blockdev` コマンドを参照してください |
| sysctl の設定 | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness = 1 | **sysctl** コマンドを参照してください |

**説明:**

- **vm.swappiness**: このパラメーターで、SQL Server のプロセス メモリ ページをスワップ アウトするようにカーネルを制限することで、ランタイム メモリをスワップ アウトするための相対的な重みを制御します。

- **vm.dirty_\** _: SQL Server ファイルの書き込みアクセスはキャッシュされないため、そのデータの整合性要件が満たされます。 これらのパラメーターを使用すると、効率的な非同期書き込みパフォーマンスを実現し、フラッシュを調整しながら十分な大きさのキャッシュを許可することで Linux での書き込みのキャッシュのストレージ IO への影響を軽減できます。

- _*kernel.sched_\**_: これらのパラメーター値は、Linux カーネルの Completely Fair Scheduling (CFS) アルゴリズムを微調整するための現在の推奨事項を表します。これにより、スレッドのプロセス間のプリエンプションと再開に関して、ネットワークおよびストレージの IO 呼び出しのスループットが向上します。

_*mssql* *_Tuned_*_ プロファイルを使用して、_vm.swappiness、vm.dirty_\* *_ および* kernel.sched_\** の設定を構成します。 `blockdev` コマンドを使用したディスク `readahead` 構成はデバイスごとに行われるため、手動で実行する必要があります。

#### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>マルチノード NUMA システムのカーネル設定の自動 numa バランシング

マルチノード *NUMA* システムに SQL Server をインストールすると、次の **kernel.numa_balancing** カーネル設定が既定で有効になります。 **NUMA** システムの効率を最大になるように SQL Server を運用するには、マルチノード NUMA システムでの自動 numa バランシングを無効にします。

```bash
sysctl -w kernel.numa_balancing=0
```

**mssql** **_Tuned_ *_ プロファイルを使用して、_* kernel.numa_balancing** オプションを構成します。

#### <a name="kernel-settings-for-virtual-address-space"></a>仮想アドレス空間のカーネル設定

**vm.max_map_count** の既定の設定 (65536) は、SQL Server のインストールに十分な大きさではない可能性があります。 このような理由から、SQL Server デプロイについては **vm.max_map_count** 値を少なくとも 262144 に変更します。これらのカーネル パラメーターをさらに調整する場合は、「[Tuned mssql プロファイルを使用した Linux 設定の提案](#proposed-linux-settings-using-a-tuned-mssql-profile)」セクションを参照してください。 vm.max_map_count の最大値は 2147483647 です。

```bash
sysctl -w vm.max_map_count=1600000
```

**mssql** **_Tuned_ *プロファイルを使用して、* vm.max_map_count** オプションを構成します。

#### <a name="leave-transparent-huge-pages-thp-enabled"></a>Transparent Huge Pages (THP) を有効なままにする

ほとんどの Linux インストールでは、このオプションが既定でオンです。 この構成オプションは有効なままにしておくことをお勧めします。 しかし、たとえば、複数のインスタンスがある SQL Server デプロイでメモリ ページング アクティビティが高い場合や、サーバー上にメモリを多く使用するアプリケーションが他にある SQL Server 実行の場合は、次のコマンドを実行した後、アプリケーションのパフォーマンスをテストすることをお勧めします。

```bash
echo madvise > /sys/kernel/mm/transparent_hugepage/enabled
```

または、次の行を使用して、**mssql** **_Tuned_* プロファイルを変更します。

```bash
vm.transparent_hugepages=madvise
```

また、変更後に *mssql* プロファイルがアクティブになるようにします。

```bash
tuned-adm off
tuned-adm profile mssql
```

**mssql** **_Tuned_ *プロファイルを使用して、* transparent_hugepage** オプションを構成します。

#### <a name="additional-advanced-kernelos-configuration"></a>その他の高度なカーネルおよび OS の構成

1. 最適なストレージ IO パフォーマンスを得るために、ブロック デバイスに Linux マルチキュー スケジューリングを使用することをお勧めします。 これにより、高速ソリッドステート ドライブ (SSD) およびマルチコア システムを使用して、ブロック レイヤーのパフォーマンスを適切にスケーリングすることができます。 Linux ディストリビューションで既定で有効になるかどうかは、ドキュメントでご確認ください。 その他のほとんどの場合は、**scsi_mod.use_blk_mq=y** を使用してカーネルを起動すると有効になります。ただし、使用している Linux ディストリビューションのドキュメントには追加のガイダンスが含まれる場合があります。 これは、アップストリームの Linux カーネルと一致しています。

1. マルチパス IO は SQL Server のデプロイによく使用されるため、**dm_mod.use_blk_mq=y** カーネル ブート オプションを有効にすることで、デバイス マッパー (DM) マルチパス ターゲットも `blk-mq` インフラストラクチャを使用するように構成する必要があります。 既定値は `n` (無効) です。 基になる SCSI デバイスで `blk-mq` が使用される場合、この設定により、DM レイヤーでのロックのオーバーヘッドが減ります。 構成方法に関する追加のガイダンスについては、使用している Linux ディストリビューションのドキュメントを参照してください。

#### <a name="configure-swapfile"></a>スワップ ファイルの構成

メモリ不足の問題を回避するには、swapfile が適切に構成されていることを確認します。 swapfile の作成方法と適切なサイズ設定方法については、Linux のドキュメントを参照してください。

#### <a name="virtual-machines-and-dynamic-memory"></a>仮想マシンと動的メモリ

仮想マシンで SQL Server on Linux を実行する場合は、その仮想マシン用に予約されているメモリの量を修正するオプションを必ず選択してください。 Hyper-V 動的メモリのような機能は使用しないでください。

## <a name="sql-server-configuration"></a>SQL Server の構成

アプリケーションで最高のパフォーマンスを実現するには、SQL Server on Linux をインストールした後で、次の構成タスクを実行することをお勧めします。

### <a name="best-practices"></a>ベスト プラクティス

- **ノードまたは CPU に PROCESS AFFINITY を使用する**

   Linux OS 上の SQL Server (通常はすべてのノードと CPU) に使用しているすべての **NUMANODE** と CPU、またはそのいずれかに `ALTER SERVER CONFIGURATION` を使用して `PROCESS AFFINITY` を設定することをお勧めします。 プロセッサ関係は、効率的な Linux および SQL スケジューリングの動作を維持するために役立ちます。 **NUMANODE** オプションを使用するのが最も簡単な方法です。 コンピューター上に NUMA ノードが 1 つしかない場合でも、**PROCESS AFFINITY** を使用します。 [PROCESS AFFINITY](../t-sql/statements/alter-server-configuration-transact-sql.md) の設定方法について詳しくは、**ALTER SERVER CONFIGURATION** に関する記事を参照してください。

- **複数の tempdb データ ファイルを構成する**

   SQL Server on Linux のインストールには複数の tempdb ファイルを構成するオプションが用意されていないため、インストール後に複数の tempdb データ ファイルを作成することを検討することをお勧めします。 詳細については、「[Tempdb データベースを SQL Server に割り当て時の競合を減らすための推奨事項](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d)」を参照してください。

### <a name="advanced-configuration"></a>高度な構成

次の推奨事項は、SQL Server on Linux のインストール後に選択できるオプションの構成設定です。 これらの選択肢は、ご利用の Linux OS のワークロードと構成の要件に基づいています。

- **mssql-conf を使用してメモリ制限を設定する**

   Linux OS に十分な空き物理メモリを確保するために、SQL Server プロセスには既定で物理 RAM の 80% のみが使用されます。 物理 RAM のサイズが大きな一部のシステムの場合、20% でも大きな数値になることがあります。 たとえば、1 TB の RAM が搭載されたシステムでは、既定の設定では約 200 GB の RAM が未使用のままになります。 このような状況では、メモリの制限をより大きな値に構成することができます。 **mssql-conf** ツールと、SQL Server に表示されるメモリ (MB 単位) を制御する [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit) 設定のドキュメントを参照してください。

   この設定を変更する場合は、この値を高く設定しすぎないように注意してください。 十分なメモリを残さないと、Linux OS やその他の Linux アプリケーションで問題が発生するおそれがあります。

## <a name="next-steps"></a>次のステップ

パフォーマンスを向上させる SQL Server の機能の詳細については、「[パフォーマンス機能の概要](sql-server-linux-performance-get-started.md)」を参照してください。

Linux 上の SQL Server の詳細については、「[SQL Server on Linux の概要](sql-server-linux-overview.md)」を参照してください。
