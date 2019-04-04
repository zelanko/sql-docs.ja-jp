---
title: Linux で MSDTC を構成する方法 |Microsoft Docs
description: この記事では、Linux 上の MSDTC を構成するためのチュートリアルについてを提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 127f39075a1b84b1250a27003efeb28083d1adbd
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52513189"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Linux 上の Microsoft 分散トランザクション コーディネーター (MSDTC) を構成する方法

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux で Microsoft 分散トランザクション コーディネーター (MSTDC) を構成する方法について説明します。 Linux 上の MSDTC のサポートは、SQL Server 2019 プレビューで導入されました。

## <a name="overview"></a>概要

分散トランザクションは SQL Server on Linux に SQL Server 内で MSDTC と RPC エンドポイント マッパー機能を導入することで有効になっています。 既定では、RPC エンドポイント マッピング プロセスは、受信 RPC 要求のポート 135 をリッスンし、MSDTC サービス) などの適切なコンポーネントにルーティングします。 プロセスには、Linux 上の既知のポート (1024 未満のポート番号) にバインドするスーパー ユーザー特権が必要です。 RPC エンドポイント マッパーのプロセスのルート特権を持つ SQL Server の起動を防ぐためには、システム管理者は、SQL Server の RPC エンドポイント マッピングのプロセスにポート 135 でトラフィックをルーティングするのに NAT 変換を作成するのに iptables を使用する必要があります。

SQL Server 2019 には、mssql conf ユーティリティの 2 つの構成パラメーターが導入されています。

| mssql conf 設定 | 説明 |
|---|---|
| **network.rpcport** | RPC エンドポイント マッパーのプロセスがバインドされる TCP ポート。 |
| **network.servertcpport** | MSDTC サーバーがリッスンするポート。 できない場合は、設定すると、MSDTC サービスを使用してランダムな一時的なポートでサービスが再起動し、ファイアウォールの例外は再 MSDTC サービスが通信を継続できるようにすることを確認するように構成する必要があります。 |

これらの設定とその他の関連の MSDTC 設定の詳細については、[mssql-conf ツールを使った Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md#msdtc)を参照してください。

## <a name="supported-msdtc-configurations"></a>サポートされている MSDTC の構成

次のような MSDTC 構成がサポートされています。

- OLE TX 分散トランザクションに対して Linux 上の SQL Server JDBC および ODBC プロバイダー。
- JDBC のプロバイダーを使用して Linux 上の SQL Server に対して XA 分散トランザクション。
- リンク サーバー上の分散トランザクション。

制限事項とプレビューの MSDTC の既知の問題は、[Linux 上の SQL Server 2019 プレビューのリリース ノート](sql-server-linux-release-notes-2019.md#msdtc)を参照してください。

## <a name="msdtc-configuration-steps"></a>MSDTC の構成手順

MSDTC 通信と機能を構成する 3 つの手順があります。 必要な構成手順が行われていない場合、SQL Server は MSDTC 機能を有効にできません。

- 構成**network.rpcport**と**distributedtransaction.servertcpport** mssql 会議を使用します。
- 通信を許可するファイアウォールを構成する**rpcport**、 **servertcpport**、ポート 135 とします。
- Linux サーバーのルーティングには、SQL Server のポート 135 で RPC 通信がリダイレクトされるように構成**network.rpcport**します。

次のセクションでは、各手順の詳細な手順を説明します。

## <a name="configure-rpc-and-msdtc-ports"></a>RPC、MSDTC のポートを構成します。

最初に、構成**network.rpcport**と**distributedtransaction.servertcpport** mssql 会議を使用します。

1. Mssql conf を使用して設定する、 **network.rpcport**値。 次の例は、13500 に設定します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport 13500
   ```

2. 設定、 **distributedtransaction.servertcpport**値。 次の例は、51999 に設定します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport 51999
   ```

3. SQL Server を再起動してください。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="configure-the-firewall"></a>ファイアウォールの構成

最後の手順が通信を許可するファイアウォールを構成するには**rpcport**、 **servertcpport**、ポート 135 とします。  これにより、RPC エンドポイント マッピングのプロセスとその他のトランザクション マネージャーとコーディネーター外部通信するために MSDTC プロセス。 この実際の手順については、ファイアウォール、Linux ディストリビューションによって異なります。 

次の例では、Ubuntu 上でこれらの規則を作成する方法を示します。

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

次の例では、どのように実行できる Red Hat Enterprise Linux (RHEL) では示しています。

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

ポートは、次のセクションでルーティングを構成する前に、ファイアウォールを構成するのには重要です。 ファイアウォールを更新すると、場合によっては、ポート ルーティング規則をクリアできます。

## <a name="configure-port-routing"></a>ポートのルーティングを構成します。

Linux サーバーのルーティング テーブルを構成するのには、SQL Server のポート 135 で RPC 通信がリダイレクトされるように**network.rpcport**します。 異なるディストリビューション上のポート転送の構成メカニズムが異なる場合があります。 Firewalld サービスを使用しないディストリビューションでは、iptable の規則は、これを実現する、効率的なメカニズムです。 このような distrubution の例は、Ubuntu 16.04 および SUSE Enterprise Linux v12 です。 Iptable の規則は可能性があります、次のコマンドは、再起動後に、ルールを復元するための手順を指定するため、再起動中に保持されません。

1. ポート 135 のルーティング規則を作成します。 次の例では、ポート 135 は、前のセクションで定義されている RPC ポート 13500 に送られます。 置換`<ipaddress>`サーバーの IP アドレスを使用します。

   ```bash
   iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   `--comment RpcEndPointMapper`後のコマンドでこれらの規則を管理するを支援し、前のコマンド パラメーター。

2. 次のコマンドで作成したルーティング規則を表示するには。

   ```bash
   iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. ルーティング規則をコンピューター上のファイルに保存します。

   ```bash
   iptables-save > /etc/iptables.conf
   ```

4. 規則を再読み込み、再起動後に、次のコマンドを追加`/etc/rc.local`(Ubuntu または RHEL) 用または`/etc/init.d/after.local`(SLES) 用。

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

**Iptables 保存**と**iptables 復元**コマンドは、保存し、iptables エントリを復元する基本的なメカニズムを提供します。 使用可能なオプションの自動化によっては、Linux ディストリビューションにある可能性があるより高度なこともできます。 たとえば、Ubuntu の代替は、 **iptables 永続的な**永続的なエントリを作成するパッケージ。 

Firewalld サービスを使用するディストリビューションでは、両方のサーバーと内部ポート転送ポートを開くため、同じサービスを使用できます。 たとえば、Red Hat Enterprise linux、する必要がありますサービスを使用する firewalld (-ファイアウォール cmd 構成ユーティリティを使用して追加-転送-ポートまたは同様のオプション) を作成し、永続的なポートの転送 iptables を使用する代わりにルールを管理します。

```bash
firewall-cmd --permanent --add-forward-port=port=135:proto=tcp:toport=13500
```

> [!IMPORTANT]
> 前の手順では、固定の IP アドレスと仮定します。 (手動による介入や DHCP) のため、SQL Server インスタンスの IP アドレスが変更された場合は、削除、iptables を使用して作成された場合は、ルーティング規則を再作成する必要があります。 再作成または既存のルーティング規則を削除する必要がある場合、次のコマンドを使用して古いを削除することができます`RpcEndPointMapper`規則。
> 
> ```bash
> iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

## <a name="verify"></a>Verify (英語の可能性あり)

この時点では、SQL Server は、分散トランザクションに参加できる必要があります。 SQL Server がリッスンしていることを確認するには、実行、 **netstat**コマンド (RHEL を使用している場合は、最初にインストールする必要があります、 **net ツール**パッケージ)。

```bash
sudo netstat -tulpn | grep sqlservr
```

次のような出力が表示されます。

```bash
tcp 0 0 0.0.0.0:1433 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 127.0.0.1:1434 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:13500 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:51999 0.0.0.0:* LISTEN 13911/sqlservr
tcp6 0 0 :::1433 :::* LISTEN 13911/sqlservr
tcp6 0 0 ::1:1434 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::13500 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::51999 :::* LISTEN 13911/sqlservr
```

ただし、再起動後、SQL Server が起動しないでリッスンしている、 **servertcpport**最初にディストリビュートされたトランザクションまでです。 ここでは、最初の分散トランザクションまで、この例ではポート 51999 でリッスンしている SQL Server が表示されないとします。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server に関する詳細については、[SQL Server on Linux](sql-server-linux-overview.md)を参照してください。
