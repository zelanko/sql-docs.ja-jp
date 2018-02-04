---
title: "Linux 環境の SQL Server 可用性の基本 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: d53e54c6e8e74970316de557ddf3bd60a09e9ffe
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>Linux 展開用の SQL Server 可用性の基礎

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

以降で[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]は Linux と Windows の両方でサポートされています。 などの Windows ベース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]展開では、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]データベースおよびインスタンスが Linux で高可用性にする必要があります。 この記事の計画と可用性の高い展開の技術的な側面を説明する Linux ベース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]データベースとインスタンス、さらに Windows ベースのインストールからの違いの一部です。 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Linux 専門家、および Linux 場合がありますの新機能について新しいもあります[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]技術者、アーティクル時点が導入されていますの概念をいくつかになじみや他のユーザーによく知らない場合があります。

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux の展開の可用性オプション
バックアップや復元だけでなく、同じ 3 つの可用性機能は、Windows ベースの展開と Linux 入手できます。
-   Always On 可用性グループ (Ag)
-   Always On フェールオーバー クラスター インスタンス (Fci)
-   [ログ配布](sql-server-linux-use-log-shipping.md)

Windows では、Fci は、基になる Windows Server フェールオーバー クラスター (WSFC) を常に必要です。 デプロイメントのシナリオによって、AG 通常必要があります、基になる WSFC されて、新しい例外でバリアント[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]です。 Linux では、WSFC がありませんでした。 Linux での実装をクラスタ リングについては下[on Linux インスタンスの Always On 可用性グループおよびフェールオーバー クラスターのペース](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux)です。

## <a name="a-quick-linux-primer"></a>Linux の入門
Linux のインストールによってはインターフェイスでインストールされているときにほとんどではありません、コマンドラインを使用してオペレーティング システムのレイヤーでほぼすべてを行うことを意味します。 Linux の世界でコマンド プロンプトの一般的な用語は、 *bash シェル*です。

Linux では、多くのコマンドは、管理者として Windows Server で実行する必要があります、さまざまなものと同じように、昇格された特権を使って実行する必要があります。 昇格した特権で実行する 2 つの主な方法はあります。
1. 適切なユーザーのコンテキストで実行します。 別のユーザーに変更するには、コマンドを使用`su`です。 場合`su`がそれ自体で実行される、username、パスワードを知っている限りするようになりますとしてシェル*ルート*です。
   
2. 使用する処理を実行する複数の一般的なとセキュリティ意識の高い方法は、`sudo`何も実行する前にします。 この例の多くの記事を使用して`sudo`です。

一般的なコマンド、各種のスイッチとオンラインの研究オプションがある各:
-   `cd`– ディレクトリを変更
-   `chmod`– ファイルまたはディレクトリのアクセス許可の変更
-   `chown`– ファイルまたはディレクトリの所有権を変更します。
-   `ls`– ディレクトリの内容を表示します。
-   `mkdir`– ドライブ上のフォルダー (ディレクトリ) の作成
-   `mv`– ファイルを別の 1 つの場所に移動
-   `ps`– 作業プロセスをすべて表示
-   `rm`– サーバーのローカルにファイルを削除
-   `rmdir`– フォルダー (ディレクトリ) を削除します。
-   `systemctl`– 開始、停止、またはサービスを有効にします。
-   テキスト エディター コマンド。 Linux では、vi emacs など、さまざまなテキスト エディター オプションがあります。

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>可用性の構成に関する一般的なタスク[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]on Linux
ここでは、すべての Linux ベースに共通するタスク[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]展開します。

### <a name="ensure-that-files-can-be-copied"></a>ファイルをコピーできることを確認してください。
1 つの点を使用してユーザー [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] on Linux を実行可能にする必要がありますは別に 1 つのサーバーからファイルをコピーします。 このタスクは、AG の構成が重要です。

Linux および Windows ベースのインストール、アクセス許可の問題などが存在できます。 ただし、Windows 上のサーバーをコピーする方法をよく知っている可能性がありますいないに習熟 Linux 上の実行方法。 一般的な方法は、コマンド ライン ユーティリティを使用する`scp`、セキュリティで保護されたコピーの略です。 背後では、 `scp` OpenSSH を使用します。 SSH は、セキュリティで保護されたシェルを表しています。 Linux ディストリビューションに応じて OpenSSH 自体がインストールされていません。 そうでない場合は、OpenSSH を最初にインストールする必要があります。 OpenSSH を構成する方法については、次のリンクの各配布に情報を参照してください。
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-OpenSSH.html)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

使用する場合`scp`、ソースまたは変換先ではない場合は、サーバーの資格情報を指定する必要があります。 たとえばを使用します。

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

その他のサーバーで指定されたフォルダーに MyAGCert.cer ファイルをコピーします。 注: アクセス許可と可能性がありますので、コピーするファイルの – 所有権されている必要があります`chown`をコピーする前に使用する必要があります。 同様に、受信側では、適切なユーザーでは、ファイルを操作するアクセスに必要です。 たとえば、その証明書ファイルを復元するため、`mssql`ユーザーがアクセスできる必要があります。

Samba で、サーバー メッセージ ブロック (SMB) の Linux バリアントがあるを使用してなどの UNC パスでアクセスの共有を作成することもできます`\\SERVERNAME\SHARE`です。 Samba を構成する方法については、次のリンクの各配布に情報を参照してください。
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

SMB 共有の Windows ベースも使用できます。SMB 共有は、samba クライアント部分が Linux サーバーのホストで正しく構成されている限り、Linux ベースである必要はありません[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]しが適切なアクセスを共有します。 混在環境に該当する場合の既存のインフラストラクチャを活用する方法の 1 つになります Linux ベース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]展開します。

重要となる 1 つの点は、展開 Samba のバージョンが準拠している SMB 3.0 をする必要があります。 SMB をサポートを追加したときに[!INCLUDE[sssql11-md](../includes/sssql11-md.md)]、SMB 3.0 をサポートするすべての共有が必要です。 Samba を使用して、共有および Windows サーバーではなく場合、Samba ベースの共有が SMB 3.1.1 をサポートする Samba 4.0 またはそれ以降、および理想的には 4.3 以降を使用する必要があります。 SMB および Linux 上の情報を適切なソースが[Samba で SMB3](http://events.linuxfoundation.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf)です。

最後に、ネットワーク ファイル システム (NFS) 共有の使用は、オプションです。 NFS を使用して上の Windows ベースの展開オプションではありません[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]、Linux ベースの展開にのみ使用できます。

### <a name="configure-the-firewall"></a>ファイアウォールの構成
Windows と同様に、Linux ディストリビューション組み込みのファイアウォールがあります。 会社は、外部サーバーへファイアウォールを使用して、linux のファイアウォールを無効にする可能性があります許容可能です。 ただし、ファイアウォールが有効になるに関係なくポートが開かれる必要があります。 次の表に、ドキュメントに必要な一般的なポート高可用性[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux 上に展開します。

| [ポート番号] | 型     | Description                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS – `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | (使用する場合) を samba – エンドポイント マッパー                                                                                          |
| 137         | UDP      | (使用する場合) を samba – NetBIOS ネーム サービス                                                                                      |
| 138         | UDP      | (使用する場合) を samba – NetBIOS データグラム                                                                                          |
| 139         | TCP      | (使用する場合) を samba – NetBIOS セッション                                                                                           |
| 445         | TCP      | (使用する場合) を samba – TCP 経由で SMB                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] – 既定のポートです。必要な場合で変更できます。`mssql-conf set network.tcpport <portnumber>`                       |
| 2049        | TCP、UDP | NFS (使用する場合)                                                                                                               |
| 2224        | TCP      | によって使用される – ペース`pcsd`                                                                                                |
| 3121        | TCP      | ペース – ペース リモート ノードがあるかどうかに必要な                                                                    |
| 3260        | TCP      | iSCSI イニシエーター (使用する場合) – は内で変更されることができます`/etc/iscsi/iscsid.config`(RHEL)、iSCSI ターゲットのポートに一致する必要がありますが、 |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -既定のポートは、AG エンドポイントの使用エンドポイントを作成するときに変更することができます。                                |
| 5403        | TCP      | ペース                                                                                                                   |
| 5404        | UDP      | UDP マルチキャストを使用する場合、Corosync によって必要 – ペース                                                                     |
| 5405        | UDP      | ペース – Corosync で必要                                                                                            |
| 21064       | TCP      | DLM を使用してリソースに必要な – ペース                                                                                 |
| 変数    | TCP      | 可用性グループのエンドポイント ポートです。既定値は 5022                                                                                           |
| 変数    | TCP      | ポートはポートを NFS – `LOCKD_TCPPORT` (で見つかった`/etc/sysconfig/nfs`RHEL 上)                                              |
| 変数    | UDP      | ポートはポートを NFS – `LOCKD_UDPPORT` (で見つかった`/etc/sysconfig/nfs`RHEL 上)                                              |
| 変数    | TCP/UDP  | ポートはポートを NFS – `MOUNTD_PORT` (で見つかった`/etc/sysconfig/nfs`RHEL 上)                                                |
| 変数    | TCP/UDP  | ポートはポートを NFS – `STATD_PORT` (で見つかった`/etc/sysconfig/nfs`RHEL 上)                                                 |

追加のポートは Samba で使用できますを参照してください[Samba ポートの使用状況](https://wiki.samba.org/index.php/Samba_Port_Usage)です。

逆に、Linux 上でサービスの名前も追加できます。 ポートの代わりに例外としてたとえば、`high-availability`ペースのです。 この方向を追求する場合は、名前のディストリビューションを参照してください。 たとえば、RHEL ペースで追加するコマンドは

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**ファイアウォールのドキュメント:**
-   [RHEL](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>インストール[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]可用性のためのパッケージ
Windows ベースの[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]インストール、他のユーザーがないときに、基本的なエンジンのインストールにもいくつかのコンポーネントがインストールされます。 Linux、のみで、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エンジンは、インストール プロセスの一部としてインストールします。 他のすべては省略できます。 高可用性[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]linux インスタンス、2 つのパッケージでインストールしてください[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]:[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェント (*mssql server エージェント*) と高可用性 (HA) パッケージ (*mssql サーバー-ha*)。 中に[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントは、技術的には省略可能な[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]のジョブのスケジューラと、ログ配布に必要なため、インストールをお勧めします。 Windows ベースのインストールで[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントは省略できません。

>[!NOTE]
>初めて使用するものの[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントが[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]の組み込みのジョブのスケジューラです。 バックアップおよびその他のようなものをスケジュールする Dba 向けの一般的な方法は[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]保守します。 Windows ベースのインストールとは異なり[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]場所[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェントは、Linux 上のまったく異なるサービス[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]のコンテキストでエージェントが実行される[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]自体です。

Ag または Fci を構成したら、Windows ベースの構成で、クラスター対応はします。 クラスター対応という[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)](sqagtres.dll および Fci、Ag の hadrres.dll の sqsrvres.dll) は、WSFC を知っている Dll の特定のリソースがあり、WSFC によってことを確認するために使用、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]クラスター化された機能を実行していると正常に機能します。 クラスタ リングが外部ないためだけに[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux 自体、Microsoft がコードの Linux ベースの AG と FCI の展開のリソース DLL の該当するショートカットは、する必要があるが、します。 これは、 *mssql サーバー-ha*パッケージ化とも呼ばれる、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ペースのリソースのエージェントです。 インストールする、 *mssql サーバー-ha*パッケージは、「 [HA および SQL Server エージェント パッケージをインストールする](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages)です。

その他の省略可能なパッケージは、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Linux では、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] 、フルテキスト検索 (*mssql サーバー-fts*) および[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Integration Services (*mssql サーバーが*)、されません。FCI は、または、AG のいずれかの高可用性のために必要です。

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Always On 可用性グループおよび Linux でのフェールオーバー クラスター インスタンスのペース
前述のように、Corosync とペースは現在の Ag と Fci を Microsoft でサポートされている唯一のクラスタ リング メカニズムです。 ここでは、ソリューション、および計画およびをできるように配置する方法について理解する基本的な情報[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]構成します。

### <a name="ha-add-onextension-basics"></a>HA のアドオンと拡張の基本事項
現在サポートされている分布のすべて付属して、高可用性アドオン-の/拡張機能は、スタックをクラスタ リングのペースに基づいています。 このスタックには、次の 2 つの主なコンポーネントが組み込まれています: ペースと Corosync です。 スタックのすべてのコンポーネントは次のとおりです。
-   ペース – コアのクラスター化されたマシン間で座標のような処理を実行するコンポーネントをクラスター化します。
-   Corosync-framework とクォーラム、プロセスの再起動に失敗しましたというようにする機能などを提供する Api のセット。
-   libQB – 提供などのログ記録をします。
-   リソース エージェント – アプリケーションがペースと統合できるようにするための特定の機能です。
-   エージェント – スクリプト/機能のノードを切り分けるために役立ちますし、問題が発生している場合とその対処を柵します。
    
> [!NOTE]
> クラスターのスタックは、Linux の世界でペースとも呼ばれます。

このソリューションはのようないくつかの方法で Windows を使用してクラスター化された構成を展開する異なるさまざまな方法でです。 Windows では、Windows Server フェールオーバー クラスター (WSFC) と呼ばれる、クラスタ リングの可用性のフォームは、オペレーティング システム、および、WSFC では、フェールオーバー クラスタ リングの作成できるように、既定で無効にする機能に組み込まれてです。 Windows では、Ag と Fci、WSFC の上に構築された、特定のリソース DLL が提供するための緊密な統合を共有[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 この密に結合されたソリューションは、1 つのベンダーからすべてになっているためと考えられる。

![](./media/sql-server-linux-ha-basics/image1.png)

Linux では、サポートされている各配布に使用可能なペースがあるときに各配布カスタマイズし、わずかに異なる実装とバージョンがあります。 違いの一部は、この記事の指示に反映されます。 オープン ソースは、クラスタ リングの層は、のディストリビューションに含まれている場合でも、緊密に統合されていない同じ方法でそのため、WSFC は、windows の場合。 これは、ため、マイクロソフトが提供*mssql サーバー-ha*できるように、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]とに近いペース スタックを提供できますが、正確に一致しない、同じ場合は、発生の Ag と Fci の Windows の下にあるようにします。

ペースで完全なドキュメントについては、RHEL、SLES の完全な参照情報にはすべての詳細な説明を含みます。
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Ubuntu の可用性のためのガイドではありません。

全体の履歴に関する詳細については、公式にも表示[ペース ドキュメント ページ](http://clusterlabs.org/doc/)Clusterlabs サイトです。

### <a name="pacemaker-concepts-and-terminology"></a>ペースの概念と用語
このセクションでは、一般的な概念と、ペースの実装の用語を説明します。

#### <a name="node"></a>ノード
ノードは、クラスターに参加しているサーバーです。 ペース クラスターには、16 ノードまでネイティブでサポートされます。 Corosync が他のノードで実行されていませんが、Corosync に必要な場合は、この数を超過する可能性が[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 したがって、ノードの最大数のいずれか、クラスターが持つことができます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-ベースの構成は 16 です。 このペースの制限は、Ag または Fci によって課される最大の制限を行うには関係ありません[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 

#### <a name="resource"></a>リソース
WSFC とペース クラスターの両方のリソースの概念があります。 リソースは、ディスクまたは IP アドレスなど、クラスターのコンテキストで実行されている特定の機能です。 たとえば、ペースで FCI と可用性グループの両方のリソースを作成を取得できます。 これは、参照先の wsfc の処理とは異なるではありません、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]か、FCI のまたは、可用性グループを構成するときに、可用性グループ リソースがないまったく同じである、基になる方法の違いにより[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ペースと統合します。

ペースでは、standard、およびクローンのリソースがあります。 複製のリソースは、すべてのノードで同時に実行したものです。 例は、負荷分散の目的での複数のノードで実行されている IP アドレスになります。 1 つのノードは、特定の時点で、FCI をホストできるため、Fci の作成を取得したすべてのリソースは、標準的なリソースを使用します。

AG の作成時に、特殊な形式の複数の状態のリソースと呼ばれる複製リソースが必要です。 AG には、1 つのプライマリ レプリカのみが、AG 自身を実行しているすべてのノードで、作業するように構成しなどの読み取り専用アクセスを許可する可能性があることができます。 あるために、これは、ノードの「ライブ」を使用して、リソース、2 つの状態の概念: マスター/スレーブです。 詳細については、次を参照してください。[複数の状態のリソース: リソースを複数のモードを持つ](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html)します。

#### <a name="resource-groupssets"></a>リソース グループ/設定
ペース クラスターが、リソース グループの概念、WSFC 内のロールと同様に、します。 (SLES のセットと呼ばれます)、リソース グループは、連携機能を 1 つの単位として別に 1 つのノードからフェールオーバーできるリソースのコレクションです。 リソース グループは、マスター/スレーブ; として構成されているリソースを含めることはできません。したがって、Ag に使用できません。 リソース グループは、Fci を使用できますが、その一般的に、構成は推奨されません。

#### <a name="constraints"></a>制約
WSFCs には、リソースと依存関係は、2 つの異なるリソース間の親子リレーションシップの WSFC に指示などのさまざまなパラメーターがあります。 依存関係は、どのリソースが最初にオンラインにする必要がある、WSFC を通知規則だけです。

ペース クラスターには、依存関係の概念はありませんが、制約があります。 制約の 3 種類があります: コロケーション、場所、および順序付けします。
-   コロケーションの制約は、2 つのリソースが同じノードで実行されている必要があるかどうかを適用します。
-   場所の制約条件は、ここでリソースできます (またはできません) を実行ペース クラスターを指示します。
-   順序付けの制約は、ペースのクラスター リソースが起動する必要があります、順序を指示します。

> [!NOTE]
> コロケーションの制約は、単一ユニットとして表示されるすべてのため、リソース グループ内のリソースの必要はありません。

#### <a name="quorum-fence-agents-and-stonith"></a>クォーラム、フェンス エージェント、および STONITH
ペースでのクォーラムは、概念的には、WSFC に似ています。 クラスターのクォーラムのメカニズムの目的では、立ち上がっており実行中に、クラスターが残ることを確認してください。 WSFC と Linux ディストリビューションの HA アドオンの両方がある投票の概念の各ノードがクォーラムになるまでカウントする場所です。 投票の過半数をそれ以外の場合、最悪のシナリオでは、クラスターをシャット ダウンされます。

異なり、WSFC クォーラムを使用するミラーリング監視サーバーのリソースはありません。 目標は、WSFC と同様に、奇数の投票の数を保持します。 クォーラム構成には、Fci より Ag に関する異なる考慮事項があります。

WSFCs が参加しているノードの状態を監視し、それらの問題が発生したときに処理します。 WSFCs の以降のバージョンが不適切に動作するか、使用できなくなったノードの検疫などの機能を提供する (ノードに含まれていない、ネットワーク通信がダウンなど)。 Linux 側では、この種の機能は、フェンス エージェントによって提供されます。 概念は、フェンス操作とも呼ばれます。 ただし、これらのフェンス エージェントは、一般に、展開に固有とハードウェア ベンダーとのハイパーバイザーを入力したユーザーなど、一部のソフトウェア ベンダーによって提供される多くの場合。 たとえば、VMware では、Linux vm の vSphere を使用して仮想化に使用できるフェンス エージェントが提供されます。

クォーラムとの結び付きを別の概念にフェンス STONITH と呼ばれるや先頭に、その他のノードを撮影してください。 STONITH にはすべての Linux ディストリビューションでサポートされるペース クラスターが必要です。 詳細については、次を参照してください。 [Red Hat 高可用性クラスター内のフェンス](https://access.redhat.com/solutions/15575)(RHEL)。

#### <a name="corosyncconf"></a>corosync.conf
`corosync.conf`ファイルには、クラスターの構成が含まれています。 ある`/etc/corosync`です。 通常の日常的な操作の過程で、このファイルはクラスターが正しく設定されている場合に編集する付与されないようにします。

#### <a name="cluster-log-location"></a>クラスターのログの場所
ペース クラスター ログの場所は、分布によって異なります。
-   RHEL、SLES-`/var/log/cluster/corosync.log`
-   Ubuntu – `/var/log/corosync/corosync.log`

既定のログの場所を変更する変更`corosync.conf`です。

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>ペース クラスターを計画します。[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
このセクションでは、ペース クラスターの場合は、重要な計画点について説明します。

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>をクラスターの仮想化の Linux ベースのペース[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
仮想マシンを使用して、Linux ベースを展開する[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Ag および Fci の展開は、Windows ベースの対応の規則でカバーされます。 ルールのサポート性のための基本セットが仮想化された[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]で Microsoft によって提供される展開[Microsoft サポート KB 956893](https://support.microsoft.com/en-us/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment)です。 Microsoft の HYPER-V と VMware ESXi などの別のハイパーバイザーでは、プラットフォーム自体の違いにより、別の差異をその上でがあります。

Ag と Fci に仮想化でに関しては、アンチ アフィニティが特定のペース クラスターのノードに対して設定されていることを確認します。 ホストする Vm を可用性グループまたは FCI の構成で高可用性構成時に[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]同じハイパーバイザー ホストで決して実行されている必要があります。 たとえば、2 つのノードの FCI が展開されている場合は必要があります*少なくとも*Live などのハイパーバイザー ホストの 3 つになるようどこかに移動するホストに障害が発生した場合に、ノードをホストする Vm のいずれかの機能を使用する場合に特に移行または vmotion を使用します。

詳細についてを参照してください。
-   HYPER-V のドキュメント:[ゲスト クラスタ リングの高可用性を使用します。](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   ホワイト ペーパーで記述された Windows ベースの展開が静止の概念のほとんどを適用) –[計画高可用性、ミッション クリティカルな SQL Server の展開 VMware vsphere](http://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

>[!NOTE]
>STONITH とペース クラスターと RHEL が HYPER-V によってまだサポートされていません。 サポートされている、詳細と、更新されるまでを参照してください[RHEL 高可用性クラスターのサポート ポリシー](https://access.redhat.com/articles/29440#3physical_host_mixing)です。

### <a name="networking"></a>ネットワーク
WSFC とは異なりペースは必要ありません、専用の名または少なくとも 1 つの専用 IP アドレス、ペース クラスター自体の。 Ag と Fci (詳細については、それぞれのドキュメントを参照してください)、IP アドレスは、名前を除く、ネットワーク名リソースが存在しないためです。 管理のために、IP アドレスの構成では、SLES が必要ですに示されているようにではありません[ペース クラスターを作成する](sql-server-linux-deploy-pacemaker-cluster.md#create)です。

WSFC の場合と同様にペース優先的冗長ネットワークは、個別のネットワーク カード (Nic または物理 pNICs) を意味個々 の IP アドレスを持ちます。 クラスター構成の観点から各 IP アドレスは、独自のリングと呼ばれるもの必要があります。 ただし、WSFCs で今日では、多くの実装では、仮想化、またはパブリック クラウドでただ 1 つがサーバーに提示する NIC (vNIC) を仮想化が実際にします。 PNICs と Vnic のすべてが同じ物理または仮想スイッチに接続されている場合はありません true 冗長性層では、ネットワーク、仮想マシンにフィルターの種類のビットは、複数の Nic を構成するため。 ネットワークの冗長性は、通常の仮想化された展開は、ハイパーバイザーに組み込まれているし、パブリック クラウドに確実に組み込まれてです。

複数の Nic と、WSFC とペースで 1 つの違いは、ペースできる複数の IP アドレス、同じサブネットに、WSFC は実行されません。 複数のサブネットと Linux クラスターの詳細については、記事を参照してください。[複数のサブネットを構成する](sql-server-linux-configure-multiple-subnet.md)です。

### <a name="quorum-and-stonith"></a>クォーラムと STONITH
クォーラム構成および要件は、デプロイに関連する可用性グループまたは FCI 固有の[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。

STONITH はペース クラスターのサポートされている必要があります。 STONITH を構成するのにには、分布からドキュメントを使用します。 例としてで[ストレージ ベースのフェンス操作](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html)SLES 用です。 ESXI ベースのソリューションの VMware vcenter STONITH エージェントもあります。 詳細については、次を参照してください。 [VMWare VM VCenter SOAP のフェンス用 (Unofficial) Stonith プラグイン エージェント](https://github.com/olafrv/fence_vmware_soap)です。

> [!NOTE]
> この記事の執筆時点で HYPER-V では STONITH の解決策ありません。 これは内部設置型の展開での場合は true であり、RHEL などの特定の配布を使用する Azure ベースのペース展開にも影響を与えます。

### <a name="interoperability"></a>相互運用性
このセクションでは、WSFC または Linux の他のディストリビューションと Linux ベースのクラスターの対話方法を説明します。

#### <a name="wsfc"></a>WSFC
現時点では、連携して動作するには、WSFC とペースのクラスターの直接的な方法はありません。 これは、可用性グループまたは FCI WSFC とペースの間で機能を作成する方法がないことを意味します。 ただし、Ag どちらもできるように設計された、2 つの相互運用性ソリューションがあります。 FCI は、クロス プラットフォームの構成に参加できる唯一の方法では、これら 2 つのシナリオの 1 つのインスタンスとして参加しているかどうかです。
-   クラスター型なしの可用性グループです。 詳細については、Windows を参照してください。[可用性グループのドキュメント](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)です。
-   分散 AG、独自の可用性グループとして構成する 2 つの異なる Ag を許可する可用性グループの特殊な型です。 分散 Ag の詳細については、ドキュメントを参照して[分散型可用性グループ](../database-engine/availability-groups/windows/distributed-availability-groups.md)です。

#### <a name="other-linux-distributions"></a>他の Linux ディストリビューション
Linux では、ペース クラスターのすべてのノードは、同じ配布する必要があります。 たとえば、つまり、RHEL ノードは SLES ノードを持つペース クラスターの一部であること。 その理由は、メインの上記: のディストリビューションが可能性がさまざまなバージョンおよび機能、処理が正しく動作しない可能性があります。 WSFCs と Linux の混在と同じストーリーがディストリビューションの混在: none、または、Ag を分散します。

## <a name="next-steps"></a>次の手順
[SQL Server on Linux のペース クラスターを展開します。](sql-server-linux-deploy-pacemaker-cluster.md)
