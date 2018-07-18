---
title: Windows から Linux への SQL Server データベースの移行 |Microsoft Docs
description: このチュートリアルでは、Windows上のSQL Serverデータベースのバックアップし、Linuxコンピューターにて実行しているSQL Server 2017に復元する方法を示します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/16/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.openlocfilehash: 559ae24a819cfff1172d1829ef3ca5e679a40122
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020190"
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>バックアップと復元を使用して Windows から Linux へ SQL Server データベースを移行する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Windows 上の SQL Server から Linux 上の SQL Server 2017 にデータベースを移行させるには、SQL Serverのバックアップと復元機能を使用することをお勧めします。 このチュートリアルでは、バックアップと復元の方法を使用して、データベースを Linux に移動させるのに必要な手順について説明します。

> [!div class="checklist"]
> * SSMS を使用して Windows にバックアップ ファイルを作成します。
> * Windows上に、Bash シェルをインストールする
> * Bash シェルから Linux にバックアップ ファイルを移動する
> * Transact SQL を使用して Linux 上のバックアップ ファイルを復元します。
> * クエリを実行して移行を検証します。

SQL Server Always On 可用性グループ Windows から Linux に SQL Server データベースを移行するを作成することもできます。 参照してください[sql-server-linux-availability-group-cross-platform](sql-server-linux-availability-group-cross-platform.md)します。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、次の前提条件が必要です。

* 次の Windows マシンの場合:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions)をインストールします。
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)をインストールします。
  * ターゲット データベースを移行します。

* インストールされている次の Linux マシンの場合:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md)、 [SLES](quickstart-install-connect-suse.md)、または[Ubuntu](quickstart-install-connect-ubuntu.md)) コマンド ライン ツールを使用します。

## <a name="create-a-backup-on-windows"></a>Windows でバックアップを作成する

Windows 上のデータベースのバックアップ ファイルを作成するには、いくつかの方法があります。 次の手順では、SQL Server Management Studio (SSMS) を使用します。

1. Windows マシンで **SQL Server Management Studio** を起動します。

1. 接続ダイアログで、「**localhost**」と入力します。

1. オブジェクト エクスプローラーで、**データベース** を展開します。

1. ターゲット データベースを右クリックし、**タスク** を選択し、**バックアップ** をクリックします。

   ![SSMS を使用して、バックアップ ファイルを作成するには](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. **データベースのバックアップ**ダイアログで、**バックアップの種類** は **完全**、**バックアップ先** は **ディスク** であることを確認します。 ファイル名と場所に注意します。 たとえば、SQL Server 2016 で **YourDB** という名前のデータベースの場合、既定のバックアップ パスは次のようになります。 `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`

1. **OK** をクリックしてデータベースをバックアップします。

> [!NOTE]
> TRANSACT-SQL クエリを実行してバックアップ ファイルを作成することもできます。 次の TRANSACT-SQL コマンドは、前の手順と同じ操作を **YourDB** と呼ばれるデータベースに対して実行します。
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Windows上に、Bash シェルをインストールする

データベースを復元するには、Windows マシンからターゲットとなる Linux マシンにバックアップ ファイルを転送する必要があります。 このチュートリアルでは、Windows で実行されている Bash シェル (ターミナル ウィンドウ) から Linux にファイルを移動させます。

1. **scp** (セキュリティで保護されたコピー) と **ssh** (リモート ログイン) コマンドをサポートする Windows マシンに Bash シェルをインストールします。 2 つの例は次のとおりです。

   * [Windows Subsystem for Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * Git Bash シェル ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Windows で、Bash セッションを開きます。

## <a id="scp"></a> Linuxにバックアップ ファイルをコピーします。

1. Bash セッションで、バックアップ ファイルを含むディレクトリに移動します。 以下に例を示します。

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. 使用して、 **scp**コマンド ターゲットの Linux マシンにファイルを転送します。 次の例の転送**YourDB.bak**のホーム ディレクトリに*user1*で IP アドレスが Linux サーバーで*192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![scp コマンド](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> ファイル転送に scp を使用する代替案がないです。 使用する 1 つは[Samba](https://help.ubuntu.com/community/Samba) Windows と Linux での SMB ネットワーク共有を構成します。 Ubuntu でチュートリアルは、次を参照してください。[をネットワーク共有を使用して Samba を作成する方法](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!)します。 確立されると、ネットワーク ファイルとしてアクセスできるよう、Windows から共有 **\\ \\machinenameorip\\共有**。

## <a name="move-the-backup-file-before-restoring"></a>復元する前にバックアップ ファイルを移動する

この時点で、バックアップ ファイルは、ユーザーのホーム ディレクトリで Linux サーバーには。 SQL Server にデータベースを復元する前のサブディレクトリに、バックアップを配置する必要があります **/var/opt/mssql**します。

1. 同じ Windows Bash セッションで、**ssh** を使用してターゲットとなる Linux マシンにリモート接続します。 次の例では、**192.0.2.9** の Linux マシンに、ユーザー **user1** として接続します。

   ```bash
   ssh user1@192.0.2.9
   ```

   リモートのLinux サーバーでコマンドを実行できるようになりました。

1. スーパー ユーザー モードに切り替えます。

   ```bash
   sudo su
   ```

1. 新しいバックアップ ディレクトリを作成します。 Pパラメーターは、ディレクトリが既に存在する場合は、何も行いません。

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. バックアップ ファイルをそのディレクトリに移動します。 次の例では、バックアップ ファイルは *user1* のホーム ディレクトリにあります。 バックアップ ファイルの場所とファイル名と一致するようにコマンドを変更してください。

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. スーパー ユーザーのモードを終了します。

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Linux上にデータベースを復元する

データベースのバックアップを復元するには、使用することができます、 **RESTORE DATABASE** TRANSACT-SQL (TQL) コマンド。

> [!NOTE]
> 次の手順では **sqlcmd** ツールを使用します。 インストールしていないかどうかは SQL Server ツールを参照してください[Linux 上の SQL Server のインストール コマンド ライン ツール](sql-server-linux-setup-tools.md)します。

1. 同じターミナルで **sqlcmd** を起動します。 次の例は、**SA** ユーザーでローカルのSQL Serverインスタンスに接続します。 メッセージが表示されたら、パスワードを入力します。もしくは **-p** パラメーターを追加して、パスワードを指定します。

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. `>1` プロンプトで、次の **RESTORE DATABASE** コマンドを入力します。各行 (複数行のコマンド全体を一度にコピーして貼り付けることはできません) の後にENTERキーを押します。
 `YourDB` をすべてデータベースの名前に置き換えます。

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   データベースの復元が正常にメッセージを取得する必要があります。

1. 復元を確認するには、サーバー上のデータベースのすべてを一覧表示します。 復元されたデータベースの一覧を表示する必要があります。

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. 移行されたデータベースで、他のクエリを実行します。 次のコマンドでは **YourDB** にデータベースコンテキストを切り替え、そのテーブルの1つから行を選択します。

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. 完了したらを使用して**sqlcmd**、型`exit`します。

1. 完了したら、リモートで作業して**ssh**セッションで、「`exit`もう一度です。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、Windows 上のデータベースをバックアップし、SQL Server 2017 を実行している Linux サーバーに移動する方法について説明しました。 学習したします。
> [!div class="checklist"]
> * SSMSとTransact SQLを使用して、Windows上のバックアップ ファイルを作成する
> * Windows上に、Bash シェルをインストールする
> * **scp** を使用してWindowsからLinuxにバックアップ ファイルを移動する
> * **ssh** を使用してLinuxコンピューターにリモート接続する
> * 復元処理の準備としてバックアップ ファイルを再配置する
> * **sqlcmd** を使用してTRANSACT-SQLコマンドを実行する
> * **RESTORE DATABASE** コマンドでデータベースのバックアップを復元する 
> * クエリを実行して移行を検証します。

次に、他の移行のシナリオについて調べる for SQL Server on Linux。 

> [!div class="nextstepaction"]
>[データベースを SQL Server on Linux に移行します。](sql-server-linux-migrate-overview.md)
