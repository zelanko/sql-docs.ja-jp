---
title: "フェールオーバー クラスター インスタンスの SQL Server on Linux |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 229c6a989a4707921eae3046e3c9707b05bb0306
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---

# <a name="failover-cluster-instances---sql-server-on-linux"></a>フェールオーバー クラスター インスタンスの SQL Server on Linux

この記事では、SQL Server フェールオーバー クラスター インスタンス (FCI) を Linux に関連する概念について説明します。 

Linux 上の SQL Server の FCI を作成するを参照してください[Linux 上の SQL Server FCI の構成。](sql-server-linux-shared-disk-cluster-configure.md)

## <a name="the-clustering-layer"></a>クラスタ リングのレイヤー

* RHEL でクラスタ リングの層は Red Hat Enterprise Linux (RHEL) に基づいて[HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)です。 

    > [!NOTE] 
    > Red Hat HA アドオンおよびドキュメントへのアクセスには、サブスクリプションが必要です。 

* SLES、クラスタ リングのレイヤーはに基づいて SUSE Linux Enterprise[高可用性の拡張機能 (HAE)](https://www.suse.com/products/highavailability)です。

    クラスターの構成、リソース エージェント オプション、管理、ベスト プラクティス、および推奨事項の詳細については、次を参照してください。 [SUSE Linux Enterprise 高可用性拡張子 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html)です。

RHEL HA アドオンおよび SUSE HAE の両方に基づいて構築されます[ペース](http://clusterlabs.org/)です。

として、次の図は、記憶域は、2 つのサーバーに表示されます。 -Corosync とペース - クラスタ リングのコンポーネントは、通信およびリソース管理を調整します。 サーバーのいずれかが、記憶域リソース、および SQL Server へのアクティブな接続です。 ペースが障害を検出したときに、クラスタ リングのコンポーネントは、他のノードに、リソースの移動を管理します。  

![Red Hat Enterprise Linux 7 ディスク SQL クラスターの共有](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 


> [!NOTE]
> この時点では、Linux 上のペースで SQL Server の統合は Windows での WSFC でとして結合します。 SQL 内ではありません、クラスターの存在についてのナレッジ、すべてのオーケストレーションが外であり、サービスは、スタンドアロン インスタンスとしてペースによって制御されます。 また、仮想ネットワーク名は、WSFC を特定、相当するのと同じペースではありません。 推測 @ を@servernameと sys.servers クラスター dmv sys.dm_os_cluster_nodes と sys.dm_os_cluster_properties にレコードがないときに、ノード名を返すにします。 文字列のサーバー名を指す接続文字列を使用して、ip アドレスを使用しない、これらには、選択したサーバーの名前 (後述) の仮想 IP リソースを作成するために使用する ip アドレスが DNS サーバーに登録する必要があります。

## <a name="number-of-instances-and-nodes"></a>インスタンスの数およびノード

SQL Server on Linux の主な違いがありますがあることですのみ SQL Server の Linux サーバーごとの 1 つインストールします。 インストールを行うことには、インスタンスが呼び出されます。 つまり、Windows Server フェールオーバー クラスター (WSFC) ごとに最大で 25 個の Fci をサポートする Windows サーバーとは異なり Linux ベースの FCI がのみ 1 つのインスタンス。 この 1 つのインスタンスが既定のインスタンスです。Linux 上の名前付きインスタンスの概念はありません。 

ペース クラスターしか持つことが 16 ノードまで Corosync が関係しているときに 1 つの FCI が最大 16 台のサーバーにまたがることができます。 SQL Server の Standard Edition を使用して実装 FCI は、ペース クラスターに最大 16 ノードがある場合でも、クラスターに最大 2 つのノードをサポートしています。

SQL Server FCI で SQL Server のインスタンスが 1 つのノードか一方でアクティブです。

## <a name="ip-address-and-name"></a>IP アドレスと名前
Linux ペース クラスターでは、各 SQL Server の FCI は独自の一意の IP アドレスと名前を必要があります。 FCI の構成は、複数のサブネットにまたがっている場合、1 つの IP アドレスがサブネットごとに必要になります。 一意の名前と IP アドレスは、アプリケーションとエンドユーザーする必要はありません、ペース クラスターの基になるサーバーが決まっているように、FCI のアクセスに使用されます。

DNS で、FCI の名前は、ペース クラスターの作成を取得する FCI リソースの名前と同じにする必要があります。
名前と IP アドレスの両方を DNS に登録する必要があります。

## <a name="shared-storage"></a>ストレージの共有
すべての Fci では、Linux または Windows Server 上にあるかどうかなんらかの形式の共有記憶域が必要です。 この記憶域が、FCI をホストできる可能性のあるすべてのサーバーに提供されますが、1 台のサーバーのみは特定の時点で、FCI の記憶域を使用することができます。 Linux での共有記憶域に使用できるオプションは次のとおりです。

- iSCSI
- Network File System (NFS)
- サーバー メッセージ ブロック (SMB) Windows Server、多少異なるオプションがあります。 Fci の Linux ベースのサポートされていない 1 つのオプションは、ローカル SQL Server の一時ワークスペースには、TempDB のノードになっているディスクを使用する機能です。

構成では、複数の場所にまたがる、1 つのデータ センターに格納されている情報同期する必要が、他のです。 フェールオーバーが発生した場合、FCI をオンラインにすることができ、同じにする、記憶域を表示します。 これを実現するがいくつかの外部メソッド レプリケーションに必要な記憶域、基になる記憶域のハードウェアまたはソフトウェア ベースの一部のユーティリティを使用して行うことがあるかどうか。 

>[!NOTE]
>SQL Server 2017、直接サーバーに提示する、このようなディスクを使用する Linux ベースの展開を XFS または EXT4 でフォーマットしなければなりません。 他のファイル システムは現在サポートされていません。 ここで、すべての変更が反映されます。

共有記憶域を表すためのプロセスは、別のサポートされているメソッドに対して同じです。

- 共有記憶域を構成します。
- FCI のペース クラスターのノードとして機能するサーバーにフォルダーと記憶域をマウントします。
- 必要に応じて、SQL Server システム データベースを共有記憶域に移動します。
- 共有記憶域に接続されている SQL Server は、各サーバーからテスト

SQL Server on Linux での 1 つの主な違いは、既定のユーザー データとログ ファイルの場所を構成するときに、システム データベース必要があります常が存在するで`/var/opt/mssql/data`です。 Windows server では、TempDB を含めて、システム データベースを移動する機能です。 このファクトは、FCI の再生にどのように共有記憶域が構成されています。

非システム データベースの既定のパスを変更できる、`mssql-conf`ユーティリティです。 既定値を変更する方法について[既定データまたはログ ディレクトリの場所の変更](sql-server-linux-configure-mssql-conf.md#datadir)です。 格納することも SQL Server データ ファイルとトランザクションの他の場所で、既定の場所ではない場合でも、適切なセキュリティがある限り、場所は、指定する必要があります。

次のトピックでは、Linux ベースの SQL Server の FCI のサポートされている記憶域の種類を構成する方法について説明します。

- [フェールオーバー クラスター インスタンス - iSCSI: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [フェールオーバー クラスター インスタンス: NFS - Linux に SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [フェールオーバー クラスター インスタンス: SMB - Linux に SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-smb.md)

