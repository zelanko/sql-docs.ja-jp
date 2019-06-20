---
title: チュートリアル:Linux 上の SQL Server の AD 認証を使用します。
titleSuffix: SQL Server
description: このチュートリアルでは、SQL Server on Linux 用の AD 認証の構成手順を提供します。
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: cf5a4c2f51d394a0322540a1651aa2549fedf8c5
ms.sourcegitcommit: 0343cdf903ca968c6722d09f017df4a2a4c7fd6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2019
ms.locfileid: "67166388"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>チュートリアル:SQL Server on Linux で Active Directory 認証を使用します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux で Active Directory (AD) 認証をサポートさせるための構成方法を説明します。 概要については、「[SQL Server on Linux の Active Directory 認証](sql-server-linux-active-directory-auth-overview.md)」を参照してください。

このチュートリアルでは、次のタスクで構成されます。

> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインにホスト
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab を構成する
> * Keytab ファイルをセキュリティ保護します。
> * Kerberos 認証に keytab ファイルを使用する SQL Server の構成します。
> * TRANSACT-SQL で AD に基づくログインを作成する
> * AD Authentication を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] へ接続する

## <a name="prerequisites"></a>前提条件

AD 認証を構成する前にする必要があります。

* AD ドメイン コント ローラー (Windows)、ネットワークの設定します。  
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストール
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> 参加[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD ドメインにホスト

Active Directory ドメイン コント ローラーで、SQL Server Linux ホストに参加する必要があります。 Active directory ドメインに参加する方法については、次を参照してください。 [Active Directory ドメインに Linux ホスト上の SQL Server の結合](sql-server-linux-active-directory-join-domain.md)します。

## <a id="createuser"></a> AD のユーザー (または MSA) を作成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SPN の設定

> [!NOTE]
> 使用して、次の手順、[完全修飾ドメイン名](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)します。 使用している場合**Azure**、する必要があります **[作成](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** 続行する前にします。

1. ドメイン コント ローラーで実行、 [New-aduser](https://technet.microsoft.com/library/ee617253.aspx)パスワードを無期限で新しい AD ユーザーを作成する PowerShell コマンド。 次の例では、アカウントの名前が`mssql`がアカウント名には、どのようなを指定できます。 アカウントの新しいパスワードを入力するように促されます。

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > SQL Server の資格情報は、同じアカウントを使用して他のサービスと共有されないように、SQL Server の専用の AD アカウントにセキュリティのベスト プラクティスを勧めします。 ただし、(これは、次の手順で keytab ファイルの生成に必要) アカウントのパスワードがわかっている場合は、既存の AD アカウントを必要に応じて再します。

2. このアカウントを使用するためのサービス プリンシパル名 (SPN) の設定、 **setspn.exe**ツール。 SPN は、次の例では指定どおり正確にフォーマットする必要があります。 完全修飾ドメイン名を見つけることができます、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト マシンを実行して`hostname --all-fqdns`上、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ホスト。 構成していない限り、TCP ポートは 1433 には[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]別のポート番号を使用します。

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > エラーが発生した場合`Insufficient access rights`、このアカウントの SPN を設定するための十分なアクセス許可がある、ドメイン管理者に確認してください。
   >
   > 実行する必要があります、将来、TCP ポートを変更する場合、 **setspn**新しいポート番号を使用してコマンド。 また、次のセクションの手順に従って、SQL Server サービス keytab に新しい SPN を追加する必要があります。

詳細については、「 [Kerberos 接続用のサービス プリンシパル名の登録](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)」を参照してください。

## <a id="configurekeytab"></a> 構成[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab

SQL Server サービス keytab ファイルを構成する 2 つのさまざまな方法はあります。 Keytab 構成に対応するコンピューター アカウント (UPN) を使用して、2 番目のオプションは、管理されたサービス アカウント (MSA) を使用しますが、最初のオプション。 両方のメカニズムは同じように機能し、環境内の最適な方法を選択することができます。

どちらの場合も、前の手順で作成した SPN が必要なおよび、keytab で SPN を登録する必要があります。

SQL Server サービス keytab ファイルの構成。

1. 構成、 [SPN keytab エントリ](#spn)次のセクションでします。

1. いずれか、 [UPN の追加](#upn)(オプション 1) または[MSA](#msa) (オプション 2) の対応するセクションの手順に従って、keytab ファイルのエントリ。

> [!IMPORTANT]
> UPN/MSA のパスワードを変更、またはに Spn が割り当てられているアカウントのパスワードが変更された、新しいパスワードとキーのバージョン番号 (KVNO) で、keytab を更新する必要があります。 一部のサービスは、パスワードを自動的に回転も可能性があります。 問題のアカウント用にパスワードのローテーション ポリシーを確認し、予期しないダウンタイムを回避するためにスケジュールされたメンテナンス作業に合わせて配置します。

### <a id="spn"></a> SPN keytab エントリ

1. 前の手順で作成した AD アカウントのキーのバージョン番号 (KVNO) を確認します。 通常は 2 ですが、アカウントのパスワードを複数回変更した場合、別の整数がある可能性があります。 SQL サーバーのホスト コンピューターで、次のコマンドを実行します。

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM
   ```

   > [!NOTE]
   > Spn で、ドメインが大きい場合は特に、数分に反映されるまで、ドメインがかかる場合があります。 エラーが発生した場合`kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM`、数分待ってから、もう一度やり直してください。  

1. 開始**ktutil**:

   ```bash
   sudo ktutil
   ```

1. 次のコマンドを使用して各 spn には、keytab エントリを追加します。

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. Keytab ファイルへの書き込みし、ktutil を終了します。

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > **Ktutil**ツールは、パスワードを検証していないため入力を求められたら、正しくする入力であることを確認してください。

### <a id="upn"></a> オプション 1:UPN を使用して、keytab を構成するには

Keytab にコンピューター アカウントを追加**ktutil**します。 (UPN とも呼ばれます) コンピューターのアカウントは存在 **/etc/krb5.keytab**形式で`<hostname>$@<realm.com>`(たとえば、 `sqlhost$@CONTOSO.COM`)。 これらのエントリからコピー **/etc/krb5.keytab**に**mssql.keytab**します。

1. 開始**ktuil**次のコマンドを使用します。

   ```bash
   sudo ktutil
   ```

1. 使用して、 **rkt**コマンドからのエントリのすべてを読み取り、 **/etc/krb5.keytab**します。

   ```bash
   rkt /etc/krb5.keytab
   ```

1. 次に、エントリを一覧表示します。

   ```bash
   list
   ```

1. UPN のないスロット番号のすべてのエントリを削除します。 次のコマンドを繰り返すことによって、この 1 つずつを実行します。

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > エントリが削除されたとき、スロット 1、その代わりに使用する 1 つをすべての値スライドなど。 つまり、スロット 2 のエントリがスロット 1 のエントリが削除されたときに、スロット 1 に移動します。

1. UPN エントリだけが残るまでもう一度エントリを一覧します。

   ```bash
   list
   ```

1. UPN エントリのみがあるときにこれらの値を追加**mssql.keytab**:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. 終了**ktutil**します。

   ```bash
   quit
   ```

### <a id="msa"></a> オプション 2:MSA を使用して、keytab を構成するには

MSA オプションで、SQL Server の Kerberos keytab を作成する必要があります。 すべてを含める必要がありますが、[最初の手順で登録されている Spn](#spn)と Spn が登録されている MSA の資格情報。 

1. SPN keytab 後にエントリが作成になり、ドメインに参加している Linux マシンから、次のコマンドを実行します。

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   この手順では、SPN の所有権を割り当てるユーザー アカウントの KVNO が表示されます。 動作するこの手順では、SPN する必要がありますがアカウントに割り当てられて、MSA、作成中にします。 MSA に SPN が割り当てられていない表示 KVNO は SPN 所有者アカウントは現在のし、構成に使用する正しいできません。  

1. 開始**ktutil**:

   ```bash
   sudo ktutil
   ```

1. 次の 2 つのコマンドを使用して MSA を追加します。

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. Keytab ファイルへの書き込みし、ktutil を終了します。

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. 構成オプションを設定する必要が MSA アプローチを使用する場合ある、 **mssql conf** keytab ファイルへのアクセス中に使用される MSA を指定するためのツール。 次の値を確認します。 **/var/opt/mssql/mssql.conf**します。

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > MSA 名とドメイン \ アカウント名ではなくのみが含まれます。

## <a id="securekeytab"></a> Keytab ファイルをセキュリティ保護します。

ドメイン上の SQL Server の権限を借用、mssql アカウントのみがある読み取りアクセスになるよう、ファイルへのアクセスを制限するように keytab ファイルへのアクセスを持つユーザーことができます。

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Kerberos 認証に keytab ファイルを使用する SQL Server の構成します。

Keytab ファイルを Kerberos 認証の使用を開始するのに SQL Server を構成するのにには、次の手順を使用します。

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

必要に応じてパフォーマンスを向上させるために、ドメイン コント ローラーへの UDP 接続を無効にします。 多くの場合、UDP 接続一貫して失敗する構成オプションを設定するために、ドメイン コント ローラーに接続するときに **/etc/krb5.conf** UDP 呼び出しをスキップします。 編集 **/etc/krb5.conf**し、次のオプションを設定します。

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

この時点では、次のように SQL Server で AD ベースのログインを使用する準備が完了したら。

## <a id="createsqllogins"></a> TRANSACT-SQL での AD ベースのログインを作成します。

1. SQL Server に接続し、AD ベースの新しいログインを作成します。

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. ログインが現在表示されていることを確認、 [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)システム カタログ ビュー。

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> AD 認証を使用して SQL Server に接続します。

ドメインの資格情報を使用して、クライアント コンピューターにログインします。 これで、AD 認証を使用して、パスワードを再入力しなくても、SQL Server に接続することができます。 AD グループのログインを作成する場合、そのグループのメンバーになっている AD ユーザーは、同じ方法で接続できます。

使用してドライバーをクライアントが AD 認証を使用する特定の接続文字列パラメーターに依存します。 次のセクションでは、次の例を検討してください。

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>ドメインに参加している Linux クライアントに sqlcmd

使用してドメインに参加している Linux クライアントにログイン**ssh**とドメインの資格情報。

```bash
ssh -l user@contoso.com client.contoso.com
```

インストールされていることを確認、 [mssql ツール](sql-server-linux-setup-tools.md)をパッケージ化しを使用して接続**sqlcmd**任意の資格情報の指定なし。

```bash
sqlcmd -S mssql-host.contoso.com
```

### <a name="ssms-on-a-domain-joined-windows-client"></a>ドメインに参加している Windows クライアント上の SSMS

ドメインの資格情報を使用してドメインに参加している Windows クライアントにログインします。 SQL Server Management Studio がインストールされているかどうかを確認し、SQL Server インスタンスに接続 (たとえば、 `mssql-host.contoso.com`) を指定して**Windows 認証**で、**サーバーへの接続**ダイアログ。

### <a name="ad-authentication-using-other-client-drivers"></a>その他のクライアント ドライバーを使用して AD 認証

次の表では、他のクライアント ドライバー用の推奨事項について説明します。

| クライアント ドライバー | 推奨 |
|---|---|
| **JDBC** | SQL Server に接続するのにには、Kerberos 統合認証を使用します。 |
| **ODBC** | 統合認証を使用します。 |
| **ADO.NET** | 接続文字列の構文。 |

## <a id="additionalconfig"></a> 追加の構成オプション

などのサードパーティ製ユーティリティを使用している場合[PBI](https://www.beyondtrust.com/)、 [VAS](https://www.oneidentity.com/products/authentication-services/)、または[Centrify](https://www.centrify.com/) AD への Linux ホストに参加するドメインには、openldap を使用して SQL server を強制ライブラリを直接構成できる、 **disablesssd**オプションを**mssql conf**次のようにします。

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> などのユーティリティがある**realmd**を設定する SSSD、他のツールの中になど、PBI、VAS および Centrify に SSSD をセットアップできません。 AD ドメインに参加するために使用するユーティリティが SSSD を設定していない場合は、構成勧め**disablesssd**オプションを`true`します。 SQL Server を ad openldap メカニズムに戻る前に SSSD を使用するときに必要ありません、SQL Server が直接 SSSD 機構のバイパス openldap 呼び出しを行うように構成するパフォーマンスが高くなります。

ドメイン コント ローラーは、LDAPS をサポートする場合は、LDAPS 経由にするドメイン コント ローラーに SQL Server からのすべての接続を強制することができます。 クライアントは、ドメイン コント ローラーを問い合わせてください ldaps では、次の bash コマンドの実行をチェックする`ldapsearch -H ldaps://contoso.com:3269`します。 のみ LDAPS を使用する SQL Server を設定するには次の手順を実行します。

```bash
sudo mssql-conf set network.forcesecureldap true
systemctl restart mssql-server
```

AD ドメインに参加している場合、LDAPS を使用して、SSSD 経由ではこのホストが SSSD パッケージを使用して行われたと**disablesssd**が設定されていないを true にします。 場合**disablesssd**に設定されていると true **forcesecureldap** SQL Server によって行われた openldap ライブラリ呼び出し経由で LDAPS プロトコルを使って true に設定されています。

### <a name="post-sql-server-2017-cu14"></a>Post SQL Server 2017 CU14

SQL Server がサード パーティ プロバイダーを使用して AD ドメイン コント ローラーに参加しているが、一般的な AD 参照を設定して openldap 呼び出しを使用する構成されている場合は、SQL Server 2017 の CU14 以降**disablesssd**に true の場合、使用することも**enablekdcfromkrb5**の KDC サーバーに対する逆引き DNS 参照ではなく KDC 検索 krb5 ライブラリを使用する SQL Server を強制的にするオプション。

SQL Server が通信しようとするドメイン コント ローラーを手動で構成するシナリオに役立つことが考えられます。 KDC の一覧を使用して openldap ライブラリ メカニズムを使用して**krb5.conf**します。

最初に、設定**disablessd**と**enablekdcfromkrb5conf**を true に、SQL Server を再起動します。

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

KDC の一覧を構成し、 **/etc/krb5.conf**次のようにします。

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> などのユーティリティを使用することは、お勧めしません**realmd**、設定の構成中に、ドメインに Linux ホストに参加するときに SSSD **disablesssd**を SQL Server で使用するように true にopenldap 呼び出し代わりに Active Directory の SSSD の関連の呼び出し。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、SQL Server on Linux での Active Directory 認証を設定する方法を説明しました。 学習したします。
> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメインにホスト
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サービス keytab を構成する
> * TRANSACT-SQL で AD に基づくログインを作成する
> * AD Authentication を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] へ接続する

次に、その他のセキュリティのシナリオについて調べる for SQL Server on Linux。

> [!div class="nextstepaction"]
> [SQL Server on Linux への接続の暗号化](sql-server-linux-encrypted-connections.md)
