---
title: "Windows から Linux に SQL Server データベースの移行 |Microsoft ドキュメント"
description: "このトピックでは、Windows では、SQL Server データベースのバックアップを行うし、SQL Server 2017 RC2 を実行している Linux コンピューターに復元する方法を示します。"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 2e23ba46381b1fb80b8ac335f6d7630f02a222bb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Windows からのバックアップと復元を使用して Linux に SQL Server データベースを移行します。

SQL Server のバックアップと復元機能は、Linux 上の SQL Server 2017 RC2 への Windows 上の SQL Server からデータベースを移行することをお勧めします。 このトピックでは、この方法の手順を説明します。 このチュートリアルでは、次の作業を行います。

- Windows コンピューターで、AdventureWorks のバックアップ ファイルをダウンロードします。
- Linux コンピューターにバックアップを転送します。
- TRANSACT-SQL コマンドを使用して、データベースを復元します。

> [!NOTE] 
> このチュートリアルは、インストールしてあることを想定しています[SQL Server 2017 RC2](sql-server-linux-setup.md)と[SQL Server ツール](sql-server-linux-setup-tools.md)ターゲットの Linux サーバーでします。

## <a name="download-the-adventureworks-database-backup"></a>AdventureWorks データベースのバックアップをダウンロードします。

任意のデータベースを復元する同じ手順を使用できますが、AdventureWorks サンプル データベースは良い例を提供します。 既存のデータベース バックアップ ファイルとなります。

>[!NOTE] 
> Linux に SQL Server にデータベースを復元するには、SQL Server 2014 または SQL Server 2016 からソース バックアップを実行する必要があります。 ビルド番号の SQL Server のバックアップを復元の SQL Server のビルド番号より大きくすることはできません。  

1. Windows コンピューター上に移動[https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661)をダウンロードし、 **Adventure Works 2014 完全 Database Backup.zip**です。

   > [!TIP] 
   > このチュートリアルでは、バックアップと Windows と Linux の間での復元を示していますは、直接、Linux コンピューターに、AdventureWorks のサンプルをダウンロードするのに on Linux ブラウザーを使用することもできます。

2. Zip ファイルを開き、コンピューターのフォルダーに AdventureWorks2014.bak ファイルを抽出します。

## <a name="transfer-the-backup-file-to-linux"></a>Linux にバックアップ ファイルを転送します。

データベースを復元するには、Windows コンピューターからターゲットの Linux マシンをバックアップ ファイルを転送する必要があります。

1. Windows の場合は、Bash シェルをインストールします。 次のいくつかのオプションがあります。

   - など、オープン ソース、Bash シェルのダウンロード[PuTTY](http://www.putty.org/)です。
   - または、Windows 10 で、新しい使用[組み込み Bash シェル (ベータ)](https://msdn.microsoft.com/en-us/commandline/wsl/about)です。
   - または、Git を使用する場合に使用して、 [Git Bash シェル](https://git-scm.com/downloads)です。

2. Bash シェル (端末) を開き、含まれているディレクトリに移動**AdventureWorks2014.bak**です。

3. 使用して、 **scp**ターゲットの Linux コンピューターへファイルを転送する (セキュリティで保護されたコピー) コマンド。 次の例転送**AdventureWorks2014.bak**のホーム ディレクトリに*user1*という名前のサーバーで*linuxserver1*です。

   ```bash
   sudo scp AdventureWorks2014.bak user1@linuxserver1:./
   ```
   
   前の例では、代わりに、サーバー名の代わりに IP アドレスを指定できます。

Scp を使用していくつかの選択肢があります。 使用する 1 つは[Samba](https://help.ubuntu.com/community/Samba) Windows と Linux の間で SMB ネットワーク共有をセットアップします。 Ubuntu でチュートリアルは、次を参照してください。 [、ネットワーク共有を介して Samba を作成する方法](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!)です。 確立されると、ネットワーク ファイルとしてアクセスできるように、Windows から共有 **\\ \\machinenameorip\\共有**です。

## <a name="move-the-backup-file"></a>バックアップ ファイルを移動します。

この時点では、バックアップ ファイルが、Linux サーバーにします。 SQL Server にデータベースを復元する前のサブディレクトリに、バックアップを配置する必要があります**/var/opt/mssql**です。

1. バックアップが格納されているターゲットの Linux コンピューター上のターミナルを開きます。

2. スーパー ユーザーのモードを入力します。

   ```bash
   sudo su
   ```

3. 新しいバックアップ ディレクトリを作成します。 -P パラメーターは、ディレクトリが既に存在する場合に、何も行われません。

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

4. バックアップ ファイルをそのディレクトリに移動します。 ホーム ディレクトリで次の例では、バックアップ ファイルが存在する*user1*です。 変更の位置に合わせてコマンド**AdventureWorks2014.bak**コンピューターにします。

   ```bash
   mv /home/user1/AdventureWorks2014.bak /var/opt/mssql/backup/
   ```

5. スーパー ユーザーのモードを終了します。

   ```bash
   exit
   ```

## <a name="restore-the-database-backup"></a>データベース バックアップを復元します。

バックアップを復元するには、RESTORE DATABASE TRANSACT-SQL (TQL) コマンドを使用できます。

> [!NOTE] 
> 次の手順では、sqlcmd ツールを使用します。 インストールを行っていないかどうかは SQL Server ツールを参照してください[Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。

1. 同じターミナルで起動**sqlcmd**です。 次の例は、ローカルの SQL Server インスタンスに接続、 *SA*ユーザー。 プロンプトが表示または-p パラメーターを使用してパスワードを指定するときに、パスワードを入力します。

   ```bash
   sqlcmd -S localhost -U SA
   ```

2. 接続した後、次の入力**データベースの復元**コマンド、各行の後に ENTER キーを押します。 次の復元の例、 **AdventureWorks2014.bak**ファイルから、 */var/opt/mssql/backup*ディレクトリ。

   ```sql
   RESTORE DATABASE AdventureWorks
   FROM DISK = '/var/opt/mssql/backup/AdventureWorks2014.bak'
   WITH MOVE 'AdventureWorks2014_Data' TO '/var/opt/mssql/data/AdventureWorks2014_Data.mdf',
   MOVE 'AdventureWorks2014_Log' TO '/var/opt/mssql/data/AdventureWorks2014_Log.ldf'
   GO
   ```

   データベースの復元が正常にメッセージを取得する必要があります。

3. AdventureWorks データベースにコンテキストを変更して、復元を確認します。 

   ```sql
   USE AdventureWorks
   GO
   ```

4. 内の上位 10 製品を一覧表示する次のクエリ実行、 **Production.Products**テーブル。

   ```sql
   SELECT TOP 10 Name, ProductNumber FROM Production.Product ORDER BY Name
   GO
   ```

![Production.Products クエリからの出力](./media/sql-server-linux-migrate-restore-database/sql-server-linux-adventureworks-query.png)

## <a name="next-steps"></a>次の手順

その他のデータベースとデータの移行方法の詳細については、次を参照してください。 [Linux に SQL Server にデータベースを移行](sql-server-linux-migrate-overview.md)です。 

