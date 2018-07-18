---
title: フェールオーバー クラスター インスタンス ストレージ NFS - SQL Server on Linux の構成 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: e0432452021919690c4d170f040e183e7de6b635
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061880"
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>NFS - SQL Server on Linux を構成するには、フェールオーバー クラスター インスタンス。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux でのフェールオーバー クラスター インスタンス (FCI) の NFS ストレージを構成する方法について説明します。 

NFS、またはネットワーク ファイル システムでは、Linux の世界がいずれかの Windows ではないのでディスクを共有するための一般的な方法です。 同様に、iSCSI、NFS で構成できます、サーバーまたはなんらかのアプライアンスまたは記憶域ユニット for SQL Server の記憶域の要件を満たしている限りです。

## <a name="important-nfs-server-information"></a>NFS サーバーの重要な情報

NFS (Linux サーバーまたは別のもの) をホストしているソースを使用して/に準拠するバージョン 4.2 以降。 以前のバージョンは、SQL Server on Linux では機能しません。

NFS サーバーで共有するフォルダーを構成する場合は、これらのガイドラインの全般的なオプションに従うことを確認します。
- `rw` フォルダーの内容を確実にからの読み取りおよび書き込みできるに
- `sync` フォルダーへの書き込みを保証することを確認
- 使用しない`no_root_squash`オプションとして、セキュリティ リスクと捉えられます
- フォルダーが完全な権限 (777) が適用されることを確認します。

アクセスするため、セキュリティ標準が適用されていることを確認します。 フォルダーを構成するときに、FCI に参加しているサーバーのみが NFS フォルダーを表示する必要があることを確認します。 NFS の Linux ベースのソリューションに変更された/etc/exports の例は、フォルダーが FCIN1 と FCIN2 に制限以下に示します。

![05 nfsacl][1]

## <a name="instructions"></a>Instructions

1. FCI の構成では、参加するサーバーのいずれかを選択します。 どれもかまいません。 

2. サーバーが NFS サーバー上、mount(s) を表示できることを確認します。

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
   * スーパー ユーザーを完全にスイッチします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    sudo -i
    ```

   * スイッチを mssql ユーザーにします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    su mssql
    ```

   * SQL Server のデータを格納するファイルとログ ファイルを一時ディレクトリを作成します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > フォルダーの名前を指定します。 次の例では、/var/opt/mssql/tmp という名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * SQL Server のデータとログ ファイルを一時ディレクトリにコピーします。 成功した場合は、すべての受信確認は受信しません。
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > は、前の手順からフォルダーの名前です。

   * ファイルがディレクトリであることを確認します。

    ```bash
    ls TempDir
    ```

    \<TempDir > 手順 d からフォルダーの名前を指定します。

   * 既存の SQL Server データ ディレクトリからファイルを削除します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   * ファイルが削除されたことを確認します。 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * ルート ユーザーに切り替えてに exit」と入力します。

   * SQL Server データ フォルダーに、NFS 共有をマウントします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスです 

    \<FolderOnNFSServer >、NFS 共有の名前を指定します。 次の構文の例では、手順 2 から NFS 情報と一致します。

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * スイッチなしでマウントを発行して、マウントが成功したことを確認します。

    ```bash
    mount
    ```

    ![10 mountnoswitches][2]

   * Mssql ユーザーに切り替えます。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    su mssql
    ```

   * 一時ディレクトリ/var/opt/mssql/data からファイルをコピーします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * ファイルがあることを確認します。

    ```bash
    ls /var/opt/mssql/data
    ```

   * キャンセルする場合は mssql できませんを入力します。 
    
   * 終了できないルートを入力します。

   * SQL Server を起動します。 場合、すべてが正しくコピーされ、セキュリティが適用されて正しく、SQL Server 表示されますが開始します。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * セキュリティが正しく設定されているかをテストするデータベースを作成します。 Transact SQL; 経由で行われている例を次に示しますこれは、SSMS を使用して実行できます。
 
    ![CreateTestdatabase][3]

   * SQL Server を停止し、シャット ダウンがあることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * 他の NFS のマウントを作成していない場合、共有のマウントを解除します。 場合はマウント解除できません。

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスです

    \<FolderOnNFSServer >、NFS 共有の名前を指定します

    \<FolderMountedIn > は、前の手順で作成したフォルダーです。 

4. ユーザー データベースやバックアップなどのシステム データベース以外の次の手順に従います。 既定の場所を使用して、専用の場合は、手順 5. に進んでください。

   * スーパー ユーザーを指定するスイッチです。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    sudo -i
    ```

   * SQL Server で使用されるフォルダーを作成します。 

    ```bash
    mkdir <FolderName>
    ```

    \<フォルダー名 > フォルダーの名前を指定します。 フォルダーの完全なパスを指定する必要があります。 適切な場所ではない場合。 次の例では、/var/opt/mssql/userdata という名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * 前の手順で作成したフォルダーで、NFS 共有をマウントします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスです

    \<FolderOnNFSServer >、NFS 共有の名前を指定します

    \<FolderToMountIn > は、前の手順で作成したフォルダーです。 例を次に示します。 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * スイッチなしでマウントを発行して、マウントが成功したことを確認します。
  
   * スーパー ユーザーをされなく exit」と入力します。

   * テストするには、そのフォルダーで、データベースを作成します。 次の例では、sqlcmd を使用して、データベースを作成、コンテキストを切り替える、ファイルは、OS レベルで存在し、一時的な場所を削除し、確認します。 SSMS を使用することができます。

    ![15 createtestdatabase][4]
 
   * 共有のマウントを解除します。 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスです
    
    \<FolderOnNFSServer >、NFS 共有の名前を指定します

    \<FolderMountedIn > は、前の手順で作成したフォルダーです。 例を次に示します。 
 
5. その他のノード上の手順を繰り返します。


## <a name="next-steps"></a>次のステップ

[Linux 上の SQL Server のフェールオーバー クラスター インスタンスを構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
