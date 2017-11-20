---
title: "フェールオーバー クラスター インスタンスの記憶域構成 SMB - SQL Server on Linux |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: c32c0593df6b40cc76ecafaabc0571090f2907fa
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>フェールオーバー クラスター インスタンス: SMB - Linux に SQL Server を構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

この記事では、Linux 上のフェールオーバー クラスター インスタンス (FCI) の SMB 記憶域を構成する方法について説明します。 
 
世界では、Windows 以外、SMB は、多くの場合、および参照されるとして、Common Internet File System (CIFS) を共有する Samba を介して実装します。 世界では、Windows、SMB 共有にアクセスするときはこのように: \\servername \sharename です。 Linux ベースの SQL Server インストールの場合、フォルダーとして SMB 共有をマウントする必要があります。

## <a name="important-source-and-server-information"></a>ソース サーバーとサーバーの重要な情報

いくつかのヒントと正常に SMB を使用するための注意事項を次に示します。
- SMB 共有には、Windows では、Linux、または SMB 3.0 を使用している間、またはそれ以上としてアプライアンスからでもを指定できます。 Samba と SMB 3.0 の詳細については、次を参照してください。 [SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0) Samba 実装が SMB 3.0 に準拠しているかどうか。
- SMB 共有は、高可用性にする必要があります。
- セキュリティを設定する必要があります、SMB 共有に対する適切です。 次に、例から/etc/samba/smb.conf、SQLData1 は共有の名前を指定します。

![05 smbsource][1]

## <a name="instructions"></a>Instructions

1.  FCI の構成では、参加するサーバーのいずれかを選択します。 どちらかは関係ありません。

2.  Mssql ユーザーに関する情報を取得します。

    ```bash
    sudo id mssql
    ```
    
    Uid や gid、そしてグループに注意してください。 

3. 実行`sudo smbclient -L //NameOrIP/ShareName -U User`です。

    \<NameOrIP > は、DNS 名または SMB 共有をホストしているサーバーの IP アドレス。

    \<共有名 > は SMB 共有の名前を指定します。 

4. システムのデータベースまたはデータの既定の場所に格納されているものは、次の手順に従っています。 それ以外の場合、手順 5 に進みます。 

   *    作業しているサーバーで SQL Server が停止していることを確認します。
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    スーパー ユーザーを完全にスイッチです。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    sudo -i
    ```

   *    Mssql ユーザーであることに切り替えます。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    su mssql
    ```

   *    SQL Server のデータを格納するファイルとログ ファイルを一時ディレクトリを作成します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    mkdir <TempDir>
    ```

    <TempDir>フォルダーの名前です。 次の例では、/var/opt/mssql/tmp をという名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   *    SQL Server データとログ ファイルを一時ディレクトリにコピーします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > 前の手順で、フォルダーの名前を指定します。
    
   *    ファイルがディレクトリであることを確認します。

    ```bash
    ls <TempDir>
    ```

    \<TempDir > 手順 d からフォルダーの名前を指定します。
    
   *    既存の SQL Server データ ディレクトリからファイルを削除します。 ユーザーは受け取りません受信正常終了した場合。
 
    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    ファイルが削除されたことを確認します。 

    ```bash
    ls /var/opt/mssql/data
    ```
 
   *    Root ユーザーに戻る exit」と入力します。

   *    SQL Server データ フォルダーに SMB 共有をマウントします。 ユーザーは受け取りません受信正常終了した場合。 この例では、Windows Server ベースの SMB 3.0 共有に接続するための構文を使用します。

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<サーバー名 > は SMB 共有を使用してサーバーの名前を指定します。
    
    \<共有名 > 共有の名前を指定します

    \<ユーザー名 > の共有にアクセスするユーザーの名前を指定します

    \<パスワード > は、ユーザーのパスワード

    \<ドメイン > Active Directory の名前を指定します

    \<mssqlUID > は、mssql ユーザーの UID 
 
    \<mssqlGID > mssql ユーザーのグループ ID は、
 
   *    スイッチなしでマウントを発行することで、マウントが成功したことを確認します。

    ```bash
    mount
    ```
 
   *    Mssql ユーザーに切り替えます。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    su mssql
    ```

   *    一時ディレクトリ/var/opt/mssql/data からファイルをコピーします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssql/data
    ```

   *    ファイルがあることを確認します。

    ```bash
    ls /var/opt/mssql/data
    ```

   *    Exit mssql 設定されませんを入力します。 

   *    終了できないルートを入力してください。

   *    SQL Server を起動します。 すべてが正しくコピーされた、セキュリティが適用されて正しく、SQL Server が表示されますを起動する場合は。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
 
   *    さらにテストするには、アクセス許可が正常であることを確認するデータベースを作成します。 次の例です。 TRANSACT-SQL を使用します。SSMS を使用することができます。

    ![10_testcreatedb][2] 
  
   *    SQL Server を停止し、シャット ダウンがあることを確認します。 追加するか、他のディスクをテストする場合はシャット ダウンできません SQL Server が追加され、テストされるまで。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    終了した場合にのみ、共有のマウントを解除します。 それ以外の場合は、テスト/、追加のディスクの追加を完了した後にマウント解除。

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
    ```

    \<IPAddressOrServerName > は、IP アドレスまたは SMB ホストの名前

    \<共有名 > 共有の名前を指定します
    
    \<FolderMountedIn > SMB がマウントされているフォルダーの名前を指定します

5.  ユーザー データベースや、バックアップなどのシステム データベース以外のものを以下の手順を実行します。 既定の場所を使用して、だけの場合は、手順 14 をスキップします。
    
   *    スーパー ユーザーにするスイッチです。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    sudo -i
    ```
    
   *    SQL Server で使用されるフォルダーを作成します。 

    ```bash
    mkdir <FolderName>
    ```

    \<フォルダー名 > フォルダーの名前を指定します。 フォルダーの完全なパスを指定する必要は、適切な場所ではない場合。 次の例では、/var/opt/mssql/userdata をという名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    SQL Server データ フォルダーに SMB 共有をマウントします。 ユーザーは受け取りません受信正常終了した場合。 この例では、Samba ベースの SMB 3.0 共有に接続するための構文を使用します。

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<サーバー名 > は SMB 共有を使用してサーバーの名前を指定します。

    \<共有名 > 共有の名前を指定します

    \<FolderName > の最後の手順で作成したフォルダーの名前を指定します。  

    \<ユーザー名 > の共有にアクセスするユーザーの名前を指定します

    \<パスワード > は、ユーザーのパスワード

    \<mssqlUID > は、mssql ユーザーの UID

    \<mssqlGID > mssql ユーザーの GID がします。
 
   * スイッチなしでマウントを発行することで、マウントが成功したことを確認します。
 
   * スーパー ユーザーを使用できなくする exit」と入力します。

   * テストするには、そのフォルダーにデータベースを作成します。 次に示す例では、sqlcmd を使用してデータベースを作成、コンテキストを切り替える、ファイルが、OS レベルが存在し、一時的な場所を削除します。 SSMS を使用することができます。
 
   * 共有のマウントを解除します。 

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
    ```
    
    \<IPAddressOrServerName > は、IP アドレスまたは SMB ホストの名前
 
    \<共有名 > 共有の名前を指定します
 
    \<FolderMountedIn > SMB がマウントされているフォルダーの名前を指定します。
 
6.  その他のノードで手順を繰り返します。

FCI を構成する準備が整いました。

## <a name="next-steps"></a>次の手順

[フェールオーバー クラスター インスタンス: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 

