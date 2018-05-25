---
title: SSMS を使用して Linux 上の SQL Server を管理する |Microsoft ドキュメント
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/21/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: b2fcf858-21c3-462a-8d49-50c85647d092
ms.custom: sql-linux
ms.openlocfilehash: 2b6293e7c0d80eb1ebe02d6cd03f17626d793c05
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="use-sql-server-management-studio-on-windows-to-manage-sql-server-on-linux"></a>Linux 上の SQL Server を管理するのに Windows 上の SQL Server Management Studio の使用します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事で紹介[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)と、いくつかの一般的なタスクについて説明します。 SSMS は、Windows アプリケーション、ので Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合に SSMS を使用します。

> [!TIP]
> Windows コンピューターで SSMS を実行する必要はない場合を検討して、新しい[SQL Server の Operations Studio](../sql-operations-studio/index.md)です。 SQL Server を管理するためのグラフィカル ツールを提供し、Windows および Linux の両方を実行します。

[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) Microsoft は無料の開発と管理のニーズに SQL ツールのセットの一部です。 SSMS は、アクセス、構成、管理、管理、および SQL Server のすべてのコンポーネントを開発する統合環境です。 これは、任意のプラットフォームで両方オンプレミスで実行して、Docker コンテナーでクラウド内や SQL Server に接続できます。 Azure SQL Database と Azure SQL Data Warehouse にも接続します。 SSMS では、あらゆるスキルレベルの開発者や管理者に SQL Server へのアクセスを提供する高機能スクリプト エディターの数がグラフィカルなツールの広範なグループを結合します。

SSMS では、ツールなど、SQL Server の開発および管理機能の広範なを提供しています。

- 構成、監視、および 1 つまたは複数の SQL Server インスタンスを管理します。
- 展開、監視、およびデータ層のコンポーネントをアップグレードなど、データベースおよびデータ ウェアハウス
- データベースのバックアップと復元
- ビルドし T-SQL クエリとスクリプトの実行し、結果を参照してください。
- データベース オブジェクトの T-SQL スクリプトを生成します。
- データベース内のデータを表示および更新
- T-SQL クエリおよびビュー、テーブル、およびストアド プロシージャなどのデータベース オブジェクトを視覚的にデザインします。

参照してください[SSMS は何ですか。](../ssms/sql-server-management-studio-ssms.md) SSMS についての詳細。

## <a name="install-the-newest-version-of-sql-server-management-studio-ssms"></a>最新バージョンの SQL Server Management Studio (SSMS) のインストールします。

SQL Server を使用する場合は、常に最新バージョンの SQL Server Management Studio (SSMS) を使用する必要があります。 SSMS の最新バージョンは継続的に更新および最適化されている 2017 on Linux を SQL Server で現在動作します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)です。 最新の状態に、SSMS の最新バージョンように求められますダウンロード可能な新しいバージョンがある場合。

> [!NOTE]
> Linux の管理に SSMS を使用する前に確認、[既知の問題](sql-server-linux-release-notes.md)Linux 上の ssms です。

## <a name="connect-to-sql-server-on-linux"></a>Linux 上の SQL Server への接続します。

接続するために、次の基本的な手順を使用します。

1. 入力して、SSMS を起動**Microsoft SQL Server Management Studio** Windows の検索ボックスで、およびデスクトップ アプリをクリックします。

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png)

1. **サーバーへの接続** ウィンドウで、次の情報を入力してください (SSMS が既に実行されている場合はクリックして**接続 > データベース エンジン**を開くには、**サーバーへの接続**ウィンドウ)。

   | 設定 | Description |
   |-----|-----|
   | **サーバーの種類** | 既定では、データベース エンジンです。この値を変更することはできません。 |
   | **サーバー名** | 対象の Linux SQL Server コンピューターまたは IP アドレスの名前を入力します。 |
   | **[認証]** | Linux 上の SQL Server 2017、使用**SQL Server 認証**です。 |
   | **Login** | サーバー上のデータベースにアクセス権を持つユーザーの名前を入力してください (たとえば、既定値**SA**セットアップ中に作成したアカウント)。 |
   | **Password** | 指定したユーザーのパスワードを入力 (用、 **SA**アカウントを作成したセットアップ時に)。 |

    ![SQL Server Management Studio: SQL データベース サーバーへの接続します。](./media/sql-server-linux-manage-ssms/connect.png)

1. **[接続]** をクリックします。

    > [!TIP]
    > 接続エラーが発生した場合は、まずエラー メッセージから問題を診断します。 次に、[接続のトラブルシューティングに関する推奨事項](sql-server-linux-troubleshooting-guide.md#connection)を確認します。
 
1. SQL Server に正常に接続した後**オブジェクト エクスプ ローラー**が開き、データベース管理タスクを実行またはデータをクエリにアクセスできます。

## <a name="run-transact-sql-queries"></a>TRANSACT-SQL クエリを実行します。

サーバーに接続した後は、データベースへの接続し、TRANSACT-SQL クエリを実行します。 Transact SQL クエリは、ほぼすべてのデータベース タスクで使用できます。

1. **オブジェクト エクスプ ローラー**サーバー上のターゲット データベースに移動します。 たとえば、**システム データベース**を使用する、**マスター**データベース。

1. データベースを右クリックし、**新しいクエリ**です。

1. クエリ ウィンドウには、すべてのデータベースの名前の戻り値を選択する TRANSACT-SQL クエリを記述、サーバー上。

   ```sql
   SELECT [Name]
   FROM sys.Databases
   ```

   新しいクエリを記述する場合を参照してください。 [TRANSACT-SQL ステートメントの記述](../t-sql/tutorial-writing-transact-sql-statements.md)です。

1. クリックして、 **Execute**クエリを実行し、結果を表示するボタンをクリックします。

   ![正常終了しました。 SQL データベース サーバーに接続します SQL Server Management Studio。](./media/sql-server-linux-manage-ssms/execute-query.png)

ほぼ任意の管理タスクに TRANSACT-SQL クエリを行うことはできますが、SSMS はできるグラフィカル ツール SQL Server の管理が容易になります。 次のセクションでは、グラフィカル ユーザー インターフェイスを使用する例をいくつかを示します。

## <a name="create-and-manage-databases"></a>作成し、データベースの管理

接続されている、*マスター*データベース、サーバー上のデータベースを作成し、変更したり既存のデータベースを削除します。 次の手順では、Management Studio を使用、いくつかの共通するデータベースの管理タスクを実行する方法について説明します。 これらのタスクを実行することを確認してくださいに接続している、*マスター* Linux 上の SQL Server 2017 を設定するときに作成した、サーバー レベル プリンシパル ログインとデータベースです。

### <a name="create-a-new-database"></a>新しいデータベースの作成

1. SSMS を起動し、Linux 上の SQL Server 2017 内のサーバーに接続

2. オブジェクト エクスプ ローラーを右クリックし、*データベース*フォルダー、およびクリック * 新しい Database…"

3. *新しいデータベース*ダイアログ ボックスを新しいデータベースの名前を入力し、クリックして*OK*

新しいデータベースが、サーバーで正常に作成されます。 T-SQL を使用して新しいデータベースを作成する場合を参照してください[CREATE DATABASE (SQL Server TRANSACT-SQL)](../t-sql/statements/create-database-sql-server-transact-sql.md)です。

### <a name="drop-a-database"></a>データベースを削除します。

1. SSMS を起動し、Linux 上の SQL Server 2017 内のサーバーに接続

2. オブジェクト エクスプ ローラーで、展開、*データベース*サーバー上のすべてのデータベースの一覧を表示するフォルダーです。

3. オブジェクト エクスプ ローラーを削除するデータベースを右クリックし、をクリックして*削除*

4. *オブジェクトの削除*ダイアログ ボックスで、チェック*既存の接続を閉じる* をクリックし、 *OK*

データベースは、サーバーから正常に削除されました。 T-SQL を使用してデータベースを削除する場合を参照してください[DROP DATABASE (SQL Server TRANSACT-SQL)](../t-sql/statements/drop-database-transact-sql.md)です。

## <a name="use-activity-monitor-to-see-information-about-sql-server-activity"></a>利用状況モニターを使用して、SQL Server の利用状況に関する情報を表示するには

[利用状況モニター](../relational-databases/performance-monitor/activity-monitor.md)ツールは、SQL Server Management Studio (SSMS) に適用され、SQL Server プロセスおよびこれらのプロセスが現在の SQL Server インスタンスに与える影響に関する情報が表示されます。

1. SSMS を起動し、Linux 上の SQL Server 2017 内のサーバーに接続

1. オブジェクト エクスプ ローラーで右クリックし、*サーバー*ノードをクリックして*利用状況モニター*

利用状況モニターは、次の情報と共に展開と折りたたみのウィンドウを示しています。

- 概要
- プロセス
- リソース待機
- データ ファイル I/O
- 最新のコストの高いクエリ
- Active Expensive Queries

ウィンドウを展開すると、利用状況モニターによってインスタンスに対して情報を照会します。 ペインを折りたたむと、そのペインのすべての利用状況クエリが停止します。 1 つまたは複数のペインを展開し、さまざまな種類のアクティビティのインスタンスを表示する、同時にすることができます。

## <a name="see-also"></a>参照
- [SSMS とは](../ssms/sql-server-management-studio-ssms.md)
- [エクスポートし、SSMS でデータベースをインポートします。](sql-server-linux-migrate-ssms.md)
- [チュートリアル: SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)
- [チュートリアル : Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)
- [サーバーのパフォーマンスと利用状況の監視](../relational-databases/performance/server-performance-and-activity-monitoring.md)
