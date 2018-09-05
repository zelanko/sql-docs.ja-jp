---
title: SQL Server on Linux でのサード パーティの Active Directory プロバイダーを使用して |Microsoft Docs
description: このチュートリアルでは、サード パーティ プロバイダーでの AD 認証の構成手順
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: 288f46a2084166a1b7164ff8f0c0ef82b81fb16b
ms.sourcegitcommit: ca5430ff8e3f20b5571d092c81b1fb4c950ee285
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2018
ms.locfileid: "43381515"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>SQL Server on Linux でサード パーティの Active Directory プロバイダーを使用します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、構成する方法を説明します、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]など、サード パーティ製 AD プロバイダーを使用する場合の AD 認証を使用した Linux ホスト マシンで[PowerBroker Identity サービス (PBI)](https://www.beyondtrust.com/)、[いる Vintela 認証サービス (VAS)](https://www.oneidentity.com/products/authentication-services/)、および[Centrify](https://www.centrify.com/)します。 このガイドの AD 構成を確認する手順について説明し、マシンをドメインに参加させる方法について説明するものではありません。 詳細な手順への参加について、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]領域と SSSD を使用してドメインにホストを参照してください[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)します。

## <a name="prerequisites"></a>Prerequisites

ネットワークと結合の AD ドメイン コント ローラー (Windows) を設定する必要が AD 認証を構成する前に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD ドメインに Linux ホストにします。 使用することができます[PBI](https://www.beyondtrust.com/)、 [VAS](https://www.oneidentity.com/products/authentication-services/)、または[Centrify](https://www.centrify.com/)します。

> [!NOTE]
>
>このチュートリアルでは"contoso.com"と"CONTOSO.COM"ドメインおよび領域名の例としてそれぞれします。 "DC1 また、使用します。CONTOSO.COM"ドメイン コント ローラーの完全修飾ドメイン名の例として。 これらを独自の値を置き換える必要があります。

## <a name="check-connection-to-domain-controller"></a>ドメイン コント ローラーへの接続を確認してください。

ドメインの短いおよび完全修飾名の両方でドメイン コント ローラーに接続することができますを確認します。

   ```bash
   ping contoso

   ping contoso.com
   ```

   これらのいずれかに失敗した場合は、ドメイン検索の一覧を更新します。

   - **Ubuntu**:

     編集、`/etc/network/interfaces`ファイルに、AD ドメインがドメインの検索リストには。 

     ```/etc/network/interfaces
     <...>
     # The primary network interface
     auto eth0
     iface eth0 inet dhcp
     dns-nameservers **<AD domain controller IP address>**
     dns-search **<AD domain name>**
     ```

     > [!NOTE]
     > さまざまなコンピューターのネットワーク インターフェイス (eth0) が異なる場合があります。 使用しているかを確認するには、ifconfig を実行し、IP アドレスと送信および受信したバイト数を持つインターフェイスをコピーします。

     このファイルを編集した後、ネットワーク サービスを再起動します。

     ```bash
     sudo ifdown eth0 && sudo ifup eth0
     ```

     これでいることを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。  

     ```/etc/resolv.conf
     search contoso.com com  
     nameserver **<AD domain controller IP address>**
     ```

   - **RHEL**:

     編集、`/etc/sysconfig/network-scripts/ifcfg-eth0`ファイル (またはその他のインターフェイス構成を必要に応じてファイル)、AD ドメインがドメインの検索リスト含まれるようにします。

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

   でも、ドメイン コント ローラーを ping できない場合は、完全修飾ドメイン名 (例: DC1 を検索します。CONTOSO.COM) とドメイン コント ローラーの IP アドレスと、次のエントリを追加 `/etc/hosts`

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

   - **SLES**:

     編集、`/etc/sysconfig/network/config`ファイルに、AD ドメイン コント ローラー IP が DNS クエリに使用して、AD ドメインがドメインの検索リストには。

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

## <a name="check-reverse-dns-is-properly-configured"></a>逆引き DNS が正しく構成されていることを確認します。

次のコマンド (例: SQL Server を実行しているホストの完全修飾ドメイン名を返す必要があります。"SqlHost.contoso.com")。

   ```bash
   host **<IP address of SQL Server host>**
   # **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
   ```

   これが、ホストの FQDN を返さない場合、または FQDN が正しい場合は、逆引き DNS エントリを追加、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Linux ホスト、DNS サーバーにします。

## <a name="check-your-krb5-configuration-is-correct"></a>KRB5 構成が正しいことを確認します。

チェック、`/etc/krb5.conf`が正しく構成されています。 ほとんどのサード パーティ製 AD プロバイダーでは、この自動的に行われます。 ただし、チェック`/etc/krb5.conf`を将来発生する問題を防ぐために次の値。

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

この記事で構成する方法について説明、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サード パーティ製 AD プロバイダーを使用する場合の AD 認証を使用した Linux のホスト コンピューターにします。 構成を完了する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD アカウントをサポートするために linux では、次の手順に[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)します。

> [!div class="nextstepaction"]
> [SQL Server on Linux で Active Directory 認証を使用します。](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> "AD ドメインに結合の SQL Server host"のセクションをスキップする[SQL Server on Linux での Active Directory を使用して認証](sql-server-linux-active-directory-authentication.md)ようにこのチュートリアルでは作業のだけです。