---
title: チュートリアル:SQL Server on Linux に対して AD 認証を使用する
titleSuffix: SQL Server
description: このチュートリアルでは、SQL Server on Linux 用に AD 認証を構成する手順について説明します。
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.date: 04/01/2019
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 69bbeb31f8da4023bd0630ae0d944165407e2dec
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68027328"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>チュートリアル:SQL Server on Linux で Active Directory 認証を使用する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、Active Directory (AD) 認証 (統合認証とも呼ばれます) をサポートするように [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux を構成する方法について説明します。 概要については、「[SQL Server on Linux に対する Active Directory 認証](sql-server-linux-active-directory-auth-overview.md)」をご覧ください。

このチュートリアルは、次のタスクで構成されています。

> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ホストを AD ドメインに参加させる
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスの keytab を構成する
> * keytab ファイルをセキュリティで保護する
> * Kerberos 認証に keytab ファイルを使用するように SQL Server を構成する
> * Transact-SQL で AD ベースのログインを作成する
> * AD 認証を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に接続する

## <a name="prerequisites"></a>Prerequisites

AD 認証を構成する前に、次のことを行う必要があります。

* ネットワーク上に AD ドメイン コントローラー (Windows) をセットアップします  
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストール
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ホストを AD ドメインに参加させる

SQL Server Linux ホストを Active Directory ドメイン コントローラーに参加させる必要があります。 Active Directory ドメインに参加する方法については、「[Linux ホスト上の SQL Server を Active Directory ドメインに参加させる](sql-server-linux-active-directory-join-domain.md)」をご覧ください。

## <a id="createuser"></a> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用の AD ユーザー (または MSA) を作成して SPN を設定する

> [!NOTE]
> 以下の手順では、[完全修飾ドメイン名](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)を使います。 **Azure** を使用している場合は、先に進む前に **[作成する](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** 必要があります。

1. ドメイン コントローラーで [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) PowerShell コマンドを実行して、有効期限がないパスワードを持つ新しい AD ユーザーを作成します。 次の例では `mssql` というアカウント名を使っていますが、任意のアカウント名にすることができます。 アカウントの新しいパスワードを入力するように求められます。

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > SQL Server 専用の AD アカウントを使用して、SQL Server の資格情報が同じアカウントを使用する他のサービスと共有されないようにすることが、セキュリティのベスト プラクティスです。 ただし、アカウントのパスワードがわかっている場合は、必要に応じて既存の AD アカウントを再利用できます (次のステップで keytab ファイルを生成するために必要です)。

2. **setspn.exe** ツールを使って、このアカウントの ServicePrincipalName (SPN) を設定します。 SPN は、次の例で指定したとおりに書式設定されている必要があります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ホスト コンピューターの完全修飾ドメイン名は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ホスト上で `hostname --all-fqdns` を実行することによって確認できます。 別のポート番号を使うように [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を構成している場合を除き、TCP ポートは 1433 にする必要があります。

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > エラー `Insufficient access rights` が発生する場合は、ドメイン管理者に連絡して、このアカウントに SPN を設定するための十分なアクセス許可があることを確認してください。
   >
   > 後で TCP ポートを変更する場合は、新しいポート番号を指定して **setspn** コマンドを再度実行する必要があります。 また、次のセクションの手順に従って、SQL Server サービスの keytab に新しい SPN を追加する必要があります。

詳細については、「 [Kerberos 接続用のサービス プリンシパル名の登録](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)」を参照してください。

## <a id="configurekeytab"></a> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスの keytab を構成する

SQL Server サービスの keytab ファイルを構成するには、2 つの方法があります。 1 つ目のオプションはコンピューター アカウント (UPN) を使用する方法で、2 つ目のオプションは keytab 構成で管理されたサービス アカウント (MSA) を使用する方法です。 どちらのメカニズムも同じように機能し、環境に最適な方法を選択できます。

どちらの場合も、前のステップで作成した SPN が必要であり、SPN を keytab に登録する必要があります。

SQL Server サービスの keytab ファイルを構成するには:

1. 次のセクションで、[SPN の keytab エントリ](#spn)を構成します。

1. 次に、各セクションの手順に従って、[UPN](#upn) (オプション 1) または[MSA](#msa) (オプション 2) エントリを keytab ファイルに追加します。

> [!IMPORTANT]
> UPN/MSA のパスワードが変更された場合、または SPN が割り当てられているアカウントのパスワードが変更された場合は、新しいパスワードとキー バージョン番号 (KVNO) を使用して、keytab を更新する必要があります。 一部のサービスでは、パスワードが自動的にローテーションされる場合もあります。 問題のアカウントのパスワード ローテーション ポリシーを確認し、予期しないダウンタイムが発生しないように、スケジュールされたメンテナンス アクティビティと一致させます。

### <a id="spn"></a> SPN の keytab エントリ

1. 前のステップで作成した AD アカウントのキー バージョン番号 (KVNO) を確認します。 通常は 2 ですが、アカウントのパスワードを複数回変更した場合は、別の整数になることがあります。 SQL Server のホスト コンピューターで、次のコマンドを実行します。

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM
   ```

   > [!NOTE]
   > SPN がドメインに反映されるまでに数分かかる場合があります (特に、ドメインが大きい場合)。 `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM` というエラーが発生する場合は、数分待ってからもう一度やり直してください。  

1. **ktutil** を開始します。

   ```bash
   sudo ktutil
   ```

1. 次のコマンドを使用して、各 SPN の keytab エントリを追加します。

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. keytab をファイルに書き込み、ktutil を終了します。

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > **ktutil** ツールではパスワードが検証されないので、要求されたら正しく入力してください。

### <a id="upn"></a> オプション 1: UPN を使用して keytab を構成する

**ktutil** で keytab にコンピューター アカウントを追加します。 コンピューター アカウント (UPN とも呼ばれます) は、`<hostname>$@<realm.com>` という形式で **/etc/krb5.keytab** に存在します (例: `sqlhost$@CONTOSO.COM`)。 これらのエントリを、 **/etc/krb5.keytab** から **mssql.keytab** にコピーします。

1. 次のコマンドで **ktuil** を開始します。

   ```bash
   sudo ktutil
   ```

1. **rkt** コマンドを使って、 **/etc/krb5.keytab** からすべてのエントリを読み取ります。

   ```bash
   rkt /etc/krb5.keytab
   ```

1. 次に、エントリを一覧表示します。

   ```bash
   list
   ```

1. UPN ではないすべてのエントリをスロット番号で削除します。 これは、次のコマンドを繰り返して、一度に 1 つずつ実行します。

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > スロット 1 などのエントリを削除すると、すべての値が 1 つ上にスライドします。 これは、スロット 1 のエントリを削除すると、スロット 2 のエントリがスロット 1 に移動することを意味します。

1. UPN のエントリだけが残るまで、エントリを再度一覧表示します。

   ```bash
   list
   ```

1. UPN のエントリだけが残ったら、それらの値を **mssql.keytab** に追加します。

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. **ktutil** を終了します。

   ```bash
   quit
   ```

### <a id="msa"></a> オプション 2: MSA を使用して keytab を構成する

MSA オプションの場合は、SQL Server の Kerberos keytab を作成する必要があります。 [最初のステップで登録したすべての SPN](#spn) と、SPN が登録されている MSA の資格情報が、含まれている必要があります。 

1. SPN の keytab エントリを作成した後、ドメインに参加している Linux コンピューターから次のコマンドを実行します。

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   このステップでは、SPN の所有権が割り当てられているユーザー アカウントの KVNO が表示されます。 このステップの処理が行われるには、作成時に SPN が MSA アカウントに割り当てられている必要があります。 SPN が MSA に割り当てられていない場合、表示される KVNO は現在の SPN 所有者アカウントであり、構成に使用する正しい値ではありません。  

1. **ktutil** を開始します。

   ```bash
   sudo ktutil
   ```

1. 次の 2 つのコマンドを使用して、MSA を追加します。

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. keytab をファイルに書き込み、ktutil を終了します。

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. MSA のアプローチを使う場合は、**mssql-conf** ツールで構成オプションを設定し、keytab ファイルにアクセスするときに使う MSA を指定する必要があります。 以下の値が **/var/opt/mssql/mssql.conf** にあることを確認します。

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > MSA 名だけが含まれるようにし、ドメイン\アカウント名は含めないでください。

## <a id="securekeytab"></a> keytab ファイルをセキュリティで保護する

この keytab ファイルにアクセスできるすべてのユーザーは、ドメインで SQL Server を偽装できるので、mssql アカウントのみに読み取りアクセス権が付与されるように、ファイルへのアクセスを制限する必要があります。

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Kerberos 認証に keytab ファイルを使用するように SQL Server を構成する

次の手順を使用して、Kerberos 認証用の keytab ファイルを使って開始するように SQL Server を構成します。

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

必要に応じて、パフォーマンスを向上させるため、ドメイン コントローラーへの UDP 接続を無効にします。 多くの場合、ドメイン コントローラーに接続するときは UDP 接続が常に失敗するので、UDP の呼び出しをスキップするように **/etc/krb5.conf** の構成オプションを設定できます。 **/etc/krb5.conf** を編集して、次のオプションを設定します。

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

この時点で、次のように SQL Server で AD ベースのログインを使用できるようになります。

## <a id="createsqllogins"></a> Transact-SQL で AD ベースのログインを作成する

1. SQL Server に接続し、AD ベースの新しいログインを作成します。

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) システム カタログ ビューにログインが表示されていることを確認します。

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> AD 認証を使用して SQL Server に接続する

ドメイン資格情報を使用してクライアント コンピューターにログインします。 AD 認証を使用してパスワードを再入力することなく SQL Server に接続できるようになります。 AD グループに対するログインを作成した場合は、そのグループのメンバーであるすべての AD ユーザーが、同じ方法で接続できます。

クライアントで AD 認証を使用するための特定の接続文字列パラメーターは、使用しているドライバーによって異なります。 次のセクションの例を検討してください。

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>ドメインに参加している Linux クライアントでの sqlcmd

**ssh** とドメイン資格情報を使用して、ドメインに参加している Linux クライアントにログインします。

```bash
ssh -l user@contoso.com client.contoso.com
```

[mssql-tools](sql-server-linux-setup-tools.md) パッケージがインストールされていることを確認した後、資格情報を指定せずに **sqlcmd** を使用して接続します。

```bash
sqlcmd -S mssql-host.contoso.com
```

### <a name="ssms-on-a-domain-joined-windows-client"></a>ドメインに参加している Windows クライアントでの SSMS

ドメイン資格情報を使用して、ドメインに参加している Windows クライアントにログインします。 SQL Server Management Studio がインストールされていることを確認した後、 **[サーバーへの接続]** ダイアログで **[Windows 認証]** を指定して、SQL Server インスタンス (例 : `mssql-host.contoso.com`) に接続します。

### <a name="ad-authentication-using-other-client-drivers"></a>他のクライアント ドライバーを使用した AD 認証

次の表では、他のクライアント ドライバーに関する推奨事項について説明します。

| クライアント ドライバー | 推奨 |
|---|---|
| **JDBC** | Kerberos 統合認証を使用して、SQL Server に接続します。 |
| **ODBC** | 統合認証を使用します。 |
| **ADO.NET** | 接続文字列の構文。 |

## <a id="additionalconfig"></a> その他の構成オプション

[PBIS](https://www.beyondtrust.com/)、[VAS](https://www.oneidentity.com/products/authentication-services/)、[Centrify](https://www.centrify.com/) などのサードパーティ製ユーティリティを使って Linux ホストを AD ドメインに参加させていて、SQL Server で強制的に openldap ライブラリを直接使いたい場合は、次のように **mssql-conf** で **disablesssd** オプションを構成できます。

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> **realmd** のように SSSD が設定されるユーティリティもありますが、PBIS、VAS、Centrify などの他のツールでは SSSD は設定されません。 AD ドメインへの参加に使用しているユーティリティで SSSD が設定されない場合は、**disablesssd** オプションを `true` に設定することをお勧めします。 openldap メカニズムにフォールバックする前に、SQL Server では AD に対して SSSD の使用が試みられるので、必須ではありませんが、SQL Server で SSSD メカニズムをバイパスして openldap が直接呼び出されるように構成すると、パフォーマンスが向上します。

ドメイン コントローラーで LDAPS がサポートされている場合は、SQL Server からドメイン コントローラーへのすべての接続で LDAPS が使用されるように強制することができます。 クライアントが LDAPS 経由でドメイン コントローラーに接続できることを確認するには、Bash コマンド `ldapsearch -H ldaps://contoso.com:3269` を実行します。 LDAPS のみを使うように SQL Server を設定するには、以下を実行します。

```bash
sudo mssql-conf set network.forcesecureldap true
systemctl restart mssql-server
```

これにより、ホストでの AD ドメイン参加が SSSD パッケージによって行われていて、**disablesssd** が true に設定されていない場合は、SSSD で LDAPS が使用されます。 **disablesssd** が true に設定されていて、**forcesecureldap** が true に設定されている場合は、SQL Server によって行われる openldap ライブラリの呼び出しで LDAPS プロトコルが使われます。

### <a name="post-sql-server-2017-cu14"></a>SQL Server 2017 CU14 以降

SQL Server 2017 CU14 以降では、SQL Server で、AD ドメイン コントローラーへの参加にサードパーティのプロバイダーが使われていて、**disablesssd** を true に設定することによって一般的な AD 参照に openldap の呼び出しが使われるように構成されている場合は、**enablekdcfromkrb5** オプションを使うことにより、KDC サーバーの逆引き DNS 参照ではなく、krb5 ライブラリを使って KDC 参照を行うように、SQL Server を強制することができます。

これは、SQL Server が通信を試みるドメイン コントローラーを手動で構成する場合に便利です。 また、**krb5.conf** で KDC リストを使うことにより、openldap ライブラリのメカニズムを使用します。

最初に、**disablessd** と **enablekdcfromkrb5conf** を true に設定した後、SQL Server を再起動します。

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

次に、 **/etc/krb5.conf** で KDC リストを次のように構成します。

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> 推奨されませんが、Linux ホストをドメインに参加させるときに SSSD が設定される **realmd** などのユーティリティを使用しながら、**disablesssd** を true に設定することで、SQL Server による Active Directory 関連の呼び出しに SSSD ではなく openldap の呼び出しが使われるようにすることができます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、SQL Server on Linux で Active Directory 認証を設定する方法について説明しました。 以下の方法を学習しました。
> [!div class="checklist"]
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ホストを AD ドメインに参加させる
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用の AD ユーザーを作成し、SPN を設定する
> * [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスの keytab を構成する
> * Transact-SQL で AD ベースのログインを作成する
> * AD 認証を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に接続する

次に、SQL Server on Linux の他のセキュリティ シナリオを調べます。

> [!div class="nextstepaction"]
> [SQL Server on Linux への接続の暗号化](sql-server-linux-encrypted-connections.md)
