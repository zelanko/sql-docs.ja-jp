---
title: 制限事項と Linux での SSIS の既知の問題 |Microsoft Docs
description: この記事について説明します制限事項と既知の問題の SQL Server Integration Services (SSIS) によって Linux コンピューターに
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
manager: craigg
ms.date: 06/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: c2e26f7a5a239a4fa25d2e2a7deb71677ac856cb
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66014968"
---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>制限事項と Linux での SSIS の既知の問題

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事について説明します制限事項と既知の問題の SQL Server Integration Services (SSIS) Linux 上。

## <a name="general-limitations-and-known-issues"></a>一般的な制限事項と既知の問題

Linux 上の SSIS のこのリリースでは、次の機能はサポートされていません。
  - SSIS カタログ データベース
  - SQL エージェントでスケジュールされたパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - SSIS スケール アウト
  - Azure Feature Pack for SSIS
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

その他の制限事項と Linux での SSIS に関する既知の問題では、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md#ssis)します。

## <a name="components"></a> サポートされているとサポート非対象のコンポーネント

次の組み込みの Integration Services コンポーネントは、Linux でサポートされます。 Linux プラットフォームでそれらの一部には制限があります。 ここに記載されていない組み込みのコンポーネントは Linux ではサポートされていません。

## <a name="supported-control-flow-tasks"></a>制御フロー タスクのサポート
- 一括挿入タスク
- [データ フロー タスク]
- データ プロファイル タスク
- SQL 実行タスク
- T-SQL ステートメントの実行タスク
- 式タスク
- FTP タスク
- Web サービス タスク
- XML タスク

## <a name="control-flow-tasks-supported-with-limitations"></a>制御フローのタスクの制限付きサポート

| タスク | 制限事項 |
|------------|---|
| プロセス実行タスク | インプロセス モードのみをサポートします。 |
| ファイル システム タスク | *移動ディレクトリ*と*ファイル属性を設定*操作がサポートされていません。 |
| スクリプト タスク | 標準の .NET Framework Api のみをサポートします。 |
| メール送信タスク | 匿名ユーザー モードのみをサポートします。 |
| データベース転送タスク | UNC パスはサポートされません。 |
| | |

## <a name="supported-and-unsupported-maintenance-plan-tasks"></a>サポートされているとサポートされていないメンテナンス プランのタスク

SQL Server メンテナンス プランでは、通常のさまざまな SSIS タスクを使用できます。

次のメンテナンス プランのタスクは、Linux ではサポートされません。
- オペレーターに通知します。
- SQL Server エージェント ジョブを実行します。

Linux では、次のメンテナンス プランのタスクがサポートされています。
- データベースの整合性を確認してください。
- データベースを圧縮します。
- [インデックスの再構成]
- インデックスを再構築します。
- 統計の更新
- 履歴をクリーンアップします。
- データベースをバックアップします。
- T-SQL ステートメント

## <a name="supported-control-flow-containers"></a>制御フロー コンテナーのサポート
- シーケンス コンテナー
- For ループ コンテナー
- Foreach ループ コンテナー

## <a name="supported-data-flow-sources-and-destinations"></a>サポートされているデータ フローの変換元および変換先
- Raw ファイル ソースと変換先
- XML ソース

## <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>データ フローの変換元および変換先の制限付きでサポート

| コンポーネント | 制限事項 |
|------------|---|
| ADO.NET ソースと変換先 | のみ、SQLClient データ プロバイダーをサポートします。 |
| フラット ファイル ソースと変換先 | 既定のパス マッピング規則が適用される、Windows スタイルのファイル パスがのみサポートします。 たとえば`D:\home\ssis\travel.csv`なります`/home/ssis/travel.csv`します。 |
| OData ソース | 基本認証のみをサポートします。 |
| ODBC のソースとターゲット | Linux 上の 64 ビットの Unicode ODBC ドライバーをサポートしています。 Linux 上の UnixODBC ドライバー マネージャーによって異なります。 |
| OLE DB ソースと変換先 | のみ SQL Server の SQL Server Native Client 11.0、Microsoft OLE DB プロバイダーをサポートします。 |
| | |

## <a name="supported-data-flow-transformations"></a>サポートされているデータ フローの変換
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

## <a name="data-flow-transformations-supported-with-limitations"></a>データ フローの変換の制限付きサポート

| コンポーネント | 制限事項 |
|------------|---|
| OLE DB コマンド変換 | OLE DB ソースおよびターゲットとして同じ制限します。 |
| スクリプト コンポーネント | 標準の .NET Framework Api のみをサポートします。 |
| | |

## <a name="supported-and-unsupported-log-providers"></a>サポートされているとサポート非対象のログ プロバイダー
組み込みの SSIS ログ プロバイダーが Linux でサポートされているすべては、Windows イベント ログ プロバイダーを除きます。

SQL Server ログ プロバイダーは、SQL 認証のみをサポートしています。Windows 認証をサポートしていません。

テキスト ファイル、XML ファイル、および SQL Server Profiler の SSIS ログ プロバイダーは、その出力を指定したファイルに書き込みます。 ファイルのパスに次の考慮事項が適用されます。
-   パスを指定しなかった場合、ログ プロバイダーは、ホストの現在のディレクトリに書き込みます。 現在のユーザーには、ホストの現在のディレクトリに対する書き込みアクセス許可を持っていない、ログ プロバイダーは、エラーが発生します。
-   ファイル パスで環境変数を使用することはできません。 環境変数を指定する場合、ファイル パスで指定したリテラル テキストが表示されます。 たとえば、指定した場合`%TMP%/log.txt`、ログ プロバイダーは、リテラル テキストを追加します。`/%TMP%/log.txt`ホストの現在のディレクトリにします。

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS に関する関連コンテンツ
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [Ssis conf で Linux 上の SQL Server Integration Services を構成します。](sql-server-linux-configure-ssis.md)
-   [スケジュールの SQL Server Integration Services パッケージ cron を使用した Linux 上の実行](sql-server-linux-schedule-ssis-packages.md)
