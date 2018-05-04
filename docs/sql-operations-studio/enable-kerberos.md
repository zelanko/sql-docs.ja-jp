---
title: SQL 操作 Studio (プレビュー) に接続するときに、Active Directory 認証 (Kerberos) を使用して |Microsoft ドキュメント
description: SQL 操作 Studio (プレビュー) に Active Directory 認証を使用する Kerberos を有効にする方法を学習します。
ms.custom: tools|sos
ms.date: 11/17/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.openlocfilehash: 46726247dc8540e67611173f6692ce092bb5be33
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connect-includename-sosincludesname-sos-shortmd-to-your-sql-server-using-windows-authentication---kerberos"></a>接続[!INCLUDE[name-sos](../includes/name-sos-short.md)]Windows 認証に Kerberos を使用して、SQL server 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Kerberos を使用して SQL Server への接続をサポートします。

MacOS または Linux で統合認証 (Windows 認証) を使用するために設定する必要があります、 **Kerberos チケット**Windows ドメイン アカウントに、現在のユーザーをリンクします。 

## <a name="prerequisites"></a>前提条件

- Kerberos ドメイン コント ローラーを照会するのには Windows ドメインに参加しているコンピューターにアクセスします。
- SQL Server は、Kerberos 認証を許可するように構成する必要があります。 Unix で実行されている、クライアント ドライバーは、統合認証のみがサポートされて Kerberos を使用します。 Kerberos を使用して認証を Sql Server を設定する方法の詳細についてはあります[ここ](https://support.microsoft.com/en-us/help/319723/how-to-use-kerberos-authentication-in-sql-server)です。 接続しようとしている Sql Server のインスタンスごとに登録されている Spn を設定する必要があります。 SQL Server の Spn の形式に関する情報が記載されて[ここ](https://technet.microsoft.com/en-us/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats)


## <a name="checking-if-sql-server-has-kerberos-setup"></a>かどうか、Sql Server は Kerberos セットアップの確認

Sql Server のホスト コンピューターにログインします。 Windows コマンド プロンプトを使用して、`setspn -L %COMPUTERNAME%`ホストのすべてのサービス プリンシパル名の一覧を表示します。 つまり Sql Server は、SPN が登録し、Kerberos 認証を受け入れる準備ができて MSSQLSvc/HostName.Domain.com で始まるエントリが表示されます。 
- Sql Server のホストへのアクセス権がないかどうかは、同じ Active Directory に参加している Windows OS 他から、コマンドを使用すること`setspn -L <SQLSERVER_NETBIOS>`< SQLSERVER_NETBIOS > は、Sql Server のホストのコンピューター名。


## <a name="get-the-kerberos-key-distribution-center"></a>Kerberos キー配布センターを取得します。

Kerberos KDC (キー配布センター) 構成値を検索します。 Active Directory ドメインに参加している Windows コンピューターで、次のコマンドを実行します。 

開始`cmd.exe`実行`nltest`です。

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where “DOMAIN.COMPANY.COM” maps to your domain’s name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
このケースの dc 33.domain.company.com で、必須の KDC 構成値は、DC の名前をコピーします。

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>OS を Active Directory ドメイン コント ローラーに参加させる

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

編集、`/etc/network/interfaces`ファイルの dns ネーム サーバーとして、AD ドメイン コント ローラーの IP アドレスが表示されるようにします。 以下に例を示します。 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```

> [!NOTE]
> さまざまなマシンのネットワーク インターフェイス (eth0) が異なる場合があります。 使用しているどちらかを調べるには、ifconfig を実行し、IP アドレスと送信および受信したバイト数を持つインターフェイスをコピーします。

このファイルを編集した後、ネットワーク サービスを再起動します。

```bash
sudo ifdown eth0 && sudo ifup eth0
```

今すぐことを確認、`/etc/resolv.conf`ファイルには、次のような行が含まれています。  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>RedHat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

編集、`/etc/sysconfig/network-scripts/ifcfg-eth0`ファイル (またはその他のインターフェイス設定ファイルに適切な) DNS サーバーとして、AD ドメイン コント ローラーの IP アドレスが表示されるよう。

```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```

このファイルを編集した後、ネットワーク サービスを再起動します。

```bash
sudo systemctl restart network
```

今すぐことを確認、`/etc/resolv.conf`ファイルには、次のような行が含まれています。  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- [次の手順] で、macOS を Active Directory ドメイン コント ローラーに参加させる (https://support.apple.com/kb/PH26282?viewlocale=en_US&locale=en_US)です。



## <a name="configure-kdc-in-krb5conf"></a>Krb5.conf の KDC を構成します。

編集、`/etc/krb5.conf`好みのエディターでします。 次のキーを構成します。

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Krb5.conf ファイルと終了を保存し、

> [!NOTE]
> ドメインはすべて大文字である必要があります。


## <a name="test-the-ticket-granting-ticket-retrieval"></a>チケット保証チケットの取得をテストします。

チケット保証チケット (TGT) を KDC からを取得します。

```bash
kinit username@DOMAIN.COMPANY.COM
```

Kinit を使用して、使用可能なチケットを表示します。 Kinit に成功した場合は、チケットが表示されます。 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-includename-sosincludesname-sos-shortmd"></a>使用して接続します。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* 新しい接続プロファイルを作成します。

* 選択**Windows 認証**認証の種類として

* 接続プロファイルの完了 をクリックして**接続**

正常に接続すると、サーバーが表示されます、*サーバー*サイドバーです。
