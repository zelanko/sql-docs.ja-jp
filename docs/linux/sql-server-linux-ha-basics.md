---
title: Linux デプロイの SQL Server 可用性の基礎 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 85ea90343ebf1cac9ba04a4b9252a6dd9fb748bf
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52533072"
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>Linux デプロイの SQL Server 可用性の基礎

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

以降で[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]は Linux と Windows の両方でサポートされています。 などの Windows ベース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]展開では、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]データベースとインスタンスが Linux で高可用性にする必要があります。 この記事の計画と高可用性展開の技術的な側面をでは Linux ベース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]データベース インスタンスとの違いは Windows ベースのインストールの一部。 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]可能性がありますの新機能で Linux の専門家、および Linux の可能性があります新しい[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]プロフェッショナル、この記事はも一部になじみや他のユーザーによく知らない可能性のある概念でいます。

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Linux デプロイの可用性オプション
バックアップと復元、だけでなく同じ 3 つの可用性機能は Windows ベースの展開の場合と Linux で利用可能です。
-   Always On 可用性グループ (Ag)
-   Always On フェールオーバー クラスター インスタンス (Fci)
-   [ログ配布](sql-server-linux-use-log-shipping.md)

Windows、Fci は基になる Windows Server フェールオーバー クラスター (WSFC) 常に必要です。 展開のシナリオに応じて、AG 通常必要があります基になる WSFC では、新しい例外ででバリアント[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]します。 WSFC は Linux ではありません。 Linux での実装をクラスタ リングは、セクションで説明[Linux 上の Always On 可用性グループとフェールオーバー クラスターの Pacemaker インスタンス](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux)します。

## <a name="a-quick-linux-primer"></a>Linux 入門
インターフェイスでは、いくつかの Linux インストールをインストールできる、ほとんどはそうでないコマンド ラインを使用して、オペレーティング システム レイヤーでほぼすべてを行うことを意味します。 このコマンドラインは、Linux の世界での一般的な用語は、 *bash シェル*します。

Linux では、多くのコマンドは、管理者として Windows Server で実行する必要がある多くのことと同じように、昇格された特権で実行する必要があります。 昇格した特権で実行する 2 つの主な方法はあります。
1. 適切なユーザーのコンテキストで実行します。 を別のユーザーに変更するコマンドを使用して、`su`します。 場合`su`を単独で実行せず、ユーザー名、パスワードを知っている限りするようになりますとしてシェル*ルート*します。
   
2. 処理を実行する詳細について共通とセキュリティ意識の高い方法は、使用する`sudo`何も実行する前にします。 この例の多くの記事使用`sudo`します。

オンライン、各種のスイッチがあり、オプションのそれぞれの一般的なコマンドを調査することができます。
-   `cd` -ディレクトリを変更
-   `chmod` -ファイルまたはディレクトリのアクセス許可の変更
-   `chown` -ファイルまたはディレクトリの所有権を変更します。
-   `ls` -ディレクトリの内容を表示します。
-   `mkdir` -ドライブ上のフォルダー (ディレクトリ) の作成
-   `mv` -1 つの場所からファイルを移動
-   `ps` -すべての作業プロセスを表示します。
-   `rm` -サーバーのローカル ファイルを削除
-   `rmdir` -フォルダー (ディレクトリ) の削除
-   `systemctl` -開始、停止、またはサービスを有効にします。
-   テキスト エディター コマンド。 Linux では、vi、emacs などのさまざまなテキスト エディター オプションがあります。

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>可用性の構成に関する一般的なタスク[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]on Linux
ここでは、Linux ベースのすべてに共通するタスク[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]展開します。

### <a name="ensure-that-files-can-be-copied"></a>ファイルがコピーされることを確認します。
1 つのサーバー間でファイルをコピーするタスクを使用してユーザーが[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]on Linux では操作を実行できます。 このタスクは、AG 構成の非常に重要です。

Linux および Windows ベースのインストール、アクセス許可の問題のようなものが存在できます。 ただし、Windows のサーバーから別のサーバーにコピーする方法を使い慣れていないがあります on Linux での実行方法について熟知。 一般的なメソッドはコマンド ライン ユーティリティを使用して、 `scp`、セキュリティで保護されたコピーの略です。 バック グラウンドで`scp`OpenSSH を使用します。 SSH は、セキュリティで保護されたシェルの略です。 Linux ディストリビューションに応じて自体 OpenSSH をインストールしない可能性があります。 そうでない場合、OpenSSH を最初にインストールする必要があります。 OpenSSH の構成の詳細については、各ディストリビューションは、次のリンクで情報を参照してください。
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-OpenSSH.html)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

使用する場合`scp`、ソースまたは変換先ではない場合は、サーバーの資格情報を指定する必要があります。 たとえば、使用します。

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

MyAGCert.cer ファイルを他のサーバーで指定されたフォルダーにコピーします。 アクセス許可 - と可能性があるため、コピーするファイルの所有権のされている必要がありますに注意してください`chown`コピーする前に使用する必要もあります。 同様に、受信側では、適切なユーザーと、ファイルを操作するアクセスが必要です。 たとえば、その証明書ファイルを復元するため、`mssql`ユーザーがアクセスできる必要があります。

サーバー メッセージ ブロック (SMB) の Linux バリアントには、samba がなどの UNC パスからアクセスする共有を作成することもでき`\\SERVERNAME\SHARE`します。 Samba の構成の詳細については、各ディストリビューションは、次のリンクで情報を参照してください。
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

SMB 共有の Windows に基づくこともできます。SMB 共有を Linux サーバーのホストで Samba のクライアント部分が正しく構成されていれば、Linux ベースにする必要はありません[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]しが適切なアクセスを共有します。 既存のインフラストラクチャを活用する方法の 1 つなりますにとって混在環境では、Linux ベース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]展開します。

重要なことの 1 つは、Samba のデプロイのバージョンに準拠している SMB 3.0 があることです。 SMB のサポートを追加したときに[!INCLUDE[sssql11-md](../includes/sssql11-md.md)]、SMB 3.0 をサポートするすべての共有が必要です。 Samba を使用して、共有と Windows サーバーではなく場合、Samba ベース共有は SMB 3.1.1 をサポートする Samba 4.0 またはそれ以降と理想的には 4.3 以降、使用する必要があります。 SMB および Linux 上の情報の適切なソースが[Samba で SMB3](https://events.linuxfoundation.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf)します。

最後に、ネットワーク ファイル システム (NFS) 共有を使用して、オプションです。 Windows ベースの展開のオプションでない NFS を使用して[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]、Linux ベースのデプロイのみ使用できます。

### <a name="configure-the-firewall"></a>ファイアウォールの構成
Windows と同様に、Linux ディストリビューションには、組み込みのファイアウォールがあります。 会社は、サーバーに外部ファイアウォールを使用して、Linux でのファイアウォールを無効にする可能性があります許容されます。 ただし、ファイアウォールが有効になっているに関係なくポートが開かれている必要があります。 次の表に、文書化に必要な共通ポート高可用性[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux にデプロイします。

| [ポート番号] | 型     | 説明                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS- `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | 使用する場合に samba にエンドポイント マッパー                                                                                          |
| 137         | UDP      | 使用する場合に samba - NetBIOS 名のサービス                                                                                      |
| 138         | UDP      | 使用する場合に samba - NetBIOS データグラム                                                                                          |
| 139         | TCP      | 使用する場合に samba - NetBIOS セッション                                                                                           |
| 445         | TCP      | 使用する場合に samba - TCP 経由で SMB                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -既定のポートです。必要な場合で変更できます。 `mssql-conf set network.tcpport <portnumber>`                       |
| 2049        | TCP、UDP | NFS (使用) する場合                                                                                                               |
| 2224        | TCP      | Pacemaker の使用 `pcsd`                                                                                                |
| 3121        | TCP      | Pacemaker - Pacemaker リモート ノードがあるかどうかに必要な                                                                    |
| 3260        | TCP      | 変更できます (使用) する場合は、イニシエーターの iSCSI `/etc/iscsi/iscsid.config` (RHEL)、iSCSI ターゲットのポートに一致する必要がありますが、 |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -既定のポートを AG エンドポイント; の使用エンドポイントを作成するときに変更することができます。                                |
| 5403        | TCP      | Pacemaker                                                                                                                   |
| 5404        | UDP      | Pacemaker - UDP マルチキャストを使用する場合は、Corosync で必要                                                                     |
| 5405        | UDP      | Pacemaker - Corosync で必要                                                                                            |
| 21064       | TCP      | Pacemaker - DLM を使用してリソースに必要な                                                                                 |
| 変数    | TCP      | 可用性グループのエンドポイント ポート。既定値は 5022                                                                                           |
| 変数    | TCP      | NFS のポートを`LOCKD_TCPPORT`(で見つかった`/etc/sysconfig/nfs`on RHEL)                                              |
| 変数    | UDP      | NFS のポートを`LOCKD_UDPPORT`(で見つかった`/etc/sysconfig/nfs`on RHEL)                                              |
| 変数    | TCP/UDP  | NFS のポートを`MOUNTD_PORT`(で見つかった`/etc/sysconfig/nfs`on RHEL)                                                |
| 変数    | TCP/UDP  | NFS のポートを`STATD_PORT`(で見つかった`/etc/sysconfig/nfs`on RHEL)                                                 |

Samba を使用できる追加のポートでは、次を参照してください。 [Samba ポートの使用状況](https://wiki.samba.org/index.php/Samba_Port_Usage)します。

逆に、Linux でのサービスの名前も追加できます。 ポートではなく、例外としてたとえば、 `high-availability` Pacemaker 用です。 この方向を追求する場合は、名前のディストリビューションを参照してください。 たとえば、RHEL で Pacemaker で追加するコマンドは

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**ファイアウォールのドキュメント:**
-   [RHEL](https://access.redhat.com/documentation/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>インストール[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]可用性のためのパッケージ
Windows ベースの[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]インストールでは、他のユーザーは、基本的なエンジンのインストールにもいくつかのコンポーネントがインストールされます。 Linux のみで、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エンジンがインストール プロセスの一部としてインストールされます。 他のすべては省略可能です。 高可用性[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux では、インスタンス、2 つのパッケージをインストールする必要があります[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]:[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] エージェント (*mssql server エージェント*) と高可用性 (HA) パッケージ (*mssql server-ha*)。 中に[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントは、技術的には省略可能な[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]のジョブのスケジューラと、ログ配布に必要なインストールをお勧めします。 Windows ベースのインストールで[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントは省略できません。

>[!NOTE]
>初めての人の[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントが[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]の組み込みのジョブ スケジューラ。 これは、バックアップやその他のスケジュールを設定する一般的な方法[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]メンテナンスします。 Windows ベースのインストールとは異なり[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]場所[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントは、Linux 上のまったく異なるサービス[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]のコンテキストでエージェントが実行される[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]自体。

Windows ベースの構成に Ag または Fci を構成すると、クラスター対応されます。 クラスター対応という[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]が特定のリソース Dll (sqagtres.dll と Fci を使用する ag hadrres.dll の sqsrvres.dll) について、WSFC が認識していると、WSFC によってことを確認するために使用、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]クラスター化された機能を実行していると正常に機能します。 クラスタ リングが外部ないためだけに[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]が Linux 自体、Microsoft と同等の Linux ベースの可用性グループおよび FCI の展開のリソース DLL をコーディングする必要があります。 これは、 *mssql server-ha*パッケージ化とも呼ばれる、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]の Pacemaker リソース エージェント。 インストールする、 *mssql server-ha*パッケージは、「 [HA と SQL Server エージェント パッケージをインストールする](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages)します。

その他のオプションのパッケージの[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]linux では、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] 、フルテキスト検索 (*mssql-サーバー-fts*) と[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Integration Services (*mssql server は*)、いません。FCI または AG のいずれかの高可用性のために必要です。

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Always On 可用性グループと Linux 上のフェールオーバー クラスター インスタンスの pacemaker
以前のように注意して、現在 Ag および Fci の Microsoft でサポートされている唯一のクラスタ リング メカニズムが Corosync と Pacemaker。 ここでは、ソリューション、および計画および展開にする方法について理解する基本的な情報[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]構成します。

### <a name="ha-add-onextension-basics"></a>HA アドオンの/拡張機能の基礎
現在サポートされているディストリビューション全体は出荷、高可用性アドオン-の/拡張機能、Pacemaker のスタックをクラスタ リングに基づいています。 このスタックには、2 つの主要コンポーネントが組み込まれています。Pacemaker と Corosync します。 スタックのすべてのコンポーネントは次のとおりです。
-   Pacemaker - クラスター化されたマシン間で座標のような処理を実行するには、コンポーネントをクラスタ リングのコア。
-   Corosync のフレームワークとクォーラム、プロセスの再起動に失敗しましたなどの機能などが提供する Api のセット。
-   libQB - ログ記録のようなものを提供します。
-   リソース エージェント - 特定の機能が提供されるため、アプリケーションは、Pacemaker を統合できます。
-   エージェント - スクリプト/ノードを特定するを支援し、それらの問題が生じている場合、対処する機能を柵します。
    
> [!NOTE]
> クラスター スタックは、Linux の世界で Pacemaker とも呼ばれます。

このソリューションは、いくつかの方法は、類似するものでは異なる Windows を使用してクラスター化された構成の展開から多くの点では。 Windows、Windows Server フェールオーバー クラスター (WSFC) と呼ばれる、クラスタ リングの可用性フォームは、オペレーティング システム、およびフェールオーバー クラスタ リング、WSFC を作成できるように、既定で無効にする機能に組み込まれています。 Windows、Ag と Fci、WSFC の上に構築され、共有の緊密な統合、特定のリソース DLL によって提供されるため[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 この密に結合されたソリューションは 1 つのベンダーからすべてであるためと考えられるです。

![](./media/sql-server-linux-ha-basics/image1.png)

Linux では、サポートされている各配布に使用可能な Pacemaker があるときに各ディストリビューション カスタマイズし、若干異なる実装とバージョンがあります。 違いの一部は、この記事の手順に反映されます。 クラスタ リングの層は、オープン ソース、ディストリビューションに含まれている場合でもが緊密に統合されていないと同じ方法で WSFC が Windows の下。 Microsoft は、このため*mssql server-ha*ように[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]と Pacemaker スタックを閉じるには、提供できますがまったく同じですが発生する Ag と Fci Windows 下でします。

Pacemaker の完全なドキュメントについては、すべてが完全なリファレンスについては、RHEL および SLES の使用の詳細な説明を含めます。
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Ubuntu の可用性のためのガイドではありません。

スタック全体の詳細についても参照してください、公式[Pacemaker ドキュメント ページ](https://clusterlabs.org/doc/)Clusterlabs サイト。

### <a name="pacemaker-concepts-and-terminology"></a>Pacemaker の概念と用語
このセクションでは、一般的な概念と Pacemaker の実装を使用する用語を説明します。

#### <a name="node"></a>ノード
ノードは、クラスターに参加しているサーバーです。 Pacemaker クラスターでは、最大 16 ノードがネイティブでサポートします。 Corosync は、他のノードで実行されていませんが、Corosync に必要な場合、この回数を超過できます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 クラスターのいずれかのノードの最大数ではそのため、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-ベースの構成は 16。 これは、Pacemaker の制限であり、Ag または Fci によって課される最大の制限事項とは無関係に、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 

#### <a name="resource"></a>リソース
WSFC と Pacemaker クラスターの両方のリソースの概念があります。 リソースは、ディスクまたは IP アドレスなど、クラスターのコンテキストで実行されている特定の機能です。 たとえば、Pacemaker で FCI と AG の両方のリソースを作成を取得できます。 これは複数の異なる表示されている、WSFC 内の処理ではありません、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] fci のいずれかのリソースや、AG を構成するときに、可用性グループ リソースが一致しない方法で基になる違いにより、同じ[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Pacemaker と統合されます。

Pacemaker には、standard、およびクローンのリソースがあります。 複製のリソースは、すべてのノードで同時に実行されるものです。 例は、負荷分散のための複数のノードで実行されている IP アドレスになります。 Fci 用に作成されるすべてのリソースは、1 つのノードは、特定の時点、FCI をホストできるため、標準のリソースを使用します。

AG が作成されたときに、特殊な形式の複数の状態のリソースと呼ばれる複製リソースが必要です。 AG では、1 つのプライマリ レプリカのみが、AG 自体を実行しているすべてのノードで、作業するように構成し、読み取り専用アクセスなどを許可する可能性があることができます。 これは、ノードの「ライブ」の使用であるため、リソースが 2 つの状態の概念をある: マスターおよびスレーブします。 詳細については、次を参照してください。[リソースの複数の状態。複数のモードが存在するリソース](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html)します。

#### <a name="resource-groupssets"></a>リソース グループ/セット
WSFC 内のロールと同様に、Pacemaker クラスターには、リソース グループの概念があります。 (SLES のセットと呼ばれます) のリソース グループとは、共に機能して、1 つの単位として別に 1 つのノードからフェールオーバーできるリソースのコレクションです。 リソース グループは、マスター/スレーブ; として構成されているリソースを含めることはできません。したがって、Ag を使用できません。 リソース グループは、Fci を使用できますは一般に推奨される構成です。

#### <a name="constraints"></a>制約
Wsfc では、リソースと依存関係は、2 つの異なるリソース間の親子リレーションシップの WSFC の通知などのさまざまなパラメーターを指定します。 依存関係は、どのリソースが最初にオンラインにする必要がある、WSFC を通知規則だけです。

Pacemaker クラスターには、依存関係の概念はありませんが、制約があります。 制約の 3 つの種類があります: コロケーション、場所、および順序付けします。
-   コロケーションの制約は、2 つのリソースは、同じノードで実行する必要があるかどうかを適用します。
-   場所の制約は、リソースできます (またはできません) 実行される場所、Pacemaker クラスターを指示します。
-   順序付けの制約は、Pacemaker クラスター リソースの開始に使用する必要があります、順序を指示します。

> [!NOTE]
> コロケーション制約は、1 つの単位として認識されるすべてのため、リソース グループ内のリソースの必要ではありません。

#### <a name="quorum-fence-agents-and-stonith"></a>クォーラム、フェンス エージェント、および STONITH
Pacemaker でクォーラムが概念的に、WSFC に少し似ています。 クラスターのクォーラムの全体的な目的では、クラスターが稼働してままになることを確認します。 WSFC と Linux ディストリビューションの HA アドオンの両方がある、投票の概念クォーラムに対する各ノードがカウントされます。 投票の過半数、それ以外の場合、最悪のシナリオでは、クラスターのシャット ダウン。

WSFC の場合とは異なりは、クォーラムを使用するミラーリング監視サーバーのリソースはありません。 WSFC でのような目的は、投票者奇数の数を保持します。 クォーラム構成では、Fci の Ag のさまざまな考慮事項があります。

Wsfc は、参加しているノードの状態を監視し、問題が発生したときに、それらを処理します。 Wsfc の以降のバージョンが不適切な動作になったりするノードを検疫などの機能を提供する (ノードに含まれていない、ネットワーク通信がダウンなど)。 Linux の側では、この種の機能は、フェンス エージェントによって提供されます。 概念は、フェンスとも呼ばれます。 ただし、これらのフェンス エージェントは、展開に一般的に固有でありハードウェア ベンダーとハイパーバイザーを提供するものなど、一部のソフトウェア ベンダーによって提供される多くの場合。 たとえば、VMware vSphere を使用して仮想化された Linux Vm 用に使用できるフェンス エージェントを提供します。

クォーラムと ties を別の概念にフェンス STONITH と呼ばれるまたは先頭に、その他のノードを撮影します。 すべての Linux ディストリビューションでサポートされている、Pacemaker クラスターが存在する STONITH が必要です。 詳細については、次を参照してください。 [Red Hat 高可用性クラスター フェンス](https://access.redhat.com/solutions/15575)(RHEL)。

#### <a name="corosyncconf"></a>corosync.conf
`corosync.conf`ファイルには、クラスターの構成が含まれています。 ある`/etc/corosync`します。 通常の日常業務の過程で、このファイルは、クラスターが正しく設定されている場合に編集することはありません必要です。

#### <a name="cluster-log-location"></a>クラスター ログの場所
Pacemaker クラスターのログの場所は、ディストリビューションによって異なります。
-   RHEL および SLES- `/var/log/cluster/corosync.log`
-   -Ubuntu `/var/log/corosync/corosync.log`

既定のログ ファイルの場所を変更する変更`corosync.conf`します。

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Pacemaker クラスターを計画します。 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
このセクションでは、Pacemaker クラスターの場合は、重要な計画点について説明します。

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Linux ベースの仮想化の Pacemaker クラスターします。 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Linux ベースのデプロイに仮想マシンを使用して[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Ag および Fci の展開は、Windows ベースの対応と同じ規則でカバーされます。 サポート性の規則の基本セットがある仮想化された[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]で Microsoft によって提供される展開[Microsoft サポート KB 956893](https://support.microsoft.com/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment)します。 マイクロソフトの Hyper-v ホストと VMware の ESXi などの異なるハイパーバイザーでは、プラットフォーム自体の違いにより、別の差異をそこに、があります。

Ag を Fci での仮想化に関しては、アンチ アフィニティが、特定の Pacemaker クラスターのノードに対して設定されていることを確認します。 ホストする Vm を高可用性の AG または FCI の構成では、構成されている場合[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]同じハイパーバイザー ホスト上で実行されることはありません。 たとえば、2 つのノードの FCI が展開されている場合は必要があります*少なくとも*など Live の 3 つのハイパーバイザー ホストになるようにホストの障害が発生した場合に、ノードをホストする Vm のいずれかの機能を使用する場合に特に移行や vmotion を使用します。

詳細についてを参照してください。
-   Hyper V のドキュメント -[ゲスト クラスタ リングの高可用性を使用します。](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   ホワイト ペーパーで記述された Windows ベースの展開がまだ概念のほとんどを適用) -[計画高可用性、ミッション クリティカルな SQL Server の展開では、VMware vSphere](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

>[!NOTE]
>STONITH を使用した Pacemaker クラスターと RHEL が HYPER-V でまだサポートされていません。 詳細と、更新、サポートされてまでを参照してください[RHEL 高可用性クラスターのサポート ポリシー](https://access.redhat.com/articles/29440#3physical_host_mixing)します。

### <a name="networking"></a>ネットワーク
WSFC の場合とは異なり Pacemaker は必要ありません、専用の名または少なくとも 1 つの専用 IP アドレス、Pacemaker クラスター自体の。 Ag と Fci (詳細については、各ドキュメントを参照してください)、IP アドレスが必要になりますが、いない名、ネットワーク名リソースがないためです。 SLES での管理のために、IP アドレスの構成は許可されていることがでわかるように、必要でない[Pacemaker クラスターを作成する](sql-server-linux-deploy-pacemaker-cluster.md#create)します。

WSFC でのように Pacemaker を希望冗長ネットワークは、個別のネットワーク カード (Nic または物理 pNICs) つまり個々 の IP アドレスを持ちます。 クラスターの構成の観点から各 IP アドレスは、独自のリングと呼ばれる必要があります。 ただし、Wsfc で現在、多くの実装が仮想化またはパブリック クラウドに 1 つだけがサーバーに提示する NIC (vNIC) を仮想化が本当にあります。 すべての pNICs と Vnic が同じ物理または仮想スイッチに接続されている場合はありません完全な冗長性、ネットワーク層での仮想マシンにフィルターの種類のビットは、複数の Nic を構成するため。 ネットワークの冗長性は、仮想化の展開では、ハイパーバイザーには、通常組み込まれているし、パブリック クラウドに間違いなく組み込まれています。

複数の Nic と WSFC と Pacemaker の違いの 1 つは、Pacemaker が、同じサブネットに複数の IP アドレスを許可、WSFC は実行されません。 複数のサブネットと Linux クラスターの詳細については、この記事を参照してください。[複数のサブネットを構成する](sql-server-linux-configure-multiple-subnet.md)します。

### <a name="quorum-and-stonith"></a>クォーラムと STONITH
クォーラム構成および要件に関連する AG または FCI 固有の展開の[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。

STONITH は、Pacemaker クラスターのサポートされている必要があります。 STONITH を構成するのにには、分布からドキュメントを使用します。 例が、[ストレージ ベースのフェンス操作](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html)SLES 用です。 VMware vCenter の ESXI ベースのソリューションの STONITH エージェントもあります。 詳細については、次を参照してください。 [VMWare VM VCenter SOAP のフェンス用 (Unofficial) Stonith プラグイン エージェント](https://github.com/olafrv/fence_vmware_soap)します。

> [!NOTE]
> この記事の執筆時点で、HYPER-V は STONITH のソリューションをありません。 これはオンプレミスのデプロイメントの場合は true であり、RHEL などの特定のディストリビューションを使用して Pacemaker の Azure ベースの展開にも影響を与えます。

### <a name="interoperability"></a>相互運用性
このセクションでは、Linux ベースのクラスターが WSFC または Linux のディストリビューションをやり取りする方法を説明します。

#### <a name="wsfc"></a>WSFC
現時点では、連携して動作するには、WSFC と Pacemaker クラスターの直接的な方法はありません。 これは、AG または WSFC と Pacemaker の間で機能する FCI を作成する方法がないことを意味します。 ただし、Ag 用に設計されたどちらも、2 つの相互運用性ソリューションがあります。 FCI は、クロス プラットフォームの構成に参加できる唯一の方法は、これら 2 つのシナリオの 1 つのインスタンスとして参加しているかどうか。
-   None のクラスターの種類での AG です。 詳細については、Windows を参照してください。[可用性グループのドキュメント](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)します。
-   これは特殊な種類を独自の可用性グループとして構成する 2 つの異なる Ag を許可する可用性グループの分散型 AG 分散型可用性グループの詳細については、ドキュメントを参照してください。[分散型可用性グループ](../database-engine/availability-groups/windows/distributed-availability-groups.md)します。

#### <a name="other-linux-distributions"></a>他の Linux ディストリビューション
Linux では、Pacemaker クラスターのすべてのノードは、同一のディストリビューションにある必要があります。 たとえば、RHEL ノードは SLES ノードを持つ Pacemaker クラスターの一部であることは。 この主な理由が前に示した: ディストリビューションが可能性がさまざまなバージョンと機能、処理が正しく動作しない可能性があります。 Wsfc と Linux の混在と同じストーリーがディストリビューションを混在させる: なし を使用するか、Ag を分散します。

## <a name="next-steps"></a>次の手順
[SQL Server on Linux のペース クラスターを展開します。](sql-server-linux-deploy-pacemaker-cluster.md)
