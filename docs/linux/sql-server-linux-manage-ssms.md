---
title: SSMS を使用して、SQL Server on Linux を管理する |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/21/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: b2fcf858-21c3-462a-8d49-50c85647d092
ms.custom: sql-linux
ms.openlocfilehash: b0a16d3818195da0a98557025d0fe96c3d5333ee
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086774"
---
# <a name="use-sql-server-management-studio-on-windows-to-manage-sql-server-on-linux"></a>Windows 上の SQL Server Management Studio を使用して、Linux 上の SQL Server を管理するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事で紹介[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)するいくつかの一般的なタスクについて説明します。 SSMS は、Windows アプリケーション、ため Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合に SSMS を使用します。

> [!TIP]
> Windows コンピューターで SSMS を実行する必要はない場合を検討して、新しい[SQL Server Operations Studio](../sql-operations-studio/index.md)します。 SQL Server を管理するためのグラフィカルなツールを提供し、Linux と Windows の両方で実行します。

[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)は Microsoft の無料の開発と管理のニーズの SQL ツールのスイートの一部です。 SSMS は、アクセス、構成、管理、管理、および SQL Server のすべてのコンポーネントを開発するための統合環境です。 これは、Docker コンテナー、およびクラウド、オンプレミスを任意のプラットフォームで実行する SQL Server に接続できます。 また Azure SQL Database と Azure SQL Data Warehouse に接続します。 SSMS は、あらゆるスキルレベルの開発者や管理者に SQL Server へのアクセスを提供する高機能スクリプト エディターの数が、グラフィカルなツールの広範なグループを結合します。

SSMS では、ツールなど、SQL Server のさまざまな開発および管理機能を提供します。

- 構成、監視、および 1 つまたは複数の SQL Server インスタンスの管理
- デプロイ、監視、およびデータ層のコンポーネントをアップグレードなど、データベースやデータ ウェアハウス
- データベースのバックアップと復元
- ビルドし T-SQL クエリとスクリプトの実行し、結果を参照してください。
- データベース オブジェクトの T-SQL スクリプトを生成します。
- データベース内のデータを表示および更新
- T-SQL クエリおよびビュー、テーブル、およびストアド プロシージャなどのデータベース オブジェクトを視覚的に設計します。

参照してください[SSMS とは何ですか?](../ssms/sql-server-management-studio-ssms.md) SSMS の詳細についてはします。

## <a name="install-the-newest-version-of-sql-server-management-studio-ssms"></a>最新バージョンの SQL Server Management Studio (SSMS) のインストールします。

SQL Server を使用する場合は、最新バージョンの SQL Server Management Studio (SSMS) を常に使用する必要があります。 SSMS の最新バージョンは更新は継続的に最適化し、2017 on Linux を SQL Server で現在動作します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)します。 最新の情報、ダウンロード可能な新しいバージョンがある場合にする最新バージョンの SSMS を求めます。

> [!NOTE]
> SSMS を使用して、Linux の管理を開始する前に、[既知の問題](sql-server-linux-release-notes.md)Linux 上の SSMS の。

## <a name="connect-to-sql-server-on-linux"></a>SQL Server on Linux への接続します。

接続するために、次の基本的な手順を使用します。

1. 」と入力して SSMS を起動**Microsoft SQL Server Management Studio** Windows では、検索ボックス、およびデスクトップ アプリをクリックします。

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png)

1. **サーバーへの接続**ウィンドウで、次の情報を入力します (SSMS が既に実行されている場合はクリックして**Connect > データベース エンジン**を開く、**サーバーへの接続**ウィンドウ):

   | 設定 | 説明 |
   |-----|-----|
   | **サーバーの種類** | 既定値はデータベース エンジンです。この値は変更しないでください。 |
   | **サーバー名** | 対象の Linux SQL Server コンピューターまたは IP アドレスの名前を入力します。 |
   | **[認証]** | Linux 上の SQL Server 2017 を使用して**SQL Server 認証**します。 |
   | **Login** | サーバー上のデータベースにアクセス権を持つユーザーの名前を入力します (既定ではたとえば、 **SA**セットアップ中に作成したアカウント)。 |
   | **Password** | 指定したユーザーのパスワードを入力します (用、 **SA**アカウントを作成したこのセットアップ中に)。 |

    ![SQL Database サーバーに接続する SQL Server Management Studio:](./media/sql-server-linux-manage-ssms/connect.png)

1. **[接続]** をクリックします。

    > [!TIP]
    > 接続エラーが発生した場合は、まずエラー メッセージから問題を診断します。 次に、[接続のトラブルシューティングに関する推奨事項](sql-server-linux-troubleshooting-guide.md#connection)を確認します。
 
1. SQL Server に正常に接続した後**オブジェクト エクスプ ローラー**が開き、データベースを管理タスクの実行やデータのクエリにアクセスできます。

## <a name="run-transact-sql-queries"></a>TRANSACT-SQL クエリの実行

サーバーに接続した後は、データベースに接続して、TRANSACT-SQL クエリを実行します。 Transact SQL クエリは、ほぼすべてのデータベース タスクを使用できます。

1. **オブジェクト エクスプ ローラー**サーバー上のターゲット データベースに移動します。 たとえば、**システム データベース**を使用する、**マスター**データベース。

1. データベースを右クリックし、**新しいクエリ**します。

1. クエリ ウィンドウで、すべてのデータベースの名前を戻り値を選択します。 TRANSACT-SQL クエリを記述、サーバー上。

   ```sql
   SELECT [Name]
   FROM sys.Databases
   ```

   新しいクエリを記述する場合を参照してください。 [TRANSACT-SQL ステートメントの記述](../t-sql/tutorial-writing-transact-sql-statements.md)します。

1. をクリックして、 **Execute**クエリを実行し、結果を表示するボタンをクリックします。

   ![正常終了しました。 SQL Database サーバーへの接続: SQL Server Management Studio](./media/sql-server-linux-manage-ssms/execute-query.png)

Transact SQL クエリと管理タスクほぼすべてを実行することはできますが、SSMS は、グラフィカルなツールが SQL Server を管理しやすいです。 次のセクションでは、グラフィカル ユーザー インターフェイスを使用していくつかの例を提供します。

## <a name="create-and-manage-databases"></a>作成し、データベースの管理

接続されている、*マスター*データベース、サーバーにデータベースを作成および変更したり既存のデータベースを削除します。 次の手順では、いくつかの一般的なデータベース管理タスク Management studio を実行する方法について説明します。 これらのタスクを実行することを確認に接続している、*マスター* SQL Server 2017 on Linux を設定するときに作成した、サーバー レベル プリンシパル ログインを持つデータベース。

### <a name="create-a-new-database"></a>新しいデータベースの作成

1. SSMS を開始し、SQL Server 2017 on Linux で、サーバーに接続します。

2. オブジェクト エクスプ ローラーを右クリックし、*データベース*フォルダー、およびクリック * 新しいデータベース"

3. *新しいデータベース*ダイアログ ボックスで、新しいデータベースの名前を入力し、クリックして*OK*

新しいデータベースがサーバーで正常に作成されます。 場合は、T-SQL を使用して新しいデータベースを作成する を参照してください[CREATE DATABASE (SQL Server TRANSACT-SQL)](../t-sql/statements/create-database-sql-server-transact-sql.md)します。

### <a name="drop-a-database"></a>データベースを削除します。

1. SSMS を開始し、SQL Server 2017 on Linux で、サーバーに接続します。

2. オブジェクト エクスプ ローラーで、*データベース*サーバー上のすべてのデータベースの一覧を表示するフォルダー。

3. オブジェクト エクスプ ローラーで、削除するデータベースを右クリックし、*削除*

4. *オブジェクトの削除*ダイアログ ボックスで、*既存の接続を閉じる*順にクリックします*OK*

データベースは、サーバーから正常に削除されます。 場合は、T-SQL を使用してデータベースを削除する を参照してください[DROP DATABASE (SQL Server TRANSACT-SQL)](../t-sql/statements/drop-database-transact-sql.md)します。

## <a name="use-activity-monitor-to-see-information-about-sql-server-activity"></a>利用状況モニターを使用して、SQL Server の利用状況に関する情報を参照してください。

[の利用状況モニター](../relational-databases/performance-monitor/activity-monitor.md)ツールは、SQL Server Management Studio (SSMS) には構築され、SQL Server のプロセスおよびこれらのプロセスが現在の SQL Server インスタンスに与える影響についての情報が表示されます。

1. SSMS を開始し、SQL Server 2017 on Linux で、サーバーに接続します。

1. オブジェクト エクスプ ローラーで右クリックし、 *server*ノード、およびクリック*の利用状況モニター*

利用状況モニターは、次の情報を展開および折りたたみ可能なペインを示しています。

- 概要
- プロセス
- リソースの待機
- データ ファイル I/O
- 最新のコストの高いクエリ
- Active Expensive Queries

ペインを展開すると、利用状況モニターはインスタンスに対して情報を照会します。 ペインを折りたたむと、そのペインのすべての利用状況クエリが停止します。 1 つまたは複数のペインを展開し、同時インスタンスのさまざまな種類のアクティビティを表示することができます。

## <a name="see-also"></a>参照
- [SSMS とは](../ssms/sql-server-management-studio-ssms.md)
- [エクスポートし、SSMS でデータベースをインポートします。](sql-server-linux-migrate-ssms.md)
- [チュートリアル: SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)
- [チュートリアル: Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)
- [サーバーのパフォーマンスと利用状況の監視](../relational-databases/performance/server-performance-and-activity-monitoring.md)
