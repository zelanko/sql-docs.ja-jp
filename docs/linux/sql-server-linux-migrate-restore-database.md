---
title: "Windows から Linux への SQL Server データベースの移行 |Microsoft ドキュメント"
description: "このチュートリアルでは、Windows上のSQL Serverデータベースのバックアップし、Linuxコンピューターにて実行しているSQL Server 2017に復元する方法を示します。"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/16/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.workload: On Demand
ms.openlocfilehash: 6d54a849630bece0fba6456a516cbd68aecf2eb5
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>WindowsからのバックアップとLinuxでの復元によりSQL Serverデータベースを移行します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Windows上のSQL ServerからLinux上のSQL Server 2017にデータベースを移行するには、SQL Serverのバックアップと復元機能をお勧めします。このチュートリアルでは、Linux にデータベースのバックアップを移動して、復元をするにあたっての必要な手順について説明します。

> [!div class="checklist"]
> * Windows上のSSMSにてバックアップ ファイルを作成します。
> * Windowsに、Bashシェルをインストールします。
> * Bashシェルにより、WindowsからLinuxにバックアップファイルを移動します。
> * Transact SQLを使用してLinux上のバックアップファイルを復元します。
> * 移行を検証するクエリを実行します。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、次の前提条件が必要です。

* 次の Windows コンピューター:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions)をインストールします。
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)をインストールします。
  * ターゲット データベースを移行します。

* インストールされている次の Linux マシン:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md)、 [SLES](quickstart-install-connect-suse.md)、または[Ubuntu](quickstart-install-connect-ubuntu.md)) コマンド ライン ツールを使用します。

## <a name="create-a-backup-on-windows"></a>Windowsでバックアップを作成します。

Windows上のデータベースのバックアップファイルを作成するには、いくつかの方法があります。 次の手順では、SQL Server Management Studio (SSMS) を使用します。

1. Windows コンピューターにて**SQL Server Management Studio**を起動します。

1. 接続ダイアログ ボックスで、 **localhost**を入力します。

1. オブジェクト エクスプローラーで、**データベース**を展開します。

1. バックアップファイルを作成する対象のデータベースを右クリックし、**タスク**を選択し、**バックアップ**をクリックします。

   ![SSMS を使用して、バックアップ ファイルを作成するには](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. **データベースのバックアップ**ダイアログ ボックスで、**バックアップの種類**は**完全**、**バックアップ先**は**ディスク**であることを確認してください。ファイル名と場所に注意してください。 たとえば、SQL Server 2016での既定のバックアップ パスは**YourDB**という名前のデータベースの場合`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`となります。

1. **OK**をクリックしてデータベースをバックアップします。

> [!NOTE]
> TRANSACT-SQLクエリを実行によりバックアップ ファイルを作成することもできます。 次のTRANSACT-SQLコマンドは、データベースに対して、前の手順と同じ操作を**YourDB**に対して実行します。
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>WindowsにBashシェルをインストールします。

データベースを復元するには、WindowsコンピューターからターゲットとなるLinuxマシンにバックアップ ファイルを転送する必要があります。 このチュートリアルではWindowsで実行されているBashシェル(ターミナル ウィンドウ)からLinuxにファイルを移動します。

1. サポートするWindows コンピューターに、**scp** (セキュリティで保護されたコピー) と**ssh** (リモート ログイン) コマンドが使えるBashシェルをインストールします。2つの例は次のとおりです。

   * [For Linux の Windows サブシステム](https://msdn.microsoft.com/commandline/wsl/about)(Windows 10)
   * Git Bash シェル ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Windowsにて、Bashセッションを開きます。

## <a id="scp"></a>Linuxにバックアップ ファイルをコピーします。

1. Bashセッションにて、バックアップ ファイルを含むディレクトリに移動します。 例:

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1.  **scp**コマンドを使用して、ファイルをターゲットとなるLinuxマシンに転送します。 次の例ではIP アドレスで*192.0.2.9*のLinuxサーバーの*user1*のホーム ディレクトリに**YourDB.bak**を転送します。 :

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![scp コマンド](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> ファイル転送にはscpを使用する以外の方法があります。1つは[Samba](https://help.ubuntu.com/community/Samba)、WindowsとLinuxの間でSMBネットワーク共有を構成します。 Ubuntuでのチュートリアルは、次を参照してください。 [ネットワーク共有を介して Samba を作成する方法](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!)確立されると、**\\ \\machinenameorip\\共有**の様な形でWindows から共有されたネットワークファイルとしてアクセスできるようになります。

## <a name="move-the-backup-file-before-restoring"></a>復元する前にバックアップ ファイルを移動します。

この時点では、バックアップ ファイルが、Linux サーバーのユーザーのホーム ディレクトリ内のあります。SQL Serverにデータベースを復元する前のサブディレクトリ**/var/opt/mssql**に、バックアップを配置する必要があります。

1. 同じWindows Bashセッションから**ssh**で、ターゲットとなるLinuxマシンにリモート接続します。 次の例は、**192.0.2.9**のLinux コンピューターに、ユーザー**user1**として接続します。

   ```bash
   ssh user1@192.0.2.9
   ```

   リモートのLinux サーバーでコマンドを実行できるようになりました。

1. スーパー ユーザーに切り替えます。

   ```bash
   sudo su
   ```

1. 新しいバックアップ ディレクトリを作成します。 -Pパラメーターは、ディレクトリが既に存在する場合は、何も行われません。

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. バックアップ ファイルをそのディレクトリに移動します。次の例ではバックアップ ファイルが存在するのは*user1*のホーム ディレクトリです。 バックアップ ファイルの場所とファイル名と一致する様にコマンドを変更します。

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. スーパー ユーザーを終了します。

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Linux上にデータベースを復元します。

データベースのバックアップを復元する際、TRANSACT-SQL (TQL)の**RESTORE DATABASE**コマンドを使います。

> [!NOTE]
> 次の手順では**sqlcmd**ツールを使用します。 インストールを行っていない場合はSQL Serverツールを参照してください[Linux 上の SQL Server のインストール コマンド ライン ツール](sql-server-linux-setup-tools.md)。

1. 同じターミナルで**sqlcmd**を起動します。 次の例は、**SA**ユーザーでローカルのSQL Serverインスタンスに接続します。メッセージが表示されたら、パスワードを入力します。もしくは**-p**パラメーターを追加して、パスワードを指定します。

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. `>1`プロンプトで、次の**RESTORE DATABASE**コマンドを入力します。各行の (全体を一度にコピーして貼り付け出来ません) 後にENTERキーを押します。すべての`YourDB`をあなたのデータベースの名前に置き換えます。

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   データベースの復元が正常であるメッセージを確認する必要があります。

1. サーバー上のデータベースのすべてを一覧表示して、復元されたことを確認します。復元されたデータベースの一覧を表示させる必要があります。

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. 移行されたデータベースで、他のクエリを実行します。次のコマンドでは**YourDB**にデータベースコンテキストを切り替え、そのテーブルの1つから行を選択します。

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. 完了したら`exit`で**sqlcmd**を終了します。

1. 完了したらもう一度`exit`**ssh**でリモートセッションを終了します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Windows上のデータベースをバックアップし、Linuxコンピューターにて実行しているSQL Server 2017に移動する方法について学習しました。以下の方法を学習しました。
> [!div class="checklist"]
> * SSMSとTransact SQLを使用して、Windows上のバックアップ ファイルを作成する
> * Windows上に、Bash シェルをインストールする
> * **scp**を使用してWindowsからLinuxにバックアップ ファイルを移動する
> * **ssh**を使用してLinuxコンピューターにリモート接続する
> * 復元処理の準備としてバックアップ ファイルを再配置する
> * **sqlcmd**を使用してTRANSACT-SQLコマンドを実行する
> * **RESTORE DATABASE**コマンドでデータベースのバックアップを復元する  

> * 移行を検証するクエリを実行します。

次にLinux上のSQL Serverの他の移行シナリオを表示します。 

> [!div class="nextstepaction"]
>[Linux 上の SQL Server にデータベースを移行します。](sql-server-linux-migrate-overview.md)
