---
title: "フェールオーバー クラスター インスタンスの記憶域構成 NFS - SQL Server on Linux |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 368fce4b3c9595f89ea14ca310049a52cf180a28
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>フェールオーバー クラスター インスタンス: NFS - Linux に SQL Server を構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上のフェールオーバー クラスター インスタンス (FCI) の NFS の記憶域を構成する方法について説明します。 

NFS、またはネットワーク ファイル システムは、Linux の世界がない、Windows のいずれかでディスクを共有するための一般的な方法です。 ISCSI と同様に、NFS で構成できます、サーバーまたは何らかのアプライアンスや記憶域ユニットの SQL Server の記憶域の要件を満たしている限り、します。

## <a name="important-nfs-server-information"></a>NFS サーバーの重要な情報

NFS (Linux サーバーまたは別のもの) をホストしているソース必要がありますを使用して/に準拠する 4.2 以降のバージョン。 以前のバージョンは、SQL Server on Linux では機能しません。

NFS サーバーで共有するフォルダーを構成するときに、これらのガイドラインの全般的なオプションに従っていることを確認してください。
- `rw` 確認するフォルダーから読み取られたしてに書き込まれます
- `sync` フォルダーへの書き込みを保証されることを確認するには
- 使用しないでください`no_root_squash`オプションとしてと見なされます、セキュリティ上のリスク
- フォルダーが適用されるすべての権利 (777) を確認してください。

アクセスするため、セキュリティの基準が適用されていることを確認します。 フォルダーを構成することを確認して、FCI に参加しているサーバーのみに NFS フォルダーが表示されます。 NFS の Linux ベースのソリューションに変更された/etc/exports の例は、フォルダーが FCIN1 と FCIN2 に制限されている次に示します。

![05 nfsacl][1]

## <a name="instructions"></a>Instructions

1. FCI の構成では、参加するサーバーのいずれかを選択します。 どちらかは関係ありません。 

2. サーバーが、NFS サーバー上、mount(s) を表示できることを確認します。

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスです。

3. システム データベースまたはデータの既定の場所に格納されているものは、次の手順に従います。 それ以外の場合、手順 4. に進みます。
 
   * 作業しているサーバーで SQL Server が停止していることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * スーパー ユーザーを完全にスイッチです。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    sudo -i
    ```

   * Mssql ユーザーであることに切り替えます。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    su mssql
    ```

   * SQL Server のデータを格納するファイルとログ ファイルを一時ディレクトリを作成します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > フォルダーの名前を指定します。 次の例では、/var/opt/mssql/tmp をという名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * SQL Server データとログ ファイルを一時ディレクトリにコピーします。 ユーザーは受け取りません受信正常終了した場合。
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > 前の手順で、フォルダーの名前を指定します。

   * ファイルがディレクトリであることを確認します。

    ```bash
    ls TempDir
    ```

    \<TempDir > 手順 d からフォルダーの名前を指定します。

   * 既存の SQL Server データ ディレクトリからファイルを削除します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   * ファイルが削除されたことを確認します。 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Root ユーザーに戻る exit」と入力します。

   * SQL Server データ フォルダーに、NFS 共有をマウントします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスは、 

    \<FolderOnNFSServer > NFS 共有の名前を指定します。 次の構文の例では、手順 2 から NFS 情報と一致します。

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * スイッチなしでマウントを発行することで、マウントが成功したことを確認します。

    ```bash
    mount
    ```

    ![10 mountnoswitches][2]

   * Mssql ユーザーに切り替えます。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    su mssql
    ```

   * 一時ディレクトリ/var/opt/mssql/data からファイルをコピーします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * ファイルがあることを確認します。

    ```bash
    ls /var/opt/mssql/data
    ```

   * Exit mssql 設定されませんを入力します。 
    
   * 終了できないルートを入力してください。

   * SQL Server を起動します。 すべてが正しくコピーされた、セキュリティが適用されて正しく、SQL Server が表示されますを起動する場合は。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * セキュリティが正しくセットアップされているかをテストするデータベースを作成します。 次の例は TRANSACT-SQL; 経由で実行されていることを示していますSSMS を使用して実行できます。
 
    ![CreateTestdatabase][3]

   * SQL Server を停止し、シャット ダウンがあることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * その他の NFS マウントを作成していない場合、共有のマウントを解除します。 場合がアンマウントされません。

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスは、

    \<FolderOnNFSServer > NFS 共有の名前を指定します。

    \<FolderMountedIn > は、前の手順で作成したフォルダーです。 

4. ユーザー データベースや、バックアップなどのシステム データベース以外のものを以下の手順を実行します。 既定の場所を使用して、だけの場合は、手順 5 に進みます。

   * スーパー ユーザーにするスイッチです。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    sudo -i
    ```

   * SQL Server で使用されるフォルダーを作成します。 

    ```bash
    mkdir <FolderName>
    ```

    \<フォルダー名 > フォルダーの名前を指定します。 フォルダーの完全なパスを指定する必要があります、適切な場所ではない場合。 次の例では、/var/opt/mssql/userdata をという名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * 前の手順で作成したフォルダーに、NFS 共有をマウントします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスは、

    \<FolderOnNFSServer > NFS 共有の名前を指定します。

    \<FolderToMountIn > は、前の手順で作成したフォルダーです。 例を次に示します。 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * スイッチなしでマウントを発行することで、マウントが成功したことを確認します。
  
   * スーパー ユーザーを使用できなくする exit」と入力します。

   * テストするには、そのフォルダーにデータベースを作成します。 次の例では、sqlcmd を使用して、データベースを作成、コンテキストを切り替える、ファイルが、OS レベルが存在し、一時的な場所が削除されます。 SSMS を使用することができます。

    ![15 createtestdatabase][4]
 
   * 共有のマウントを解除します。 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスは、
    
    \<FolderOnNFSServer > NFS 共有の名前を指定します。

    \<FolderMountedIn > は、前の手順で作成したフォルダーです。 例を次に示します。 
 
5. その他のノードで手順を繰り返します。


## <a name="next-steps"></a>次の手順

[フェールオーバー クラスター インスタンス: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
