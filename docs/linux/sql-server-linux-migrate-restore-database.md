---
title: "Windows から Linux に SQL Server データベースの移行 |Microsoft ドキュメント"
description: "このチュートリアルでは、Windows では、SQL Server データベースのバックアップを行うし、SQL Server 2017 を実行している Linux コンピューターに復元する方法を示します。"
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
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Windows からのバックアップと復元を使用して Linux に SQL Server データベースを移行します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server のバックアップと復元機能は、Linux 上の SQL Server 2017 を Windows 上の SQL Server からデータベースを移行することをお勧めします。 このチュートリアルでは、linux のバックアップ データベースを移動して、復元の方法に必要な手順について説明します。

> [!div class="checklist"]
> * SSMS での Windows 上のバックアップ ファイルを作成します。
> * Windows では、Bash シェルをインストールします。
> * Linux、Bash シェルから、バックアップ ファイルを移動します。
> * Transact SQL を使用した Linux 上のバックアップ ファイルを復元します。
> * 移行を検証するクエリを実行します。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、次の前提条件が必要です。

* 次の Windows コンピューター:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions)をインストールします。
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)をインストールします。
  * ターゲット データベースを移行します。

* インストールされている次の Linux マシン:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md)、 [SLES](quickstart-install-connect-suse.md)、または[Ubuntu](quickstart-install-connect-ubuntu.md)) コマンド ライン ツールを使用します。

## <a name="create-a-backup-on-windows"></a>Windows でバックアップを作成します。

Windows 上のデータベースのバックアップ ファイルを作成するいくつかの方法はあります。 次の手順では、SQL Server Management Studio (SSMS) を使用します。

1. 開始**SQL Server Management Studio** Windows コンピューターにします。

1. 接続ダイアログ ボックスで、次のように入力します。 **localhost**です。

1. オブジェクト エクスプ ローラーで、**データベース**です。

1. ターゲット データベースを右クリックし、選択**タスク**、クリックして**をバックアップしています.**.

   ![SSMS を使用して、バックアップ ファイルを作成するには](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. **データベースのバックアップ**ダイアログ ボックスで、いることを確認**バックアップの種類**は**完全**と**バックアップ先**は**ディスク**です。 ファイルの名前と場所に注意してください。 たとえば、という名前のデータベース**YourDB** SQL Server 2016 での既定のバックアップ パスを持つ`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`します。

1. をクリックして**OK**データベースをバックアップします。

> [!NOTE]
> バックアップ ファイルを作成する TRANSACT-SQL クエリを実行することもできます。 次の TRANSACT-SQL コマンドは、データベースに対して、前の手順として同じ操作を実行しますと呼ばれる**YourDB**:。
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Windows では、Bash シェルをインストールします。

データベースを復元するには、Windows コンピューターからターゲットの Linux マシンをバックアップ ファイルを転送する必要があります。 このチュートリアルでは Windows で実行されている、Bash シェル (ターミナル ウィンドウ) から Linux にファイルを移動します。

1. サポートする Windows コンピューターに、Bash シェルのインストール、 **scp** (コピーをセキュリティで保護) と**ssh** (リモート ログイン) コマンド。 2 つの例は次のとおりです。

   * [For Linux の Windows サブシステム](https://msdn.microsoft.com/commandline/wsl/about)(Windows 10)
   * Git Bash シェル ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Windows では、Bash セッションを開きます。

## <a id="scp"></a>Linux のバックアップ ファイルをコピーします。

1. バッシュ セッションには、バックアップ ファイルを含むディレクトリに移動します。 例:

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. 使用して、 **scp**コマンドをファイル ターゲットの Linux マシンを転送します。 次の例転送**YourDB.bak**のホーム ディレクトリに*user1* Linux サーバーの IP アドレスで*192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![scp コマンド](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> ファイル転送の scp を使用に代わる方法があります。 使用する 1 つは[Samba](https://help.ubuntu.com/community/Samba) Windows と Linux の間で SMB ネットワーク共有を構成します。 Ubuntu でチュートリアルは、次を参照してください。 [、ネットワーク共有を介して Samba を作成する方法](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!)です。 確立されると、ネットワーク ファイルとしてアクセスできるように、Windows から共有 **\\ \\machinenameorip\\共有**です。

## <a name="move-the-backup-file-before-restoring"></a>復元する前に、バックアップ ファイルを移動します。

この時点では、バックアップ ファイルが、ユーザーのホーム ディレクトリ内の Linux サーバーにします。 SQL Server にデータベースを復元する前のサブディレクトリに、バックアップを配置する必要があります**/var/opt/mssql**です。

1. 同じ Windows Bash セッションへのリモート接続で、ターゲットの Linux マシン**ssh**です。 次の例は、Linux コンピューターに接続**192.0.2.9**ユーザーとして**user1**です。

   ```bash
   ssh user1@192.0.2.9
   ```

   リモートの Linux サーバーでコマンドを実行するようになりました。

1. スーパー ユーザーのモードを入力します。

   ```bash
   sudo su
   ```

1. 新しいバックアップ ディレクトリを作成します。 -P パラメーターは、ディレクトリが既に存在する場合に、何も行われません。

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. バックアップ ファイルをそのディレクトリに移動します。 ホーム ディレクトリで次の例では、バックアップ ファイルが存在する*user1*です。 バックアップ ファイルの場所とファイル名と一致するコマンドを変更します。

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. スーパー ユーザーのモードを終了します。

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Linux 上のデータベースを復元します。

データベースのバックアップを復元する際、**データベースの復元**TRANSACT-SQL (TQL) コマンド。

> [!NOTE]
> 次の手順を使用して、 **sqlcmd**ツールです。 インストールを行っていないかどうかは SQL Server ツールを参照してください[Linux 上の SQL Server のインストール コマンド ライン ツール](sql-server-linux-setup-tools.md)です。

1. 同じターミナルで起動**sqlcmd**です。 次の例は、ローカルの SQL Server インスタンスに接続、 **SA**ユーザー。 メッセージが表示されたら、パスワードを入力するかを追加して、パスワードを指定、 **-p**パラメーター。

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. `>1`プロンプトで、次を入力します**RESTORE DATABASE**コマンド、各行の (できませんコピーして貼り付けるマルチライン コマンド全体を一度に) 後に ENTER キーを押します。 すべての出現を置換`YourDB`データベースの名前に置き換えます。

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   データベースの復元が正常にメッセージを取得する必要があります。

1. サーバー上のデータベースのすべてを一覧表示して、復元を確認します。 復元されたデータベースの一覧を表示する必要があります。

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. 移行されたデータベースでは、他のクエリを実行します。 次のコマンドにコンテキストの切り替え、 **YourDB**データベースし、そのテーブルの 1 つから行を選択します。

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. 完了したらを使用して**sqlcmd**、型`exit`です。

1. 完了したら、リモートで作業して**ssh**セッションで、「`exit`もう一度です。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Windows 上のデータベースをバックアップし、SQL Server 2017 を実行する Linux サーバーに移動する方法について学習しました。 方法を学習します。
> [!div class="checklist"]
> * SSMS と Transact SQL を使用して、Windows 上のバックアップ ファイルを作成するには
> * Windows では、Bash シェルをインストールします。
> * 使用して**scp** Windows から Linux にバックアップ ファイルを移動するには
> * 使用して**ssh** Linux コンピューターにリモート接続
> * 復元処理の準備をするバックアップ ファイルを再配置します。
> * 使用して**sqlcmd** TRANSACT-SQL コマンドを実行するには
> * データベースのバックアップと復元、 **RESTORE DATABASE**コマンド 

Linux 上 SQL Server の他の移行シナリオを次に、表示します。 

> [!div class="nextstepaction"]
>[Linux 上の SQL Server にデータベースを移行します。](sql-server-linux-migrate-overview.md)
