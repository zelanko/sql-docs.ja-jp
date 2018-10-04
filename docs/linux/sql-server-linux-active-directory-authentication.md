---
title: Linux 上の SQL Server の active Directory 認証のチュートリアル |Microsoft Docs
description: このチュートリアルでは、SQL Server on Linux の AAD 認証の構成手順を提供します。
author: meet-bhagdev
ms.date: 02/23/2018
ms.author: meetb
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 85684fdb257dea2d4b3c06537c59e4c1a997aaaf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631596"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>SQL Server on Linux でのチュートリアル: Active Directory を使用して認証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux で Active Directory (AD) 認証をサポートさせるための構成方法を説明します。 概要については、「[SQL Server on Linux の Active Directory 認証](sql-server-linux-active-directory-auth-overview.md)」を参照してください。

このチュートリアルでは、次のタスクで構成されます。

> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインにホスト
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab を構成する
> * TRANSACT-SQL で AD に基づくログインを作成する
> * AD Authentication を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] へ接続する

> [!NOTE]
>
> 構成する場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サード パーティ製の AD プロバイダーを使用する linux を参照してください[サード パーティの Active Directory プロバイダーを使用して、SQL Server on Linux で](./sql-server-linux-active-directory-third-party-providers.md)します。

## <a name="prerequisites"></a>前提条件

AD 認証を構成する前にする必要があります。

* AD ドメイン コント ローラー (Windows)、ネットワークの設定します。  
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストール
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> 参加[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD ドメインにホスト

参加を次の手順を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Active Directory ドメインにホスト。

1. 使用**[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)** ホスト マシンを AD ドメインに参加させる。 まだインストールしていない場合に、realmd と Kerberos クライアント パッケージの両方をインストール、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト マシンの Linux ディストリビューションのパッケージ マネージャーを使用します。

   ```bash
   # RHEL
   sudo yum install realmd krb5-workstation

   # SUSE
   sudo zypper install realmd krb5-client

   # Ubuntu
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Kerberos クライアント パッケージのインストールでは、領域名を求め、大文字で、ドメイン名を入力します。

   > [!NOTE]
   > このチュートリアルでは使用"contoso.com"を"CONTOSO.COM"ドメインおよび領域名の例としてそれぞれします。 これらを独自の値を置き換える必要があります。 これらのコマンドは大文字小文字を区別ので、使用することを確認して大文字このチュートリアルで使用される任意の場所。

1. 構成、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] DNS ネーム サーバーとして AD ドメイン コントローラの IP アドレスを使用するホスト コンピューター。 

   - **Ubuntu**:

      編集、`/etc/network/interfaces`ファイルに dns ネーム サーバーとして AD ドメイン コントローラの IP アドレスが表示されます。 以下に例を示します。 

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
      nameserver **<AD domain controller IP address>**
      ```

   - **RHEL**:

     編集、`/etc/sysconfig/network-scripts/ifcfg-eth0`ファイル (またはその他のインターフェイス構成をファイルに適切な) DNS サーバーとして AD ドメイン コントローラの IP アドレスが表示されるようします。

     ```/etc/sysconfig/network-scripts/ifcfg-eth0
     <...>
     PEERDNS=no
     DNS1=**<AD domain controller IP address>**
     ```

     このファイルを編集した後、ネットワーク サービスを再起動します。

     ```bash
     sudo systemctl restart network
     ```

     これでいることを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。  

     ```/etc/resolv.conf
     nameserver **<AD domain controller IP address>**
     ```

   - **SLES**:

     編集、 `/etc/sysconfig/network/config` AD ドメイン コント ローラー IP が DNS クエリに使用するように、ファイルと、AD ドメインがドメインの検索リストには。

     ```/etc/sysconfig/network/config
     <...>
     NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
     ```

     このファイルを編集した後、ネットワーク サービスを再起動します。

     ```bash
     sudo systemctl restart network
     ```

     これでいることを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。

     ```/etc/resolv.conf
     nameserver **<AD domain controller IP address>**
     ```

1. ドメインに参加します。

   DNS が正しく構成されていることを確認したら、次のコマンドを実行して、ドメインに参加します。 新しいマシンをドメインに参加させる AD のための十分な特権を持つ AD アカウントを使用して認証する必要があります。

   具体的には、このコマンドは AD で新しいコンピューター アカウントを作成、作成、 `/etc/krb5.keytab` keytab ファイルをホストしでドメインを構成する`/etc/sssd/sssd.conf`:

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   <...>
   * Successfully enrolled machine in realm
   ```

   > [!NOTE]
   > エラーが表示し、「必要なパッケージがインストールされていない」実行する前に、Linux ディストリビューションのパッケージ マネージャーを使用してそれらのパッケージをインストールする必要があります、`realm join`コマンドを再実行します。
   >
   > 「、ドメインに参加する十分なアクセス許可」、エラーが発生する場合は、Linux マシンをドメインに参加させるための十分なアクセス許可があるドメイン管理者に確認する必要があります。
   >
   > 「KDC 応答と一致しませんでした予測を行い、」エラーが発生した場合を指定していないユーザーの適切な領域の名前。 領域名の大文字小文字を区別、大文字は通常、およびコマンドを使用して識別できます`realm discover contoso.com`します。
   
   > SQL Server は、ユーザー アカウントとグループをセキュリティ識別子 (SID) にマップするための SSSD と NSS を使用します。 SSSD 構成され、AD ログインを正常に作成する SQL Server の順序で実行されている必要があります。 Realmd は、ドメインへの参加の一環として自動的にこれは通常が、場合によってはこれを行うとは別にします。
   >
   > チェック アウトを構成するには、次[SSSD 手動で](https://access.redhat.com/articles/3023951)、および[SSSD を使用する NSS を構成します。](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options)

  
5. ドメインからユーザーに関する情報を収集できますようになりましたこととそのユーザーとして Kerberos チケットを取得することを確認します。

   次の例では**id**、  **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)**、および**[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** このコマンド。

   ```bash
   id user@contoso.com
   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM
   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   <...>
   ```

   > [!NOTE]
   > 場合`id user@contoso.com`戻り値は、「しないこのようなユーザー、」コマンドを実行して、SSSD サービスが正常に開始されたことを確認`sudo systemctl status sssd`します。 サービスが実行されても「このようなユーザーはありません」エラーが発生した場合は、SSSD の詳細ログ記録を有効にしてください。 詳細については、Red Hat のドキュメントを参照してください[トラブルシューティング SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting)します。
   >
   > 場合`kinit user@CONTOSO.COM`戻り値は、「KDC の応答が想定どおりでない最初の資格情報の取得中に」ことを realm は大文字で指定することを確認します。

詳細については、Red Hat のドキュメントを参照してください[探索および結合の Id ドメイン](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html)します。 

## <a id="createuser"></a> AD ユーザーを作成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SPN の設定

  > [!NOTE]
  > 次の手順を使用して[完全修飾ドメイン名](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)します。 使用している場合**Azure**、する必要があります**[作成](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** 続行する前にします。

1. ドメイン コント ローラーで実行、 [New-aduser](https://technet.microsoft.com/library/ee617253.aspx)パスワードを無期限で新しい AD ユーザーを作成する PowerShell コマンド。 この例で、アカウントの"mssql"は名前が、アカウント名には、どのようなを指定できます。 アカウントの新しいパスワードの入力が求められます。

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > SQL Server の資格情報は、同じアカウントを使用して他のサービスと共有されないように、SQL Server の専用の AD アカウントにセキュリティのベスト プラクティスを勧めします。 ただし、再利用できます既存の AD アカウント場合は、(次の手順で keytab ファイルを生成するために必要な) アカウントのパスワードがわかっている場合。

2. このアカウントを使用するためのサービス プリンシパル名 (SPN) の設定、`setspn.exe`ツール。 SPN は、次の例では指定どおり正確にフォーマットする必要があります。 完全修飾ドメイン名を見つけることができます、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト マシンを実行して`hostname --all-fqdns`上、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト、および TCP ポートは 1433 構成していない限り[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]別のポート番号を使用します。

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > 「十分なアクセス権、」エラーが発生した場合は、このアカウントの SPN を設定するための十分なアクセス許可があるドメイン管理者に確認する必要があります。
   >
   > 今後、TCP ポートを変更する場合は、新しいポート番号、setspn コマンドをもう一度実行する必要があります。 また、次のセクションの手順に従って、SQL Server サービス keytab に新しい SPN を追加する必要があります。

3. 詳細については、「 [Kerberos 接続用のサービス プリンシパル名の登録](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)」を参照してください。

## <a id="configurekeytab"></a> 構成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab

1. 前の手順で作成した AD アカウントのキーのバージョン番号 (kvno) を確認します。 通常は 2 ですが、アカウントのパスワードを複数回変更した場合、別の整数がある可能性があります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト コンピューターで、次を実行します。

   ```bash
   kinit user@CONTOSO.COM

   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

   > [!NOTE]
   > Spn で、ドメインが大きい場合は特に、数分に反映されるまで、ドメインがかかる場合があります。 エラーが発生した場合"kvno: サーバー データベースに見つかりません Kerberos MSSQLSvc の資格情報を取得中に/\*\*\<ホスト コンピューターの完全修飾ドメイン名\>\*\*:\* \* \<tcp ポート\>\*\*\@CONTOSO.COM"、数分待ってから、もう一度やり直してください。

2. Keytab ファイルを作成**[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)** 前の手順で作成した AD ユーザーにします。 入力を求められたら、その AD アカウントのパスワードを入力します。

   ```bash
   sudo ktutil

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

   > [!NOTE]
   > Ktutil ツールはないパスワードの検証、ので正しく入力してください。

3. Keytab にコンピューター アカウントを追加 **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)** します。 (UPN とも呼ばれます) コンピューターのアカウントは存在`/etc/krb5.keytab`形式で"\<ホスト名\>$\@\<realm.com\>"(例: sqlhost$\@CONTOSO.COM)。 これらのエントリからコピーします`/etc/krb5.keytab`に`mssql.keytab`します。

   ```bash
   sudo ktutil

   # Read all entries from /etc/krb5.keytab
   ktutil: rkt /etc/krb5.keytab

   # List all entries
   ktutil: list

   # Delete all entries by their slot number which are not the UPN one at a
   # time.
   # Warning: when an entry is deleted (e.g. slot 1), all values slide up by
   # one to take its place (e.g. the entry in slot 2 moves to slot 1 when slot
   # 1's entry is deleted)
   ktutil: delent <slot num>
   ktutil: delent <slot num>
   ...

   # List all entries to ensure only UPN entries are left
   ktutil: list

   # When only UPN entries are left, append these values to mssql.keytab
   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

4. これにアクセスできる人物による`keytab`ファイル権限を借用できます[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインで、ようにしてこのようなファイルへのアクセスを制限するだけ、`mssql`アカウントは、読み取りアクセス。

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
   sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
   ```

5. 構成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]これを使用する`keytab`Kerberos 認証用のファイル。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
   sudo systemctl restart mssql-server
   ```

6. 省略可能: は、パフォーマンスを向上させるために、ドメイン コント ローラーへの UDP 接続を無効にします。 多くの場合、UDP 接続は常に失敗構成オプションを設定するために、ドメイン コント ローラーに接続するときに`/etc/krb5.conf`UDP 呼び出しをスキップします。 編集`/etc/krb5.conf`し、次のオプションを設定します。

   ```/etc/krb5.conf
   [libdefaults]
   udp_preference_limit=0
   ```

## <a id="createsqllogins"></a> TRANSACT-SQL での AD ベースのログインを作成します。

1. 接続する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、AD ベースの新しいログインを作成します。

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

2. ログインが現在表示されていることを確認、 [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)システム カタログ ビュー。

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> 接続する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 認証を使用します。

ドメインの資格情報を使用して、クライアント コンピューターにログインします。 接続できるようになりました[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 認証を使用して、パスワードを再入力しなくてもします。 AD グループのログインを作成する場合、そのグループのメンバーになっている AD ユーザーは、同じ方法で接続できます。

使用してドライバーをクライアントが AD 認証を使用する特定の接続文字列パラメーターに依存します。 次の例を考えてみます。

* `sqlcmd` ドメインに参加している Linux クライアントに

   使用してドメインに参加している Linux クライアントにログイン`ssh`とドメインの資格情報。

   ```bash
   ssh -l user@contoso.com client.contoso.com
   ```

   インストールされていることを確認、 [mssql ツール](sql-server-linux-setup-tools.md)をパッケージ化しを使用して接続`sqlcmd`任意の資格情報の指定なし。

   ```bash
   sqlcmd -S mssql-host.contoso.com
   ```

* ドメインに参加している Windows クライアント上の SSMS

   ドメインの資格情報を使用してドメインに参加している Windows クライアントにログインします。 確認[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]がインストールされている場合、その後に接続、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンス (例:"mssql-host.contoso.com") を指定して**Windows 認証**で、**サーバーへの接続**ダイアログ。

* その他のクライアント ドライバーを使用して AD 認証

  * JDBC: [Kerberos を使用して統合 SQL Server の接続の認証](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
  * ODBC:[統合認証を使用](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
  * ADO.NET:[接続文字列の構文](https://msdn.microsoft.com/library/system.data.sqlclient.sqlauthenticationmethod(v=vs.110).aspx)

## <a name="performance-improvements"></a>パフォーマンスの強化
AD の構成は手順で有効な AD アカウントの参照は、しばらく時間をチェックすることを確認する場合[サード パーティ製 AD プロバイダー経由の Linux 上の SQL Server と Active Directory 認証を使用して](sql-server-linux-active-directory-third-party-providers.md)、追加することができます、線の下に`/var/opt/mssql/mssql.conf`を SSSD 呼び出しをスキップし、直接の LDAP 呼び出しを使用します。

```/var/opt/mssql/mssql.conf
[network]
disablesssd = true
```

## <a name="next-steps"></a>次の手順

このチュートリアルでは、SQL Server on Linux での Active Directory 認証を設定する方法を説明しました。 学習したします。
> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインにホスト
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab を構成する
> * TRANSACT-SQL で AD に基づくログインを作成する
> * AD Authentication を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] へ接続する

次に、その他のセキュリティのシナリオについて調べる for SQL Server on Linux。

> [!div class="nextstepaction"]
>[SQL Server on Linux への接続の暗号化](sql-server-linux-encrypted-connections.md)
