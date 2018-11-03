---
title: SQL Server on Linux でのサード パーティの Active Directory プロバイダーを使用して |Microsoft Docs
description: このチュートリアルでは、サード パーティ プロバイダーを使用した Active Directory 認証の構成手順
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: 0ffe146de3a842f9c273b4dbba2a9fe4d9ff7ff5
ms.sourcegitcommit: 41979c9d511b3eeb45134d30ccb0dbc6bba70f1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757997"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>SQL Server on Linux でサード パーティの Active Directory プロバイダーを使用します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、構成する方法を説明します、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サード パーティの Active Directory プロバイダーを使用する場合、Active Directory 認証を使用した Linux のホスト コンピューターにします。 例としては、 [PowerBroker Identity サービス (PBI)](https://www.beyondtrust.com/)、 [1 つの Id](https://www.oneidentity.com/products/authentication-services/)、および[Centrify](https://www.centrify.com/)します。 このガイドには、Active Directory の構成を確認する手順が含まれます。 マシンをドメインに参加させる方法について説明するためのものではありません。 詳細な手順への参加について、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] realmd と SSSD を使用してドメインにホストを参照してください[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)します。

## <a name="prerequisites"></a>前提条件

Active Directory 認証を構成する前に、Active Directory ドメイン コント ローラーを Windows、ネットワーク上を設定する必要があります。 参加し、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Linux ホストは、Active Directory ドメインにします。 使用することができます[PBI](https://www.beyondtrust.com/)、 [VAS](https://www.oneidentity.com/products/authentication-services/)、または[Centrify](https://www.centrify.com/)します。

> [!NOTE]
>
>このチュートリアルでは**`contoso.com`** と**`CONTOSO.COM`** ドメインおよび領域名の例としてそれぞれします。 またを使用して**`DC1.CONTOSO.COM`** 例の完全修飾ドメイン名、ドメイン コント ローラーのようにします。 これらの名前は、独自の値で置き換える必要があります。

## <a name="check-the-connection-to-a-domain-controller"></a>ドメイン コント ローラーへの接続を確認してください。

ドメインの短期的および完全修飾の名前を持つドメイン コント ローラーに接続できることを確認します。

```bash
ping contoso

ping contoso.com
```

これらの名前のチェックのいずれかが失敗した場合は、ドメイン検索の一覧を更新します。

- **Ubuntu**

  編集、`/etc/network/interfaces`ファイル、Active Directory ドメインがドメインの検索リスト含まれるようにします。 

  ```/etc/network/interfaces
  <...>
  # The primary network interface
  auto eth0
  iface eth0 inet dhcp
  dns-nameservers **<AD domain controller IP address>**
  dns-search **<AD domain name>**
  ```

  > [!NOTE]  
  > ネットワーク インターフェイス、 **eth0**、さまざまなマシンが異なる場合があります。 使用しているかを確認するには、実行**ifconfig**します。 次に、IP アドレスと送信および受信したバイト数を持つインターフェイスをコピーします。

  このファイルを編集した後、ネットワーク サービスを再起動します。

  ```bash
  sudo ifdown eth0 && sudo ifup eth0
  ```

  これでいることを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

- **RHEL**

  編集、`/etc/sysconfig/network-scripts/ifcfg-eth0`ファイル、Active Directory ドメインがドメインの検索リスト含まれるようにします。 または、必要に応じて別のインターフェイス構成ファイルを編集します。

  ```/etc/sysconfig/network-scripts/ifcfg-eth0
  <...>
  PEERDNS=no
  DNS1=**<AD domain controller IP address>**
  DOMAIN="contoso.com com"
  ```

  このファイルを編集した後、ネットワーク サービスを再起動します。

  ```bash
  sudo systemctl restart network
  ```

  これでいることを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

  まだドメイン コント ローラーを ping できない場合は、完全修飾ドメイン名とドメイン コント ローラーの IP アドレスを検索します。 ドメイン名の例は、`DC1.CONTOSO.COM`します。 次のエントリを追加`/etc/hosts`:

  ```/etc/hosts
  **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
  ```

- **SLES**

  編集、`/etc/sysconfig/network/config`ように DNS クエリでは、Active Directory ドメイン コント ローラー IP が使用され、Active Directory ドメインがドメイン検索の一覧では、ファイルします。

  ```/etc/sysconfig/network/config
  <...>
  NETCONFIG_DNS_STATIC_SEARCHLIST=""
  NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
  ```

  このファイルを編集した後、ネットワーク サービスを再起動します。

  ```bash
  sudo systemctl restart network
  ```

  これでいることを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。

  ```/etc/resolv.conf
  search contoso.com com
  nameserver **<AD domain controller IP address>**
  ```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>逆引き DNS が正しく構成されていることを確認します。

次のコマンドは、SQL Server を実行するホストの完全修飾ドメイン名を返す必要があります。 例としては、  **`SqlHost.contoso.com`** します。

```bash
host **<IP address of SQL Server host>**
# **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
```

このコマンドは、ホストの FQDN で返されない場合、または FQDN が正しい場合はの逆引き DNS エントリを追加[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux ホスト、DNS サーバーにします。

## <a name="check-that-your-krb5-configuration-is-correct"></a>KRB5 構成が正しいことを確認します。

いることを確認、`/etc/krb5.conf`が正しく構成されています。 ほとんどのサードパーティの Active Directory プロバイダーでは、この構成は自動的に行われます。 ただし、チェック`/etc/krb5.conf`を将来発生する問題を防ぐために次の値。

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

## <a name="next-steps"></a>次の手順

この記事では、構成する方法を説明します、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上の Linux ホスト マシン サード パーティの Active Directory プロバイダーを使用する場合、Active Directory 認証を使用します。 構成を完了する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Active Directory アカウントをサポートするために linux では、次の手順に[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)します。

> [!div class="nextstepaction"]
> [SQL Server on Linux で Active Directory 認証を使用します。](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> スキップすることができます、 **Active Directory ドメインに参加させる SQL Server ホスト**セクション[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)このチュートリアルで完了したとします。
