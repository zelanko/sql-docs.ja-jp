---
title: フェールオーバー クラスター インスタンスの SQL Server on Linux |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: e42c5cc42b1b6d0de6d9674070f53df33bda31b4
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705309"
---
# <a name="failover-cluster-instances---sql-server-on-linux"></a>フェールオーバー クラスター インスタンスの SQL Server on Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux に SQL Server フェールオーバー クラスター インスタンス (FCI) に関連する概念を説明します。 

Linux 上の SQL Server FCI を作成するを参照してください[Linux 上の SQL Server FCI の構成。](sql-server-linux-shared-disk-cluster-configure.md)

## <a name="the-clustering-layer"></a>クラスタ リングのレイヤー

* RHEL でクラスタ リングの層は Red Hat Enterprise Linux (RHEL) に基づいて[HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)します。 

    > [!NOTE] 
    > Red Hat HA アドオンとドキュメントへのアクセスには、サブスクリプションが必要です。 

* SLES でのクラスタ リングの階層は SUSE Linux Enterprise に基づいて[高可用性の拡張機能 (HAE)](https://www.suse.com/products/highavailability)します。

    クラスターの構成、リソース エージェントのオプション、管理、ベスト プラクティス、および推奨事項の詳細については、次を参照してください。 [SUSE Linux Enterprise 高可用性拡張子 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html)します。

RHEL HA アドオンと SUSE HAE の両方が上に構築された[Pacemaker](https://clusterlabs.org/)します。

次の図に示すよう、2 つのサーバーに記憶域が表示されます。 -Corosync と Pacemaker - クラスタ リングのコンポーネントは、通信、およびリソース管理を調整します。 サーバーのいずれかが、ストレージ リソースと SQL Server への接続。 Pacemaker は、障害を検出したときにクラスタ リングのコンポーネントは、他のノードに、リソースの移動を管理します。  

![Red Hat Enterprise Linux 7 ディスク SQL クラスターの共有](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 


> [!NOTE]
> この時点では、Linux 上の Pacemaker との SQL Server の統合は、Windows の WSFC でとして結合ではありません。 SQL 内ではありません、クラスターの存在に関する知識と、すべてのオーケストレーションが外部では、サービスは、スタンドアロン インスタンスとして Pacemaker によって制御されます。 また、仮想ネットワーク名は、WSFC を特定、Pacemaker で同じの相当するものはありません。 必要がありますを @@servername sys.servers クラスター dmv sys.dm_os_cluster_nodes と sys.dm_os_cluster_properties にレコードがないときに、ノード名を返すとします。 文字列のサーバー名を指す接続文字列を使用し、ip アドレスを使用しない、選択したサーバー名に置き換えます (次のセクションで説明) と仮想 IP リソースの作成に使用される IP が DNS サーバーに登録する必要があります。

## <a name="number-of-instances-and-nodes"></a>インスタンスとノードの数

SQL Server on Linux で 1 つの重要な違いは、あることにのみ SQL Server の Linux サーバーあたり 1 回のインストールです。 インストールには、インスタンスが呼び出されます。 これは、Windows Server フェールオーバー クラスター (WSFC) ごとに最大 25 の Fci をサポートする Windows Server とは異なり、Linux ベースの FCI のみがされる 1 つのインスタンスを意味します。 この 1 つのインスタンスも既定のインスタンス。Linux 上の名前付きインスタンスの概念はありません。 

Pacemaker クラスターしか持つことが最大 16 ノード Corosync が関係しているときに、1 つの FCI が最大 16 台のサーバーにまたがることができます。 SQL Server の Standard Edition で実装される、FCI は、Pacemaker クラスターに最大 16 ノードがある場合でも、クラスターに最大 2 つのノードをサポートしています。

SQL Server FCI では、SQL Server インスタンスが 1 つのノードまたは他のアクティブです。

## <a name="ip-address-and-name"></a>IP アドレスと名前
Linux の Pacemaker クラスターの各 SQL Server FCI には、独自の一意の IP アドレスと名前が必要があります。 FCI の構成は、複数のサブネットにまたがっている場合、1 つの IP アドレスがサブネットごとに必要になります。 一意の名前と IP アドレスを使用して、FCI にアクセスすると、アプリケーションとエンドユーザーが、Pacemaker クラスターの基になるサーバーを把握する必要はありません。

DNS の FCI の名前、Pacemaker クラスターで作成される FCI リソースの名前と同じことがあります。
名前と IP アドレスを DNS に登録する必要があります。

## <a name="shared-storage"></a>共有記憶域
Linux または Windows Server 上にあるかどうか、すべての Fci 共有記憶域のいくつかの形式が必要です。 このストレージは、FCI をホストできる可能性があるすべてのサーバーに表示されますが、1 台のサーバーは、特定の時点で、FCI の記憶域を使用することができます。 Linux での共有記憶域の使用可能なオプションがあります。

- iSCSI
- Network File System (NFS)
- サーバー メッセージ ブロック (SMB) で Windows Server には多少異なるオプションがあります。 Linux ベースの Fci のサポートされていない 1 つのオプションは、SQL Server の一時ワークスペースには、TempDB のノードに対してローカルなディスクを使用する機能です。

複数の場所にわたる構成で 1 つのデータ センターに格納されている必要がありますと同期、その他。 フェールオーバーが発生した場合、FCI をオンラインにすることになります、同じである記憶域が表示されます。 これを実現する必要があります何らかの外部ストレージ レプリケーションの場合は、基になる記憶域ハードウェアまたはソフトウェア ベースのいくつかのユーティリティを使用して、そのかどうか。 

>[!NOTE]
>For SQL Server では、このようなサーバーに直接表示されるディスクを使用して Linux ベースの展開をか EXT4、XFS でフォーマットされてする必要があります。 他のファイル システムは現在サポートされていません。 ここで、すべての変更が反映されます。

共有記憶域を表示するためのプロセスは、さまざまなサポートされている方法についても同じです。

- 共有記憶域を構成します。
- FCI の Pacemaker クラスターのノードとして機能するサーバーにフォルダーとして、記憶域をマウントします。
- 必要に応じて、SQL Server のシステム データベースを共有記憶域に移動します。
- 共有記憶域に接続されている SQL Server は、各サーバーからテスト

SQL Server on Linux での 1 つの大きな違い既定ユーザー データとログ ファイルの場所を構成するときに、システム データベース必要があります常に存在しないことですで`/var/opt/mssql/data`します。 Windows Server では、TempDB も含め、システム データベースを移動する機能です。 この事実は、fci の再生にどのように共有記憶域が構成されています。

使用してシステム以外のデータベースの既定のパスを変更することができます、`mssql-conf`ユーティリティ。 既定値を変更する方法について[既定データまたはログ ディレクトリの場所を変更する](sql-server-linux-configure-mssql-conf.md#datadir)します。 格納することも SQL Server データおよびトランザクションの他の場所で、既定の場所でない場合でも、適切なセキュリティがある限り、場所は、記述する必要があります。

次のトピックでは、Linux ベースの SQL Server FCI 用にサポートされているストレージの種類を構成する方法について説明します。

- [フェールオーバー クラスター インスタンスの iSCSI - SQL Server on Linux を構成します。](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [NFS - SQL Server on Linux を構成するには、フェールオーバー クラスター インスタンス。](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [フェールオーバー クラスター インスタンス - SMB - SQL Server on Linux の構成します。](sql-server-linux-shared-disk-cluster-configure-smb.md)
