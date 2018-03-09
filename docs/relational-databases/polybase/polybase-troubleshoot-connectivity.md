---
title: "PolyBase Kerberos の接続性のトラブルシューティング | Microsoft Docs"
description: 
services: 
documentationcenter: 
author: alazad-msft
manager: 
editor: 
tags: 
ms.assetid: 
ms.service: 
ms.component: polybase
ms.suite: sql
ms.custom: 
ms.workload: 
ms.tgt_pltfrm: na
ms.devlang: 
ms.topic: article
ms.date: 07/19/2017"
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.author: alazad
ms.openlocfilehash: cbbc687cf4c3a5edf769ab973879bc81f8db8406
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="troubleshoot-polybase-kerberos-connectivity"></a>PolyBase Kerberos の接続性のトラブルシューティング
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Kerberos によるセキュリティで保護された Hadoop クラスターに対して PolyBase を使用する場合、PolyBase に組み込まれている対話型診断ツールを使用すると、認証の問題のトラブルシューティングに役立ちます。 

この記事は、このツールを使用したこのような問題のデバッグ方法を示すガイドとして利用できます。

## <a name="prerequisites"></a>Prerequisites

1. PolyBase がインストールされた SQL Server 2016 RTM CU6 / SQL Server 2016 SP1 CU3 / SQL Server 2017 またはそれ以降
1. Kerberos (Active Directory または MIT) によるセキュリティで保護された Hadoop クラスター (Cloudera または Hortonworks)

## <a name="introduction"></a>概要
まず Kerberos プロトコルの概要を理解することが役に立ちます。 次の 3 つのアクターが関係します。
1. Kerberos クライアント (SQL Server)
1. セキュリティで保護されたリソース (HDFS、MR2、YARN、ジョブ履歴など)
1. キー配布センター (Active Directory のドメイン コント ローラーと呼ばれる)

Hadoop によるセキュリティで保護された各リソースは、Hadoop クラスターの Kerberos 対応プロセスの一部として、一意の**サービス プリンシパル名 (SPN)** を使用して**キー配布センター (KDC)** に登録されます。 この登録は、クライアントが KDC から**チケット保証チケット (TGT)** と呼ばれる一時的なユーザー チケットを取得することを目標に行われます。TGT は、クライアントがアクセスする対象の特定の SPN に対して、**サービス チケット (ST)** と呼ばれる別の一時的なチケットを要求するために必要です。  
PolyBase では、Kerberos によるセキュリティで保護されたリソースに対する認証が要求されたときに、次の 4 ラウンドトリップ ハンドシェイクが行われます。
1. SQL Server が KDC に接続し、ユーザー用に TGT を取得します。 KDC の秘密キーを使用して TGT が暗号化されます。
1. SQL Server は、Hadoop によるセキュリティで保護されたリソース (例: HDFS) を呼び出し、どの SPN の ST が必要なのかを判別します。
1. SQL Server は、KDC に戻って TGT を渡し、セキュリティで保護されたその特定のリソースにアクセスするための ST を要求します。 ST は、セキュリティで保護されたサービスの秘密キーを使用して暗号化されます。
1. SQL Server は ST を Hadoop に転送し、そのサービスに対してセッションが作成されるように認証を取得します。

![](./media/polybase-sqlserver.png)

認証の問題は、上記の 4 つのステップのうちの 1 つ以上に分類されます。 迅速なデバッグを支援するため、PolyBase には、障害発生時点の特定に役立つ統合された診断ツールが導入されています。

## <a name="troubleshooting"></a>トラブルシューティング
PolyBase には、Hadoop クラスターのプロパティを含む複数の構成 XML があります。 つまり、次のファイルです。
- core-site.xml
- hdfs-site.xml
- hive-site.xml
- jaas.conf
- mapred-site.xml
- yarn-site.xml

これらのファイルは、次の場所にあります。

\\[システム ドライブ\\]:{インストール パス}\\{インスタンス}\\{名前}\\MSSQL\\Binn\\Polybase\\Hadoop\\conf

たとえば、SQL Server 2016 の既定では、"C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Binn\\Polybase\\Hadoop\\conf" です。

次の 3 つのプロパティに環境に応じた値を設定して、PolyBase 構成ファイル **core-site.xml** の 1 つを更新します。
```xml
<property>
    <name>polybase.kerberos.realm</name>
    <value>CONTOSO.COM</value>
</property>
<property>
    <name>polybase.kerberos.kdchost</name>
    <value>kerberos.contoso.com</value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```
プッシュダウン操作を希望する場合は、その他の XML も後で更新する必要があります。しかし、このファイルを構成しただけでも、少なくとも HDFS ファイル システムにアクセスできるようになります。

ツールは SQL Server とは独立して実行できます。そのため、XML を更新する場合に実行中である必要はなく、再起動する必要もありません。 ツールを実行するには、SQL Server がインストールされているホストで次のコマンドを実行します。

```
> cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase  
> java -classpath ".\Hadoop\conf;.\Hadoop\*;.\Hadoop\HDP2_2\*" com.microsoft.polybase.client.HdfsBridge {Name Node Address} {Name Node Port} {Service Principal} {Filepath containing Service Principal's Password} {Remote HDFS file path (optional)}
```

## <a name="arguments"></a>引数
| 引数 | Description|
| --- | --- |
| *名前ノードのアドレス* | 名前ノードの IP または FQDN です。 CREATE EXTERNAL DATA SOURCE T-SQL の "LOCATION" 引数を参照します。|
| *名前ノードのポート* | 名前ノードのポートです。 CREATE EXTERNAL DATA SOURCE T-SQL の "LOCATION" 引数を参照します。 通常は 8020 です。 |
| *サービス プリンシパル* | KDC に対する管理サービス プリンシパルです。 CREATE DATABASE SCOPED CREDENTIAL T-SQL で "IDENTITY" 引数として使用するプリンシパルと一致する必要があります。|
| *サービスのパスワード* | コンソールにパスワードを入力するのではなく、パスワードをファイルに保存し、そのファイルのパスをここに指定します。 CREATE DATABASE SCOPED CREDENTIAL T-SQL で "SECRET" 引数として使用するプリンシパルと一致する必要があります。 |
| *リモート HDFS ファイル パス (省略可能) * | アクセスする対象である既存のファイルのパスです。 指定しない場合、ルート "/" が使用されます。 |

## <a name="example"></a>例
```dos
java -classpath ".\Hadoop\conf;.\Hadoop\*;.\Hadoop\HDP2_2\*" com.microsoft.polybase.client.HdfsBridge 10.193.27.232 8020 admin_user C:\temp\kerberos_pass.txt
```
拡張デバッグ用の詳細な出力ですが、MIT を使用しているか AD を使用しているかにかかわらず、確認する主要なチェックポイントは 4 つしかありません。 それらは前述した 4 つのステップに対応しています。 

MIT KDC からの抜粋を以下に示します。 MIT と AD の完全なサンプル出力は、この記事の終わりの「参照」から確認できます。

## <a name="checkpoint-1"></a>チェックポイント 1
サーバー プリンシパル = krbtgt/*MYREALM.COM@MYREALM.COM* のチケットの 16 進数ダンプが存在する必要があります。 これは、SQL Server が KDC に対して認証され、TGT を受け取ったことを示します。 それ以外の場合は、問題は Hadoop ではなく厳密に SQL Server と KDC の間に存在します。

PolyBase は AD と MIT 間の信頼関係を**サポートしていない**ため、Hadoop クラスターに構成されているのと同じ KDC に対して構成されている必要があります。 このような環境では、手動でその KDC にサービス アカウントを作成し、そのアカウントを使って認証を実行できます。
```dos
|>>> KrbAsReq creating message 
 >>> KrbKdcReq send: kdc=kerberos.contoso.com UDP:88, timeout=30000, number of retries =3, #bytes=143 
 >>> KDCCommunication: kdc=kerberos.contoso.com UDP:88, timeout=30000,Attempt =1, #bytes=143 
 >>> KrbKdcReq send: #bytes read=646 
 >>> KdcAccessibility: remove kerberos.contoso.com 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 >>> KrbAsRep cons in KrbAsReq.getReply myuser 
 [2017-04-25 21:34:33,548] INFO 687[main] - com.microsoft.polybase.client.KerberosSecureLogin.secureLogin(KerberosSecureLogin.java:97) - Subject: 
 Principal: admin_user@CONTOSO.COM 
 Private Credential: Ticket (hex) = 
 0000: 61 82 01 48 30 82 01 44 A0 03 02 01 05 A1 0E 1B a..H0..D........ 
 0010: 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D A2 21 30 .CONTOSO.COM.!0 
 0020: 1F A0 03 02 01 02 A1 18 30 16 1B 06 6B 72 62 74 ........0...krbt 
 0030: 67 74 1B 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D gt..CONTOSO.COM 
 0040: A3 82 01 08 30 82 01 04 A0 03 02 01 10 A1 03 02 ....0........... 
 *[…Condensed…]* 
 0140: 67 6D F6 41 6C EB E0 C3 3A B2 BD B1 gm.Al...:... 
 Client Principal = admin_user@CONTOSO.COM 
 Server Principal = krbtgt/CONTOSO.COM@CONTOSO.COM 
 *[…Condensed…]* 
 [2017-04-25 21:34:34,500] INFO 1639[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1579) - Successfully authenticated against KDC server. 
```
## <a name="checkpoint-2"></a>チェックポイント 2
PolyBase は HDFS へのアクセスを試行しますが、必要なサービス チケットが要求に含まれていないため、アクセスは失敗します。
```dos
 [2017-04-25 21:34:34,501] INFO 1640[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1584) - Attempting to access external filesystem at URI: hdfs://10.193.27.232:8020 
 Found ticket for admin_user@CONTOSO.COM to go to krbtgt/CONTOSO.COM@CONTOSO.COM expiring on Wed Apr 26 21:34:33 UTC 2017 
 Entered Krb5Context.initSecContext with state=STATE_NEW 
 Found ticket for admin_user@CONTOSO.COM to go to krbtgt/CONTOSO.COM@CONTOSO.COM expiring on Wed Apr 26 21:34:33 UTC 2017 
 Service ticket not found in the subject 
```
## <a name="checkpoint-3"></a>チェックポイント 3
2 番目の 16 進数ダンプは、SQL Server が TGT を使用して、名前ノードの SPN に対応したサービス チケットを KDC から取得できたことを示しています。
```dos
 >>> KrbKdcReq send: kdc=kerberos.contoso.com UDP:88, timeout=30000, number of retries =3, #bytes=664 
 >>> KDCCommunication: kdc=kerberos.contoso.com UDP:88, timeout=30000,Attempt =1, #bytes=664 
 >>> KrbKdcReq send: #bytes read=669 
 >>> KdcAccessibility: remove kerberos.contoso.com 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 >>> KrbApReq: APOptions are 00100000 00000000 00000000 00000000 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 Krb5Context setting mySeqNumber to: 1033039363 
 Created InitSecContextToken: 
 0000: 01 00 6E 82 02 4B 30 82 02 47 A0 03 02 01 05 A1 ..n..K0..G...... 
 0010: 03 02 01 0E A2 07 03 05 00 20 00 00 00 A3 82 01 ......... ...... 
 0020: 63 61 82 01 5F 30 82 01 5B A0 03 02 01 05 A1 0E ca.._0..[....... 
 0030: 1B 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D A2 26 ..CONTOSO.COM.& 
 0040: 30 24 A0 03 02 01 00 A1 1D 30 1B 1B 02 6E 6E 1B 0$.......0...nn. 
 0050: 15 73 68 61 73 74 61 2D 68 64 70 32 35 2D 30 30 .hadoop-hdp25-00 
 0060: 2E 6C 6F 63 61 6C A3 82 01 1A 30 82 01 16 A0 03 .local....0..... 
 0070: 02 01 10 A1 03 02 01 01 A2 82 01 08 04 82 01 04 ................ 
 *[…Condensed…]* 
 0240: 03 E3 68 72 C4 D2 8D C2 8A 63 52 1F AE 26 B6 88 ..hr.....cR..&.. 
 0250: C4 . 
```
## <a name="checkpoint-4"></a>チェックポイント 4
最後に、ターゲット パスのファイル プロパティを確認メッセージと共に出力する必要があります。 これは、SQL Server が ST を使用して Hadoop によって認証され、セキュリティで保護されたリソースへのアクセスがセッションに許可されたことを示します。

このポイントに到達した場合、次のことが確認されます。(i) 3 つのアクターが正常に通信できる。(ii) core-site.xml と jaas.conf が正しい。(iii) KDC で資格情報が認識された。
```dos
 [2017-04-25 21:34:35,096] INFO 2235[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1586) - File properties for "/": FileStatus{path=hdfs://10.193.27.232:8020/; isDirectory=true; modification_time=1492028259862; access_time=0; owner=hdfs; group=hdfs; permission=rwxr-xr-x; isSymlink=false} 
 [2017-04-25 21:34:35,098] INFO 2237[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1587) - Successfully accessed the external file system. 
```
## <a name="common-errors"></a>一般的なエラー
ツールが実行され、ターゲット パスのファイル プロパティが*出力されていない*場合 (チェックポイント 4)、途中で例外がスローされています。 例外を確認し、4 ステップのフローで例外が発生したコンテキストを検討します。 次の一般的な問題が発生していないかをこの順に確認します。
| 例外とメッセージ | 原因 | 
| --- | --- |
| org.apache.hadoop.security.AccessControlException<br>簡易認証が有効になっていません。 Available:[TOKEN, KERBEROS] | core-site.xml で hadoop.security.authentication プロパティが "KERBEROS" に設定されていません。|
|javax.security.auth.login.LoginException<br>Client not found in Kerberos database  (6) - CLIENT_NOT_FOUND |    入力された管理者のサービス プリンシパルが、core-site.xml に指定されている領域に存在しません。|
| javax.security.auth.login.LoginException<br> Checksum failed |    管理者のサービス プリンシパルは存在しますが、パスワードが正しくありません。 |
| Native config name: C:\Windows\krb5.ini<br>Loaded from native config | これは例外ではなく、Java の krb5LoginModule でコンピューター上にカスタム クライアント構成が検出されたことを示します。 カスタム クライアント設定が問題の原因である可能性があります。設定を確認してください。 |
| javax.security.auth.login.LoginException<br>java.lang.IllegalArgumentException<br>Illegal principal name admin_user@CONTOSO.COM: org.apache.hadoop.security.authentication.util.KerberosName$NoMatchingRule: No rules applied to admin_user@CONTOSO.COM | Hadoop クラスターごとに適切なルールを指定して、プロパティ "hadoop.security.auth_to_local" を core-site.xml に追加します。 |
| java.net.ConnectException<br>Attempting to access external filesystem at URI: hdfs://10.193.27.230:8020<br>Call From IAAS16981207/10.107.0.245 to 10.193.27.230:8020 failed on connection exception | KDC に対する認証は成功しましたが、Hadoop 名前ノードにアクセスできませんでした。 名前ノードの IP とポートを確認してください。 Hadoop 上のファイアウォールが無効になっていることを確認します。 |
| java.io.FileNotFoundException<br>File does not exist: /test/data.csv |    認証は成功しましたが、指定された場所が存在しません。 パスを確認するか、まずルート "/" でテストしてください。 |
## <a name="debugging-tips"></a>デバッグのヒント
### <a name="mit-kdc"></a>MIT KDC  
KDC に登録されたすべての SPN は、管理者を含めて、KDC ホストまたは構成されている任意の KDC クライアントで **kadmin.local** > (管理者ログイン) > **listprincs** を実行して表示できます。 Hadoop クラスターが適切に Kerberos 対応になっている場合、クラスター内で使用可能な多数のサービス (nn、dn、rm、yarn、spnego など) のそれぞれに、1 つの SPN が存在します。それらに対応する keytab ファイル (パスワード代用) は、既定で **/etc/security/keytabs** にあります。 それらのファイルは KDC の秘密キーを使用して暗号化されます。  

[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html) ツールを使用して、KDC 上でローカルに管理者の資格情報を検証することも検討します。 たとえば、*kinit identity@MYREALM.COM*のように使用します。 パスワードのプロンプトは、ID が存在することを示します。  
KDC ログは既定で **/var/log/krb5kdc.log** にあり、要求を行ったクライアント IP を含め、チケットに対するすべての要求が記録されています。 ツールが実行された SQL Server コンピューターの IP から 2 つの要求が行われています。1 つ目は認証サーバーに対する TGT の要求 (**AS\_REQ**) であり、その後にチケット保証サーバーに ST を要求する **TGS\_REQ** が続きます。
```bash
 [root@MY-KDC log]# tail -2 /var/log/krb5kdc.log 
 May 09 09:48:26 MY-KDC.local krb5kdc[2547](info): **AS_REQ** (3 etypes {17 16 23}) 10.107.0.245: ISSUE: authtime 1494348506, etypes {rep=16 tkt=16 ses=16}, admin_user@CONTOSO.COM for **krbtgt/CONTOSO.COM@CONTOSO.COM** 
 May 09 09:48:29 MY-KDC.local krb5kdc[2547](info): **TGS_REQ** (3 etypes {17 16 23}) 10.107.0.245: ISSUE: authtime 1494348506, etypes {rep=16 tkt=16 ses=16}, admin_user@CONTOSO.COM for **nn/hadoop-hdp25-00.local@CONTOSO.COM** 
```
### <a name="active-directory"></a>Active Directory 
Active Directory では、[コントロール パネル] > [Active Directory ユーザーとコンピューター] > [*MyRealm*] > [*MyOrganizationalUnit*] を参照して SPN を表示できます。 Hadoop クラスターが適切に Kerberos 対応になっている場合、使用可能な多数のサービス (nn、dn、rm、yarn、spnego など) のそれぞれに、1 つの SPN が存在します。

## <a name="see-also"></a>参照
[Active Directory 認証を使用した PolyBase と Cloudera の統合](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/10/17/integrating-polybase-with-cloudera-using-active-directory-authentication)  
[CDH 用に Kerberos を設定するための Cloudera のガイド](https://www.cloudera.com/documentation/enterprise/5-6-x/topics/cm_sg_principal_keytab.html)  
[HDP 用に Kerberos を設定するための Hortonworks のガイド](https://docs.hortonworks.com/HDPDocuments/Ambari-2.2.0.0/bk_Ambari_Security_Guide/content/ch_configuring_amb_hdp_for_kerberos.html)  
[PolyBase のトラブルシューティング](polybase-troubleshooting.md)


