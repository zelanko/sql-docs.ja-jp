---
title: "抽出、変換、および SSIS Linux でのデータを読み込む |Microsoft ドキュメント"
description: 
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: aa4ac0cca739ea57a28beb399325d55b38502217
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>抽出、変換、および SSIS Linux でのデータを読み込む

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックでは、Linux 上の SQL Server Integration Services (SSIS) パッケージを実行する方法について説明します。 SSIS は、複数のソースと形式からデータを抽出することで複雑なデータ統合の問題を解決し、データをクレンジング データ変換および読み込み、複数の送信先にします。 

Linux で実行されている SSIS パッケージは、Windows、オンプレミスまたはクラウドでは、Linux では、または Docker で実行されている Microsoft SQL Server に接続できます。 Azure SQL Database、Azure SQL Data Warehouse、ODBC データ ソース、フラット ファイル、および ADO.NET ソース、XML ファイル、および OData サービスを含む他のデータ ソースに接続することもできます。

SSIS の機能に関する詳細については、次を参照してください。 [SQL Server Integration Services](../integration-services/sql-server-integration-services.md)です。

## <a name="prerequisites"></a>前提条件

最初を Linux コンピューターで SSIS パッケージを実行するには、SQL Server Integration Services をインストールする必要があります。 SSIS は、Linux コンピューターの SQL Server のインストールには含まれません。 インストール手順については、次を参照してください。 [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)です。

さらに、作成およびパッケージを管理する Windows コンピューターをいなければなりません。 SSIS のデザインおよび管理ツールは、現在は使用できませんの Linux コンピューターを Windows アプリケーションです。 

## <a name="run-an-ssis-package"></a>SSIS パッケージを実行します。

Linux コンピューターで、SSIS パッケージを実行するには、次の作業を行います。

1.  SSIS パッケージを Linux コンピューターにコピーします。
2.  次のコマンドを実行します。
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="other-common-ssis-tasks"></a>その他の一般的な SSIS タスク

-   **パッケージをデザイン**です。

    -   **ODBC データ ソースに接続**です。 Linux CTP 2.1 の更新以降、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 この機能は、SQL Server および MySQL の ODBC ドライバーでテスト済みですはまた、ODBC 仕様に従うすべての Unicode ODBC ドライバーを使用する必要があります。 、デザイン時に、ODBC データに接続する DSN または接続文字列を指定できますWindows 認証を使用することもできます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

    -   **パス**です。 SSIS パッケージ内の Windows スタイル パスを提供します。 Linux 上の SSIS では、Linux スタイルのパスをサポートしていませんが、実行時に、Windows 形式のパスを Linux スタイル パスにマップします。 次に、たとえば、Linux 上の SSIS マップ Windows 形式のパス`C:\test`Linux スタイルのパスに`/test`です。

-   **パッケージを配置**です。 パッケージは、このリリースでは、Linux 上のファイル システムにのみ保存できます。 SSIS カタログ データベースと、レガシ SSIS サービスでは、パッケージの配置とストレージの Linux で使用できません。

-   **パッケージのスケジュール**です。 スケジューリング ツールなど、Linux システムを使用する`cron`パッケージをスケジュールします。 このリリースでは、パッケージの実行をスケジュールするのに Linux で SQL エージェントを使用することはできません。 詳細については、次を参照してください。 [cron を Linux 上のスケジュールの SSIS パッケージ](sql-server-linux-schedule-ssis-packages.md)です。

## <a name="limitations-and-known-issues"></a>制限事項と既知の問題

### <a name="general-limitations-and-known-issues"></a>一般的な制限事項と既知の問題

次の機能は、Linux 上の SSIS のこのリリースではサポートされません。
  - SSIS カタログ データベース
  - SQL エージェントがスケジュールされているパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - SSIS のスケール アウト
  - SSIS 用 azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

その他の制限事項と Linux 上の SSIS に関する既知の問題には、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md#ssis)です。

### <a name="components"></a>サポートされており、サポートされていないコンポーネント

次の組み込みの Integration Services コンポーネントは、Linux でサポートされます。 Linux プラットフォーム上の制限は、次の表で説明したようにそれらの一部があります。

ここに記載されていない組み込みのコンポーネントは、Linux ではサポートされていません。

#### <a name="supported-control-flow-tasks"></a>制御フロー タスクのサポート
- 一括挿入タスク
- [データ フロー タスク]
- データ プロファイル タスク
- SQL 実行タスク
- T-SQL ステートメントの実行タスク
- 式タスク
- FTP タスク
- Web サービス タスク
- XML タスク

#### <a name="control-flow-tasks-supported-with-limitations"></a>制御フロー タスクの制限付きでサポート

| タスク | 制限事項 |
|------------|---|
| プロセス実行タスク | インプロセス モードでのみサポートしています。 |
| ファイル システム タスク | *移動ディレクトリ*と*ファイル属性を設定*アクションはサポートされません。 |
| スクリプト タスク | 標準の .NET Framework Api をのみサポートされます。 |
| メール送信タスク | 匿名ユーザー モードのみをサポートします。 |
| データベース転送タスク | UNC パスはサポートされません。 |
| | |

#### <a name="supported-control-flow-containers"></a>制御フロー コンテナーのサポート
- シーケンス コンテナー
- For ループ コンテナー
- Foreach ループ コンテナー

#### <a name="supported-data-flow-sources-and-destinations"></a>サポートされているデータ フローの変換元および変換先
- Raw ファイル ソースと変換先
- XML ソース

#### <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>データ フローの変換元および変換先の制限付きでサポート

| コンポーネント | 制限事項 |
|------------|---|
| ADO.NET ソースと変換先 | SQLClient データ プロバイダーのみをサポートします。 |
| フラット ファイル ソースと変換先 | のみ、既定のパス マッピング規則を適用する、Windows 形式ファイル パスをサポートします。 たとえば`D:\home\ssis\travel.csv`なります`/home/ssis/travel.csv`です。 |
| OData ソース | 基本認証のみをサポートします。 |
| Odbc 入力元および変換先 | Linux 上の 64 ビットの Unicode ODBC ドライバーをサポートしています。 Linux 上の UnixODBC ドライバー マネージャーに依存します。 |
| OLE DB ソースと変換先 | のみ SQL Server の SQL Server Native Client 11.0 と Microsoft OLE DB プロバイダーをサポートします。 |
| | |

#### <a name="supported-data-flow-transformations"></a>データ フロー変換をサポート
- Aggregate
- 監査
- Balanced Data Distributor
- 文字マップ
- 条件分割
- 列コピー
- データ変換
- [派生列]
- 列エクスポート
- あいまいグループ化
- あいまい参照
- 列インポート
- Lookup
- Merge
- マージ結合
- マルチキャスト
- ピボット
- 行数
- 緩やかに変化するディメンション
- 並べ替え
- 用語参照
- Union All
- ピボット解除

#### <a name="data-flow-transformations-supported-with-limitations"></a>データ フローの変換が制限付きでサポート

| コンポーネント | 制限事項 |
|------------|---|
| OLE DB コマンド変換 | OLE DB ソースと宛先のと同じ制限はします。 |
| スクリプト コンポーネント | 標準の .NET Framework Api をのみサポートされます。 |
| | |

### <a name="supported-and-unsupported-log-providers"></a>サポートされており、サポートされていないログ プロバイダー
Windows イベント ログ プロバイダーを除く組み込みの SSIS ログ プロバイダーが Linux でサポートされているすべてとします。

SQL Server ログ プロバイダーは、SQL 認証のみをサポートしています。Windows 認証をサポートしていません。

テキスト ファイル、XML ファイル、および SQL Server Profiler の SSIS ログ プロバイダーは、その出力を指定したファイルに書き込みます。 ファイルのパスに次の考慮事項が適用されます。
-   パスを指定しない場合、ログ プロバイダーは、ホストの現在のディレクトリに書き込みます。 現在のユーザーには、ホストの現在のディレクトリに対する書き込みアクセス許可が割り当てられていない、ログ プロバイダーは、エラーが発生します。
-   ファイル パスで環境変数を使用することはできません。 環境変数を指定すると、ファイル パスで指定されたリテラルのテキストが表示されます。 指定する場合など、 `%TMP%/log.txt`、ログ プロバイダーは、リテラル テキストを追加する`/%TMP%/log.txt`ホストの現在のディレクトリにします。

## <a name="more-info-about-ssis-on-linux"></a>詳細については、Linux 上の SSIS

Linux 上の SSIS の詳細については、次のブログの投稿を参照してください。

-   [Linux 上の SSIS では、SQL Server 2017 CTP2.1 で使用できます。](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC は (SQL Server 2017 CTP 2.1 更新) を Linux 上の SSIS でサポートされています。](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>詳細については、SSIS

Microsoft SQL Server Integration Services (SSIS) は、抽出、変換、およびデータ ウェアハウスの読み込み (ETL) のパッケージを含む、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。 詳細については、「[SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md)」を参照してください。

SSIS では、次の機能があります。
- グラフィカル ツールとのビルドと Windows 上のパッケージをデバッグするためのウィザード
- さまざまな SQL ステートメントの実行、電子メール メッセージを送信する FTP 操作などのワークフロー機能を実行するタスク
- さまざまなデータ ソースおよび変換先を抽出およびデータの読み込みを行う
- さまざまなクリーニング、集計、マージ、およびデータのコピーの変換
- 独自のカスタム スクリプトおよびコンポーネントと SSIS を拡張するためのアプリケーション プログラミング インターフェイス (Api)

最新バージョンをダウンロード、SSIS で作業を開始する[SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md)です。

## <a name="see-also"></a>参照
- [SQL Server Integration Services の詳細を表示します](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) の開発および管理ツール](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [SQL Server Integration Services のチュートリアル](../integration-services/integration-services-tutorials.md)

