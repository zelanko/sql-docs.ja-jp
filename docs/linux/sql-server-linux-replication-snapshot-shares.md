---
title: Linux 上のスナップショット フォルダーの共有 SQL Server レプリケーションの構成 |Microsoft Docs
description: この記事では、Linux でのスナップショット フォルダーの共有 SQL Server レプリケーションを構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 9/24/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e8da23d77719fd15b12c9f305491827c4a92954b
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715085"
---
# <a name="configure-replication-snapshot-folder-with-shares"></a>共有スナップショット フォルダーのレプリケーションを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

スナップショット フォルダーが共有; として指定したディレクトリ読み取りし、書き込みをこのフォルダーにエージェントにアクセスするための十分なアクセス許可が必要です。

![レプリケーションのダイアグラム][1]

### <a name="replication-snapshot-folder-share-explained"></a>レプリケーション スナップショット フォルダーの共有の説明

前の例には、SQL Server がレプリケーションで samba 共有を使用する方法を見てみましょう。 このしくみの基本的な例を次に示します。

1. Samba 共有が構成されているファイルに書き込まれる`/local/path1`レプリケーションによって、サブスクライバーでパブリッシャー上のエージェントを表示できます
2. すべてのインスタンスが確認されるようにパブリッシャー側でディストリビューション サーバーをセットアップするときに、共有のパスを使用する SQL Server が構成されて、 `//share/path`
3. SQL Server からローカル パスの検索、`//share/path`ファイルを検索する場所を指定するには
4. ローカル パスは、samba 共有をバックアップする SQL Server の読み取り/書き込み


## <a name="configure-a-samba-share-for-the-snapshot-folder"></a>スナップショット フォルダーの samba 共有を構成します。 

レプリケーション エージェントには、他のコンピューターでスナップショット フォルダーにアクセスするホストをレプリケーションの間で共有ディレクトリが必要です。 たとえば、トランザクション プル レプリケーションでは、記事を取得するためにディストリビューターへのアクセスを必要とすると、サブスクライバーでディストリビューション エージェントが存在します。 このセクションでは、レプリケーションの 2 つのホストで samba 共有を構成する方法の例をしましょう。


## <a name="steps"></a>手順

例としては、Samba を使用してホスト 2 (サブスクライバー) を共有するホスト 1 (ディストリビューター) で、スナップショット フォルダーを構成します。 

### <a name="install-and-start-samba-on-both-machines"></a>インストールして Samba を両方のマシンで開始 

Ubuntu の場合。

```bash
sudo apt-get -y install samba
sudo service smbd restart
```

On RHEL:

```bash
sudo yum install samba
sudo service smb start
sudo service smb status
```

### <a name="on-host-1-distributor-set-up-the-samba-share"></a>ホスト 1 (ディストリビューター) のセットアップ、Samba 共有します。 

1. セットアップのユーザーと samba のパスワード:

  ```bash
  sudo smbpasswd -a mssql 
  ```

1. 編集、`/etc/samba/smb.conf`を次のエントリを含め、入力、 *share_name*と*パス*フィールド
 ```bash
  <[share_name]>
  path = </local/path/on/host/1>
  writable = yes
  create mask = 770
  directory mask 
  valid users = mssql 
  ```

  **例**

  ```bash
  [mssql_data]    <- Name of the shared directory
  path = /var/opt/mssql/repldata <- location of directory we wish to share
  writable = yes  <- determines if the share is writable from other hosts
  create mask = 770  <- Linux permissions for files created 
  directory mask = 770 <- Linux permissions for directories created
  valid users = mssql   <- list of users who can login to this share
  ```

### <a name="on-host-2-subscriber--mount-the-samba-share"></a>ホスト 2 (サブスクライバー) に、Samba 共有をマウントします

正しいパスを指定してコマンドを編集し、machine2 で、次のコマンドを実行します。

  ```bash
  sudo mount //<name_of_host_1>/<share_name> </local/path/on/host/2> -o user=mssql,uid=mssql,gid=mssql
  ```

  **例**

  ```bash
  mount //host1/mssql_data /var/opt/mssql/repldata_shared -o user=mssql,uid=mssql,gid=mssql

  user=mssql <- sets the login name for samba
  uid=mssql   <- makes the mssql user as the owner of the mounted directory
  gid=mssql   <- sets the mssql group as the owner of the mounted directory
  ```

### <a name="on-both-hosts--configure-sql-server-on-linux-instances-to-use-snapshot-share"></a>両方のホストを構成する SQL server でスナップショット共有を使用する Linux インスタンス

次のセクションに追加`mssql.conf`両方のコンピューターにします。 任意の場所を使用して、//共有/パスの samba 共有します。 この例では、ことになります `//host1/mssql_data`

  ```bash
  [uncmapping]
  //share/path = /local/path/on/hosts/
  ```

  **例**

  Host1:

  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/1
  ```

  Host2:
  
  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/2
  ```

### <a name="configuring-publisher-with-shared-paths"></a>共有パスでパブリッシャーを構成します。

* レプリケーションを設定する場合は、共有パス (例を使用してください。 `//host1/mssql_data`
* マップ`//host1/mssql_data`ローカル ディレクトリに追加のマッピングを`mssql.conf`します。

## <a name="next-steps"></a>次の手順

[Linux 上の概念: SQL Server レプリケーション](sql-server-linux-replication.md)

[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。

[1]: ./media/sql-server-linux-replication-snapshot-shares/image1.png
