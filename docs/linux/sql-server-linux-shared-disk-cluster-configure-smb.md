---
title: フェールオーバー クラスター インスタンス ストレージ SMB - SQL Server on Linux の構成 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 5bd5581b2842ec5d11cd27a989aa41ddb2cee1de
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47661940"
---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>フェールオーバー クラスター インスタンス - SMB - SQL Server on Linux の構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux でのフェールオーバー クラスター インスタンス (FCI) の SMB 記憶域を構成する方法について説明します。 
 
Windows 以外の世界で、SMB が多くの場合、として、共通インターネット ファイル システム (CIFS) を共有する呼ばれ、Samba を使用して実装されます。 Windows の世界で、この方法の実行で、SMB 共有にアクセスする: \\servername \sharename します。 Linux ベースの SQL Server インストールの場合、SMB 共有フォルダーとしてマウントする必要があります。

## <a name="important-source-and-server-information"></a>ソース サーバーとサーバーの重要な情報

いくつかのヒントと正常に SMB を使用するための注意事項を次に示します。
- SMB 共有は、Windows、Linux、または SMB 3.0 を使用している限り、またはそれ以上とアプライアンスからでもできます。 Samba と SMB 3.0 の詳細については、次を参照してください。 [SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0) 、Samba の実装が SMB 3.0 に準拠しています。
- 高可用性 SMB 共有があります。
- セキュリティを設定する必要があります、SMB 共有に適切です。 以下の SQLData1 が共有の名前を/etc/samba/smb.conf から例を示します。

![05 smbsource][1]

## <a name="instructions"></a>Instructions

1.  FCI の構成では、参加するサーバーのいずれかを選択します。 どれもかまいません。

2.  Mssql ユーザーに関する情報を取得します。

    ```bash
    sudo id mssql
    ```
    
    Uid や gid、グループに注意してください。 

3. 実行`sudo smbclient -L //NameOrIP/ShareName -U User`します。

    \<NameOrIP > は SMB 共有をホストするサーバーの IP アドレスまたは DNS 名。

    \<共有名 > は SMB 共有の名前を指定します。 

4. システム データベースまたはデータの既定の場所に格納されているものは、次の手順に従っています。 それ以外の場合は、手順 5. に進みます。 

   *    作業しているサーバーで SQL Server が停止していることを確認します。
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    スーパー ユーザーを完全にスイッチします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    sudo -i
    ```

   *    スイッチを mssql ユーザーにします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    su mssql
    ```

   *    SQL Server のデータを格納するファイルとログ ファイルを一時ディレクトリを作成します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    mkdir <TempDir>
    ```

    <TempDir> フォルダーの名前です。 次の例では、/var/opt/mssql/tmp という名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   *    SQL Server のデータとログ ファイルを一時ディレクトリにコピーします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > は、前の手順からフォルダーの名前です。
    
   *    ファイルがディレクトリであることを確認します。

    ```bash
    ls <TempDir>
    ```

    \<TempDir > 手順 d からフォルダーの名前を指定します。
    
   *    既存の SQL Server データ ディレクトリからファイルを削除します。 成功した場合は、すべての受信確認は受信しません。
 
    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    ファイルが削除されたことを確認します。 

    ```bash
    ls /var/opt/mssql/data
    ```
 
   *    ルート ユーザーに切り替えてに exit」と入力します。

   *    SQL Server データ フォルダー内の SMB 共有をマウントします。 成功した場合は、すべての受信確認は受信しません。 この例では、Windows Server ベースの SMB 3.0 共有に接続するための構文を示します。

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<ServerName > は SMB 共有を使用したサーバーの名前です
    
    \<共有名 > は、共有の名前です

    \<ユーザー名 > の共有にアクセスするユーザーの名前を指定します

    \<パスワード > は、ユーザーのパスワード

    \<ドメイン > Active Directory の名前を指定します

    \<mssqlUID > mssql ユーザーの UID は、 
 
    \<mssqlGID > mssql ユーザーの GID は、
 
   *    スイッチなしでマウントを発行して、マウントが成功したことを確認します。

    ```bash
    mount
    ```
 
   *    Mssql ユーザーに切り替えます。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    su mssql
    ```

   *    一時ディレクトリ/var/opt/mssql/data からファイルをコピーします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssql/data
    ```

   *    ファイルがあることを確認します。

    ```bash
    ls /var/opt/mssql/data
    ```

   *    キャンセルする場合は mssql できませんを入力します。 

   *    終了できないルートを入力します。

   *    SQL Server を起動します。 場合、すべてが正しくコピーされ、セキュリティが適用されて正しく、SQL Server 表示されますが開始します。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
 
   *    さらにテストするには、アクセス許可が正常であることを確認するデータベースを作成します。 次のコードの例では、TRANSACT-SQL です。SSMS を使用することができます。

    ![10_testcreatedb][2] 
  
   *    SQL Server を停止し、シャット ダウンがあることを確認します。 追加または他のディスクをテストする場合は、シャットしないで SQL Server をものを追加してテストするまで。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    完了している場合のみ、共有のマウントを解除します。 ない場合は、任意のディスクのテスト/追加を終了した後のマウントを解除します。

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
    ```

    \<IPAddressOrServerName > IP アドレスまたは SMB ホストの名前です

    \<共有名 > は、共有の名前です
    
    \<FolderMountedIn > は SMB がマウントされているフォルダーの名前です

5.  ユーザー データベースやバックアップなどのシステム データベース以外の次の手順に従います。 既定の場所を使用して、専用の場合は、手順 14 に進みます。
    
   *    スーパー ユーザーを指定するスイッチです。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    sudo -i
    ```
    
   *    SQL Server で使用されるフォルダーを作成します。 

    ```bash
    mkdir <FolderName>
    ```

    \<フォルダー名 > フォルダーの名前を指定します。 フォルダーの完全なパスを指定する必要があります。 適切な場所ではない場合。 次の例では、/var/opt/mssql/userdata という名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    SQL Server データ フォルダー内の SMB 共有をマウントします。 成功した場合は、すべての受信確認は受信しません。 この例では、Samba ベースの SMB 3.0 共有に接続するための構文を示します。

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<ServerName > は SMB 共有を使用したサーバーの名前です

    \<共有名 > は、共有の名前です

    \<フォルダー名 > は、最後の手順で作成したフォルダーの名前です  

    \<ユーザー名 > の共有にアクセスするユーザーの名前を指定します

    \<パスワード > は、ユーザーのパスワード

    \<mssqlUID > mssql ユーザーの UID は、

    \<mssqlGID > mssql ユーザーの GID です。
 
   * スイッチなしでマウントを発行して、マウントが成功したことを確認します。
 
   * スーパー ユーザーをされなく exit」と入力します。

   * テストするには、そのフォルダーで、データベースを作成します。 次の例では、sqlcmd を使用して、データベースを作成、コンテキストを切り替える、ファイルは、OS レベルで存在し、一時的な場所を削除し、確認します。 SSMS を使用することができます。
 
   * 共有のマウントを解除します。 

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
    ```
    
    \<IPAddressOrServerName > IP アドレスまたは SMB ホストの名前です
 
    \<共有名 > は、共有の名前です
 
    \<FolderMountedIn > は SMB がマウントされているフォルダーの名前です。
 
6.  その他のノード上の手順を繰り返します。

FCI を構成する準備が整いました。

## <a name="next-steps"></a>次の手順

[Linux 上の SQL Server のフェールオーバー クラスター インスタンスを構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 
