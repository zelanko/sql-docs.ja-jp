---
title: Linux 上の SQL Server の active Directory 認証チュートリアル |Microsoft ドキュメント
description: このチュートリアルでは、SQL Server on Linux の AAD 認証の構成手順を提供します。
author: meet-bhagdev
ms.date: 02/23/2018
ms.author: meetb
manager: craigg
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: d14914079cca30006255d4316bf0aba91e659880
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>SQL Server on Linux でのチュートリアル: を使用して Active Directory 認証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux で Active Directory (AD) 認証をサポートさせるための構成方法を説明します。Active Directory (AD) 認証は、統合認証としても知られています。 概要については、「[SQL Server on Linux の Active Directory 認証](sql-server-linux-active-directory-auth-overview.md)」を参照してください。

このチュートリアルは、次のタスクで構成されます。

> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインにホスト
> * AD ユーザーを作成する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SPN を設定し、
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab を構成する
> * TRANSACT-SQL で AD に基づくログインを作成する
> * AD Authentication を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] へ接続する

## <a name="prerequisites"></a>前提条件

AD の認証を構成する前にする必要があります。

* ネットワーク上の AD ドメイン コントローラ (Windows) の設定します。  
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストール
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> 参加[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD ドメインにホスト

参加を次の手順を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Active Directory ドメインにホストします。

1. 使用して**[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)** ホスト コンピューターを AD ドメインに参加させる。 まだインストールしていない場合に、realmd と Kerberos クライアント パッケージの両方をインストール、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト マシンの Linux ディストリビューションのパッケージ マネージャーを使用します。

   ```bash
   # RHEL
   sudo yum install realmd krb5-workstation

   # SUSE
   sudo zypper install realmd krb5-client

   # Ubuntu
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Kerberos クライアント パッケージのインストールを求めるプロンプト領域名を大文字に変換されたドメイン名を入力します。

   > [!NOTE]
   > このチュートリアル"contoso.com"と"CONTOSO.COM"ドメインおよび領域名の例としてそれぞれ使用します。 独自の値に置き換える必要があります。 これらのコマンドは大文字小文字を区別してください。 使用することを確認して大文字このチュートリアルで使用されている場所にします。

1. 構成、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] DNS ネーム サーバーとして、AD ドメイン コント ローラーの IP アドレスを使用するマシンをホストします。 

   - **Ubuntu**:

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

      今すぐことを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。  

      ```Code
      nameserver **<AD domain controller IP address>**
      ```

   - **RHEL**:

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

     今すぐことを確認、`/etc/resolv.conf`ファイルには、次の例のような行が含まれています。  

     ```Code
     nameserver **<AD domain controller IP address>**
     ```

1. ドメインに参加します。

   DNS が正しく構成されていることを確認した後、次のコマンドを実行して、ドメインに参加します。 新しいマシンをドメインに参加させる AD のための十分な特権を持つ AD アカウントを使用して認証する必要があります。

   具体的には、このコマンドは AD での新しいコンピューター アカウントを作成、作成、 `/etc/krb5.keytab` keytab ファイルをホストしでドメインを構成する`/etc/sssd/sssd.conf`:

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   <...>
   * Successfully enrolled machine in realm
   ```

   > [!NOTE]
   > エラーが表示するかどうかは、「必要なパッケージがインストールされていない」し、実行する前に、Linux ディストリビューションのパッケージ マネージャーを使用してそれらのパッケージをインストールする必要があります、`realm join`もう一度コマンドします。
   >
   > 「アクセス許可がありません、ドメインに参加する」、エラーが発生する場合は、Linux マシンをドメインに参加させるための十分なアクセス許可がある、ドメイン管理者に確認する必要があります。
   >
   > 「KDC 応答と一致しませんでした予測を行い、」、エラーが発生する場合を指定していないユーザーの適切な領域の名前。 領域名の大文字小文字を区別、通常の大文字、およびコマンドを使用して識別できる`realm discover contoso.com`です。
   
   > SQL Server は、ユーザー アカウントとグループをセキュリティ識別子 (SID) にマップするため、SSSD と NSS を使用します。 SSSD 構成され、AD ログインを正常に作成する SQL Server の順序で実行されている必要があります。 Realmd は、ドメインへの参加の一部として自動的にこれは通常が、場合によってはこれを行うとは別にします。
   >
   > 構成するには、以下のチェック_アウト[SSSD 手動で](https://access.redhat.com/articles/3023951)、および[SSSD を操作する NSS を構成します。](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options)

  
5. ドメインからユーザーに関する情報を収集できるようになりましたことと、そのユーザーとして Kerberos チケットを取得することを確認します。

   次の例で**id**、  **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)**、および**[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** このコマンド。

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
   > 場合`id user@contoso.com`戻り値は、「ないこのようなユーザー、」コマンドを実行して、SSSD サービスが正常に開始されたことを確認`sudo systemctl status sssd`です。 場合は、サービスが実行されており、「そのようなユーザーはありません」エラーが引き続き表示、SSSD の詳細ログ記録を有効にしてください。 詳細については、Red Hat でドキュメントを参照して[トラブルシューティング SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting)です。
   >
   > 場合`kinit user@CONTOSO.COM`戻り値は、「KDC 応答と一致しませんでした期待最初の資格情報の取得中に」は、realm は大文字で指定するを確認してください。

詳細については、Red Hat でドキュメントを参照して[探索および結合の Id ドメイン](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html)です。 

## <a id="createuser"></a> AD ユーザーを作成する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SPN を設定し、

  > [!NOTE]
  > 次のステップを使用して、[完全修飾ドメイン名](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)です。 表示されている場合**Azure**、する必要があります**[作成](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/portal-create-fqdn)** 続行する前にします。

1. 、ドメイン コント ローラーで実行、 [New-aduser](https://technet.microsoft.com/library/ee617253.aspx)パスワードを無期限にすると、新しい AD ユーザーを作成する PowerShell コマンド。 この例で、アカウント"mssql"は名前が、アカウント名には、どのようなを指定できます。 アカウントの新しいパスワードを入力が求められます。

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > SQL Server の資格情報が同じアカウントを使用して他のサービスと共有されないようにするには、専用の AD アカウントを SQL Server のセキュリティのベスト プラクティスを勧めします。 ただし、再利用できます既存の AD アカウントを使用する場合 (次の手順では、keytab ファイルを生成するために必要な) アカウントのパスワードがわかっている場合。

2. このアカウントを使用するためのサービス プリンシパル名 (SPN) を設定、`setspn.exe`ツールです。 SPN は次の例では指定どおり正確にフォーマットされている必要があります。 完全修飾ドメイン名を見つけることができます、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を実行して、ホスト マシン`hostname --all-fqdns`上、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト、および TCP ポートは、構成していない限りに、1433 にする必要があります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]別のポート番号を使用します。

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > 「十分なアクセス権、」、エラーが発生する場合は、このアカウントの SPN を設定するための十分なアクセス許可がある、ドメイン管理者に確認する必要があります。
   >
   > 後で、TCP ポートを変更する場合は、新しいポート番号、setspn コマンドを再度実行する必要があります。 また、次のセクションの手順に従って、SQL Server サービス keytab に新しい SPN を追加する必要があります。

3. 詳細については、「 [Kerberos 接続用のサービス プリンシパル名の登録](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)」を参照してください。

## <a id="configurekeytab"></a> 構成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab

1. 前の手順で作成した AD アカウントのキーのバージョン番号 (kvno) を確認します。 通常、2 が、アカウントのパスワードを複数回変更した場合、別の整数がある可能性があります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト マシンを次を実行します。

   ```bash
   kinit user@CONTOSO.COM

   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

2. Keytab ファイルを作成**[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)** 前の手順で作成した AD ユーザー用です。 メッセージが表示されたらは、その AD アカウントのパスワードを入力します。

   ```bash
   sudo ktutil

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

   > [!NOTE]
   > Ktutil ツールされていません、パスワードの検証、正しく入力するようにします。

3. アクセスを持つユーザー`keytab`ファイル権限を借用できます[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインで、必ずようにこのようなファイルへのアクセスを制限するだけ、`mssql`アカウントは、読み取りアクセス。

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
   sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
   ```

4. 構成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]これを使用する`keytab`Kerberos 認証用のファイル。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
   sudo systemctl restart mssql-server
   ```

## <a id="createsqllogins"></a> TRANSACT-SQL の AD に基づくログインを作成します。

1. 接続[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]し、AD ベースの新しいログインを作成します。

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

2. ログインが現在表示されていることを確認、 [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)システム カタログ ビュー。

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> 接続[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 認証を使用します。

ドメインの資格情報を使用してクライアント コンピューターにログインします。 接続できるようになりました[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 認証を使用して、パスワードを再入力しなくてもします。 AD グループのログインを作成する場合、そのグループのメンバーになっている AD ユーザーは、同じ方法で接続できます。

クライアントが AD の認証を使用する特定の接続文字列パラメーターは、使用しているドライバーによって異なります。 次の例を考えてみます。

* `sqlcmd` ドメインに参加している Linux クライアントで

   使用してドメインに参加している Linux クライアントへのログインに`ssh`と、ドメイン資格情報。

   ```bash
   ssh -l user@contoso.com client.contoso.com
   ```

   インストールされていることを確認、 [mssql ツール](sql-server-linux-setup-tools.md)をパッケージ化しを使用して接続`sqlcmd`せず、すべての資格情報を指定します。

   ```bash
   sqlcmd -S mssql.contoso.com
   ```

* ドメインに参加している Windows クライアントでの SSMS

   ドメインの資格情報を使用してドメインに参加している Windows クライアントにログインします。 確認してください[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]がインストールされているしへの接続、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を指定してインスタンス**Windows 認証**で、**サーバーへの接続**ダイアログ。

* その他のクライアント ドライバーを使用して AD の認証

  * JDBC: [Kerberos を使用して統合 SQL Server の接続に認証](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
  * ODBC:[統合認証を使用します。](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
  * ADO.NET:[接続文字列の構文](https://msdn.microsoft.com/library/system.data.sqlclient.sqlauthenticationmethod(v=vs.110).aspx)
  
## <a name="next-steps"></a>次の手順

このチュートリアルではとおし、SQL Server on Linux での Active Directory 認証を設定する方法です。 方法を学習します。
> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインにホスト
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab を構成する
> * TRANSACT-SQL で AD に基づくログインを作成する
> * AD Authentication を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] へ接続する

Linux 上 SQL Server の他のセキュリティ シナリオを次に、表示します。

> [!div class="nextstepaction"]
>[Linux 上の SQL Server への接続を暗号化](sql-server-linux-encrypted-connections.md)
