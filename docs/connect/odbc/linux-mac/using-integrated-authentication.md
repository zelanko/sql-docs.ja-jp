---
title: "統合認証を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 162b94d551ea8625b6b22fafec61e19038dc2051
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-integrated-authentication"></a>統合認証を使用する
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Kerberos を使用して Linux および macOS のサポートの接続で統合認証です。 MIT Kerberos キー配布センター (KDC) をサポートし、Generic Security Services アプリケーション プログラム インターフェイス (GSSAPI) および Kerberos v5 ライブラリと連携します。
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversionmdmd-from-an-odbc-application"></a>接続に統合認証を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]ODBC アプリケーションから  

指定して Kerberos 統合認証を有効にすることができます**Trusted_Connection = yes**の接続文字列で**SQLDriverConnect**または**SQLConnect**です。 例:  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
を DSN に接続するときに追加することも**Trusted_Connection = yes** DSN エントリに`odbc.ini`です。
  
`-E`オプション`sqlcmd`と`-T`のオプション`bcp`統合認証を指定にも使用できます参照してください[を使用した接続**sqlcmd** ](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)と。[使用した接続**bcp** ](../../../connect/odbc/linux-mac/connecting-with-bcp.md)詳細についてはします。

クライアント プリンシパルへの接続に移動することを確認[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Kerberos KDC で既に認証されています。
  
**ServerSPN** と **FailoverPartnerSPN** はサポートされていません。  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>サービスとして実行するように Linux または macOS ODBC ドライバー アプリケーションを設計を展開します。

システム管理者が Kerberos 認証を使用してに接続するサービスとして実行するアプリケーションを展開できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
まず、クライアントで Kerberos を構成し、アプリケーションが既定のプリンシパルの Kerberos 資格情報を使用できることを確認してください必要があります。

使用することを確認してください。`kinit`または PAM (Pluggable Authentication Module) を取得して、次のメソッドのいずれかを使用して、接続に使用されるプリンシパルの TGT をキャッシュします。  
  
-   実行`kinit`プリンシパル名とパスワードを渡して、します。  
  
-   実行`kinit`プリンシパルの名前とによって作成されたプリンシパルのキーを含む keytab ファイルの場所を渡して、`ktutil`です。  
  
-   システムにログインが実行されたことを確認してください。 Kerberos PAM (Pluggable Authentication Module) を使用します。

デザインで Kerberos 資格情報が期限切れのため、サービスとしてアプリケーションを実行すると、継続的なサービス可用性を確保するための資格情報を更新します。 ODBC ドライバーが更新しない資格情報自体です。あることを確認してください、`cron`ジョブ、またはその有効期限前に資格情報を更新する定期的に実行されるスクリプト。 更新するたびに、パスワードを必要とするを回避するのには、keytab ファイルを使用することができます。  
  
[Kerberos の構成と使用](http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) では、Linux 上でサービスを Kerberos 認証する方法の詳細を提供しています。
  
## <a name="tracking-access-to-a-database"></a>データベースへのアクセスを追跡する

システム アカウントを使用してアクセスするときに、データベース管理者はデータベースへのアクセスの監査証跡を作成できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]統合認証を使用します。  
  
ログイン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]システム アカウントを使用し、セキュリティ コンテキストを偽装する Linux の機能はありません。 そのため、ユーザーを特定するための詳細が必要です。
  
内のアクティビティを監査する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]システム アカウント以外のユーザーの代理として、アプリケーションを使用する必要があります[!INCLUDE[tsql](../../../includes/tsql_md.md)] **EXECUTE AS**です。  
  
アプリケーションのパフォーマンスを向上させるため、アプリケーションで接続プールを統合認証と監査とともに使用できます。 ただし、接続プール、統合認証を使用して監査を組み合わせることを作成、セキュリティ上のリスク unixODBC ドライバー マネージャーが、ユーザーは、異なるプールされた接続を再利用するためです。 詳細については、「 [ODBC Connection Pooling (ODBC 接続プール)](http://www.unixodbc.org/doc/conn_pool.html)」を参照してください。  

再利用する前に、アプリケーションを実行してプールされた接続をリセットする必要があります`sp_reset_connection`です。  

## <a name="using-active-directory-to-manage-user-identities"></a>Active Directory を使用して、ユーザー ID を管理する

アプリケーションは、システム管理者が別々 のログイン資格情報のセットを管理する必要はありません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 統合認証のキー配布センター (KDC) として Active Directory を構成することができます。 参照してください[Microsoft Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747(v=vs.85).aspx)詳細についてはします。

## <a name="using-linked-server-and-distributed-queries"></a>リンク サーバーと分散クエリを使用する

開発者は、SQL 資格情報の個別セットを保持するデータベース管理者がいなくても、リンク サーバーまたは分散クエリを使用するアプリケーションを展開できます。 このような状況は、開発者は、統合認証を使用するアプリケーションを構成する必要があります。  
  
-   ユーザーは、クライアント コンピューターにログインし、アプリケーション サーバーに対して認証します。  
  
-   アプリケーション サーバーが別のデータベースとして認証しに接続する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]別のデータベースにデータベース ユーザーとして認証 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
統合認証を構成すると、資格情報がリンク サーバーに渡されます。  
  
## <a name="integrated-authentication-and-sqlcmd"></a>統合認証 と sqlcmd
アクセスする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]統合認証を使用して、`-E`オプション`sqlcmd`です。 実行するアカウントを確認してください`sqlcmd`既定の Kerberos クライアント プリンシパルと関連付けられています。

## <a name="integrated-authentication-and-bcp"></a>統合認証 と bcp
アクセスする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]統合認証を使用して、`-T`オプション`bcp`です。 実行するアカウントを確認してください`bcp`既定の Kerberos クライアント プリンシパルと関連付けられています。 
  
使用すると、エラーは`-T`で、`-U`または`-P`オプション。
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversionmdmd"></a>によって登録された SPN でサポートされる構文[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]

接続文字列または接続属性で Spn に使用される構文は次のとおりです。  

|構文|説明|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|TCP が使用される場合にプロバイダーが生成する既定の SPN。 *port* は、TCP ポート番号です。 *fqdn* は完全修飾ドメイン名です。|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Linux または macOS Active Directory を使用してコンピューターの認証

Kerberos を構成するには、データを入力、`krb5.conf`ファイル。 `krb5.conf``/etc/`例: 構文を使用して別のファイルを参照することができますが、`export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`です。 例を次に示します`krb5.conf`ファイル。  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
```  
  
使用することができます、Linux または macOS コンピューターが DNS サーバーを提供する Windows DHCP サーバーで使用する動的ホスト構成プロトコル (DHCP) を使用する構成されている場合**dns_lookup_kdc = true**です。 Kerberos を使用して、コマンドを実行して、ドメインにサインインするようになりましたが、`kinit alias@YYYY.CORP.CONTOSO.COM`です。 渡されるパラメーター`kinit`大文字小文字を区別し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]そのユーザーがコンピューターをドメインに存在するように構成は必要`alias@YYYY.CORP.CONTOSO.COM`ログイン用に追加します。 ここで、信頼関係接続を使用することができます (**Trusted_Connection = [はい]**接続文字列で**bcp-t**、または**sqlcmd -E**)。  
  
Linux または macOS コンピューターの時刻とタイム Kerberos キー配布センター (KDC) では、閉じるでなければなりません。 システム時刻が正しく設定されて、たとえばネットワーク タイム プロトコル (NTP) を使用して、ことを確認します。  

Kerberos 認証が失敗した場合、ODBC driver on Linux または macOS は NTLM 認証を使用しません。  

Linux または macOS のコンピューターを Active Directory の認証の詳細については、次を参照してください[Active Directory と Linux クライアントを認証](http://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048)と[Active DirectoryとOSXを統合するためのベストプラクティス。](http://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Kerberos の構成の詳細については、次を参照してください。、 [MIT Kerberos のドキュメント](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html)です。

## <a name="see-also"></a>参照  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)

[Azure Active Directory を使用します。](../../../connect/odbc/using-azure-active-directory.md)
