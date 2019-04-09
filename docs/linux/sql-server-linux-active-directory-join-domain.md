---
title: Active Directory への Linux 上の SQL サーバーを参加させる
titleSuffix: SQL Server
description: ''
author: Dylan-MSFT
ms.author: Dylan.Gray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 6ccc94acb42fa7043912099c4888834cf4ff3e71
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59243586"
---
# <a name="join-sql-server-on-a-linux-host-to-an-active-directory-domain"></a>SQL Server を Linux ホストを Active Directory ドメインに参加します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、SQL Server Linux ホストのコンピューターを Active Directory (AD) ドメインに参加させる方法については、一般的なガイダンスを提供します。 2 つの方法: 組み込みの SSSD パッケージを使用して、またはサード パーティの Active Directory プロバイダーを使用します。 サード パーティのドメイン参加の製品の例は、 [PowerBroker Identity サービス (PBI)](https://www.beyondtrust.com/)、 [1 つの Id](https://www.oneidentity.com/products/authentication-services/)、および[Centrify](https://www.centrify.com/)します。 このガイドには、Active Directory の構成を確認する手順が含まれます。 ただし、サード パーティのユーティリティを使用する場合、マシンをドメインに参加させる方法について説明することはありません。

## <a name="prerequisites"></a>前提条件

Active Directory 認証を構成する前に、Active Directory ドメイン コント ローラーを Windows、ネットワーク上を設定する必要があります。 その後、SQL Server Linux ホストを Active Directory ドメインに参加します。

> [!IMPORTANT]
> この記事で説明されているサンプルの手順では、ガイダンスのためだけです。 実際の手順は、環境全体の構成方法に応じて、環境若干異なる場合があります。 特定の構成、カスタマイズ、およびトラブルシューティングに必要な環境のシステムとドメイン管理者が情報交換できます。

## <a name="check-the-connection-to-a-domain-controller"></a>ドメイン コント ローラーへの接続を確認してください。

ドメインの短期的および完全修飾の名前を持つドメイン コント ローラーに接続できることを確認します。

```bash
ping contoso
ping contoso.com
```

> [!TIP]
> このチュートリアルでは**contoso.com**と**CONTOSO.COM**ドメインおよび領域名の例としてそれぞれします。 また、使用**DC1 します。CONTOSO.COM**例の完全修飾ドメイン名、ドメイン コント ローラーのようにします。 これらの名前は、独自の値で置き換える必要があります。

これらの名前のチェックのいずれかが失敗した場合は、ドメイン検索の一覧を更新します。 次のセクションでは、Ubuntu、Red Hat Enterprise Linux (RHEL)、および SUSE Linux Enterprise Server (SLES) の手順をそれぞれ提供します。

### <a name="ubuntu"></a>Ubuntu

1. 編集、 **/etc/network/interfaces**ファイル、Active Directory ドメインがドメインの検索リスト含まれるようにします。

   ```/etc/network/interfaces
   # The primary network interface
   auto eth0
   iface eth0 inet dhcp
   dns-nameservers **<AD domain controller IP address>**
   dns-search **<AD domain name>**
   ```

   > [!NOTE]
   > ネットワーク インターフェイス、 `eth0`、さまざまなマシンが異なる場合があります。 使用しているかを確認するには、実行**ifconfig**します。 次に、IP アドレスと送信および受信したバイト数を持つインターフェイスをコピーします。

1. このファイルを編集した後、ネットワーク サービスを再起動します。

   ```bash
   sudo ifdown eth0 && sudo ifup eth0
   ```

1. 次に、いることを確認、 **/etc/resolv.conf**ファイルには、次の例のような行が含まれています。

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

### <a name="rhel"></a>RHEL

1. 編集、 **/etc/sysconfig/network-scripts/ifcfg-eth0**ファイル、Active Directory ドメインがドメインの検索リスト含まれるようにします。 または、必要に応じて別のインターフェイス構成ファイルを編集します。

   ```/etc/sysconfig/network-scripts/ifcfg-eth0
   PEERDNS=no
   DNS1=**<AD domain controller IP address>**
   DOMAIN="contoso.com com"
   ```

1. このファイルを編集した後、ネットワーク サービスを再起動します。

   ```bash
   sudo systemctl restart network
   ```

1. これでいることを確認、 **/etc/resolv.conf**ファイルには、次の例のような行が含まれています。

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

1. まだドメイン コント ローラーを ping できない場合は、完全修飾ドメイン名とドメイン コント ローラーの IP アドレスを検索します。 ドメイン名の例は、 **DC1 します。CONTOSO.COM**します。 次のエントリを追加 **/etc/ホスト**:

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

### <a name="sles"></a>SLES

1. 編集、 **/etc/sysconfig/network/config**ように、Active Directory ドメイン コント ローラー IP が DNS クエリに使用され、Active Directory ドメインがドメイン検索の一覧では、ファイルします。

   ```/etc/sysconfig/network/config
   NETCONFIG_DNS_STATIC_SEARCHLIST=""
   NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
   ```

1. このファイルを編集した後、ネットワーク サービスを再起動します。

   ```bash
   sudo systemctl restart network
   ```

1. 次に、いることを確認、 **/etc/resolv.conf**ファイルには、次の例のような行が含まれています。

   ```/etc/resolv.conf
   search contoso.com com
   nameserver **<AD domain controller IP address>**
   ```

## <a name="join-to-the-ad-domain"></a>AD ドメインに参加させる

基本的な構成とドメイン コント ローラーとの接続を検証した後は、Active Directory ドメイン コント ローラーと SQL Server Linux ホスト コンピューターを参加させるための 2 つのオプションがあります。

- [オプション 1:SSSD パッケージを使用します。](#option1)
- [オプション 2:サード パーティ製 openldap プロバイダー ユーティリティを使用してください。](#option2)

### <a id="option1"></a> オプション 1:SSSD パッケージを使用して、AD ドメインに参加するには

このメソッドは、AD ドメインを使用して、SQL Server ホストを参加**realmd**と**sssd**パッケージ。

> [!NOTE]
> これは、AD ドメイン コント ローラーに Linux ホストに参加する推奨される方法です。

Active Directory ドメインに SQL Server ホストに参加するのにには、次の手順を使用します。

1. 使用[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.md)ホスト マシンを AD ドメインに参加させる。 両方をインストールする必要があります最初、 **realmd**と Linux ディストリビューションのパッケージ マネージャーを使用して SQL Server ホスト マシンでの Kerberos クライアント パッケージ。

   **RHEL の場合:**

   ```base
   sudo yum install realmd krb5-workstation
   ```

   **SUSE の場合:**

   ```bash
   sudo zypper install realmd krb5-client
   ```

   **Ubuntu の場合:**

   ```bash
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Kerberos クライアント パッケージのインストールでは、領域名を求め、大文字で、ドメイン名を入力します。

1. DNS が正しく構成されていることを確認した後、次のコマンドを実行して、ドメインに参加します。 新しいマシンをドメインに参加させる AD のための十分な特権を持つ AD アカウントを使用して認証する必要があります。 このコマンドは、AD で新しいコンピューター アカウントを作成、作成、 **/etc/krb5.keytab** keytab ファイルをホストでドメインを構成します **/etc/sssd/sssd.conf**、および更新 **/etc/krb5.conf。**.

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   ```

   メッセージが表示`Successfully enrolled machine in realm`します。

   次の表は、いくつか受け取る可能性があるエラー メッセージとそれを解決する他の推奨事項を示します。

   | エラー メッセージ | 推奨 |
   |---|---|
   | `Necessary packages are not installed` | 領域の結合コマンドをもう一度実行する前に、Linux ディストリビューションのパッケージ マネージャーを使用してそれらのパッケージをインストールします。 |
   | `Insufficient permissions to join the domain` | Linux マシンをドメインに参加させるための十分なアクセス許可があるドメイン管理者に確認します。 |
   | `KDC reply did not match expectations` | ユーザーの適切な領域名が指定されていません。 領域名の大文字小文字を区別、大文字は通常、およびコマンド領域で識別できる contoso.com を検出します。 |

   SQL Server は、ユーザー アカウントとグループをセキュリティ識別子 (Sid) にマップするための SSSD と NSS を使用します。 SSSD 構成され、AD ログインを正常に作成する SQL Server を実行している必要があります。 **realmd**は、通常は自動的に一環として、ドメインに参加するが、場合によっては、これを行うとは別にします。

   詳細については、次を参照してください。 方法[SSSD を手動で構成](https://access.redhat.com/articles/3023951)、および[SSSD を使用する NSS を構成する](https://access.redhat.com/documentation/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options)します。

1. ドメインからユーザーに関する情報を収集できますようになりましたこととそのユーザーとして Kerberos チケットを取得することを確認します。 次の例では**id**、 [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)、および[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)このコマンド。

   ```bash
   id user@contoso.com

   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM

   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   ```

   > [!NOTE]
   > - 場合**id user@contoso.com** から制御が戻る`No such user`、コマンドを実行して、SSSD サービスが正常に開始されていることを確認`sudo systemctl status sssd`します。 サービスが実行されてもエラーが発生した場合は、SSSD の詳細ログ記録を有効にしてください。 詳細については、Red Hat のドキュメントを参照してください[トラブルシューティング SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting)します。
   >
   > - 場合**kinit user@CONTOSO.COM** から制御が戻る`KDC reply did not match expectations while getting initial credentials`、大文字で領域を指定したかどうかを確認します。

詳細については、Red Hat のドキュメントを参照してください[探索および結合の Id ドメイン](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html)します。

### <a id="option2"></a> オプション 2:サード パーティ製 openldap プロバイダー ユーティリティを使用してください。

など、サード パーティのユーティリティを使用できる[PBI](https://www.beyondtrust.com/)、 [VAS](https://www.oneidentity.com/products/authentication-services/)、または[Centrify](https://www.centrify.com/)します。 この記事では、各ユーティリティによる個々 の手順は含まれません。 これらのユーティリティのいずれかを使用して、転送を続行する前に、SQL Server 用の Linux ホストをドメインに参加する必要があります最初。  

SQL Server は、すべての AD に関連するクエリのサード パーティ製インテグレーターのコードやライブラリを使用しません。 SQL Server は、常にこのセットアップでは直接 openldap ライブラリ呼び出しを使用して AD を照会します。 サード パーティ製のインテグレーターは AD ドメインに Linux ホストに参加するだけで使用され、SQL Server には、直接的な通信にこれらのユーティリティはありません。

> [!IMPORTANT]
> 使用するための推奨事項を参照してください、 **mssql conf** `network.disablesssd`構成オプション、**追加の構成オプション**、記事の「[使用 ActiveSQL Server on Linux でのディレクトリ認証](sql-server-linux-active-directory-authentication.md#additionalconfig)します。

いることを確認、 **/etc/krb5.conf**が正しく構成されています。 ほとんどのサードパーティの Active Directory プロバイダーでは、この構成は自動的に行われます。 ただし、チェック **/etc/krb5.conf**を将来発生する問題を防ぐために次の値。

```/etc/krb5.conf
[libdefaults]
default_realm = CONTOSO.COM

[realms]
CONTOSO.COM = {
}

[domain_realm]
contoso.com = CONTOSO.COM
.contoso.com = CONTOSO.COM
```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>逆引き DNS が正しく構成されていることを確認します。

次のコマンドは、SQL Server を実行するホストの完全修飾ドメイン名 (FQDN) を返す必要があります。 例としては、 **SqlHost.contoso.com**します。

```bash
host **<IP address of SQL Server host>**
```

このコマンドの出力はようになります`**<reversed IP address>**.in-addr.arpa domain name pointer SqlHost.contoso.com`します。 このコマンドでは、ホストの FQDN、返さない場合、または FQDN が正しい場合は、SQL Server を DNS サーバーの Linux ホスト上の逆引き DNS エントリを追加します。

## <a name="next-steps"></a>次のステップ

この記事では、Active Directory 認証での Linux ホスト マシンで SQL Server を構成する方法の前提条件について説明します。 Active Directory アカウントをサポートする Linux 上の SQL Server の構成を完了する」の手順に従います[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)します。