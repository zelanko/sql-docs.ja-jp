---
title: "SSMS を使用して Linux 上の SQL Server を管理する |Microsoft ドキュメント"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 08/23/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: b2fcf858-21c3-462a-8d49-50c85647d092
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: f8dd1654dc05a89147ecf9d658d492adeb3d0ceb
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="use-sql-server-management-studio-on-windows-to-manage-sql-server-on-linux"></a>Linux 上の SQL Server を管理するのに Windows 上の SQL Server Management Studio の使用します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックで紹介[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)と、いくつかの一般的なタスクについて説明します。 SSMS は、Windows アプリケーション、ので Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合に SSMS を使用します。

[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) Microsoft は無料の開発と管理のニーズに SQL ツールのセットの一部です。 SSMS は、アクセス、構成、管理、管理、およびオンプレミスで実行して SQL Server または Linux、Windows または macOS と Azure SQL データベース上の Docker と Azure SQL Data Warehouse で、クラウド内のすべてのコンポーネントを開発する統合環境です。 SSMS では、あらゆるスキルレベルの開発者や管理者に SQL Server へのアクセスを提供する高機能スクリプト エディターの数がグラフィカルなツールの広範なグループを結合します。

SSMS では、ツールなど、SQL Server の開発および管理機能の広範なを提供しています。

- 構成、監視、および 1 つまたは複数の SQL Server インスタンスの管理
- 展開、監視、およびデータ層のコンポーネントをアップグレードなど、データベースおよびデータ ウェアハウス
- データベースのバックアップと復元
- ビルドし T-SQL クエリとスクリプトの実行し、結果を参照してください。
- データベース オブジェクトの T-SQL スクリプトを生成します。
- データベース内のデータを表示および更新
- T-SQL クエリおよびビュー、テーブルおよびストアド プロシージャなどのデータベース オブジェクトを視覚的にデザインします。

参照してください[SQL Server Management Studio の使用](https://msdn.microsoft.com/en-us/library/ms174173.aspx)詳細についてはします。

## <a name="install-the-newest-version-of-sql-server-management-studio-ssms"></a>最新バージョンの SQL Server Management Studio (SSMS) のインストールします。

SQL Server を使用する場合は、常に最新バージョンの SQL Server Management Studio (SSMS) を使用する必要があります。 SSMS の最新バージョンは継続的に更新および最適化されている 2017 on Linux を SQL Server で現在動作します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)です。 最新の状態に、SSMS の最新バージョンように求められますダウンロード可能な新しいバージョンがある場合。 

## <a name="before-you-begin"></a>アンインストールの準備
- 参照してください[on Linux に SQL Server への接続に Windows を使用して SSMS](sql-server-linux-develop-use-ssms.md)に接続し、SSMS を使用してクエリを実行する方法
- 読み取り、[既知の問題](sql-server-linux-release-notes.md)for Linux に SQL Server 2017

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

4. *オブジェクトの削除*ダイアログ ボックスで、チェック*既存の接続を閉じる*をクリックし、 *OK*

データベースは、サーバーから正常に削除されました。 T-SQL を使用してデータベースを削除する場合を参照してください[DROP DATABASE (SQL Server TRANSACT-SQL)](../t-sql/statements/drop-database-transact-sql.md)です。

## <a name="use-activity-monitor-to-see-information-about-sql-server-activity"></a>利用状況モニターを使用して、SQL Server の利用状況に関する情報を表示するには

[利用状況モニター](../relational-databases/performance-monitor/activity-monitor.md)ツール組み込み SQL Server Management Studio (SSMS) には、SQL Server プロセスおよびこれらのプロセスが現在の SQL Server インスタンスに与える影響に関する情報が表示されます。

1. SSMS を起動し、Linux 上の SQL Server 2017 内のサーバーに接続

2. オブジェクト エクスプ ローラーで右クリックし、*サーバー*ノードをクリックして*利用状況モニター*

利用状況モニターは、次の情報と共に展開と折りたたみのウィンドウを示しています。
- 概要
- プロセス
- リソース待機
- データ ファイル I/O
- 最新のコストの高いクエリ
- Active Expensive Queries

ウィンドウを展開すると、利用状況モニターによってインスタンスに対して情報を照会します。 ペインを折りたたむと、そのペインのすべての利用状況クエリが停止します。 1 つまたは複数のペインを展開し、さまざまな種類のアクティビティのインスタンスを表示する、同時にすることができます。

## <a name="see-also"></a>参照
- [SQL Server Management Studio の使用 [SQL Server]](https://msdn.microsoft.com/en-us/library/ms174173.aspx)
- [エクスポートし、SSMS でデータベースをインポートします。](sql-server-linux-migrate-ssms.md)
- [チュートリアル: SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/bb934498.aspx)
- [チュートリアル: Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)
- [サーバーのパフォーマンスと利用状況の監視](../relational-databases/performance/server-performance-and-activity-monitoring.md)

