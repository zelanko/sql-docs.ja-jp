---
title: "制限事項と既知の問題を Linux 上の SSIS の |Microsoft ドキュメント"
description: "この記事の内容について説明します制限事項と既知の問題 SQL Server Integration Services (SSIS) を Linux コンピューター上"
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 96bf588edd15c77caa6649ac04b6a95046135e95
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>制限事項と Linux の SSIS の既知の問題

このトピックの内容について説明します現在の制限事項と既知の問題 SQL Server Integration Services (SSIS) を Linux 上。

## <a name="general-limitations-and-known-issues"></a>一般的な制限事項と既知の問題

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

## <a name="components"></a>サポートされており、サポートされていないコンポーネント

次の組み込みの Integration Services コンポーネントは、Linux でサポートされます。 Linux プラットフォーム上の制限は、次の表で説明したようにそれらの一部があります。

ここに記載されていない組み込みのコンポーネントは、Linux ではサポートされていません。

### <a name="supported-control-flow-tasks"></a>制御フロー タスクのサポート
- 一括挿入タスク
- [データ フロー タスク]
- データ プロファイル タスク
- SQL 実行タスク
- T-SQL ステートメントの実行タスク
- 式タスク
- FTP タスク
- Web サービス タスク
- XML タスク

### <a name="control-flow-tasks-supported-with-limitations"></a>制御フロー タスクの制限付きでサポート

| タスク | 制限事項 |
|------------|---|
| プロセス実行タスク | インプロセス モードでのみサポートしています。 |
| ファイル システム タスク | *移動ディレクトリ*と*ファイル属性を設定*アクションはサポートされません。 |
| スクリプト タスク | 標準の .NET Framework Api をのみサポートされます。 |
| メール送信タスク | 匿名ユーザー モードのみをサポートします。 |
| データベース転送タスク | UNC パスはサポートされません。 |
| | |

### <a name="supported-control-flow-containers"></a>制御フロー コンテナーのサポート
- シーケンス コンテナー
- For ループ コンテナー
- Foreach ループ コンテナー

### <a name="supported-data-flow-sources-and-destinations"></a>サポートされているデータ フローの変換元および変換先
- Raw ファイル ソースと変換先
- XML ソース

### <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>データ フローの変換元および変換先の制限付きでサポート

| コンポーネント | 制限事項 |
|------------|---|
| ADO.NET ソースと変換先 | SQLClient データ プロバイダーのみをサポートします。 |
| フラット ファイル ソースと変換先 | のみ、既定のパス マッピング規則を適用する、Windows 形式ファイル パスをサポートします。 たとえば`D:\home\ssis\travel.csv`なります`/home/ssis/travel.csv`です。 |
| OData ソース | 基本認証のみをサポートします。 |
| Odbc 入力元および変換先 | Linux 上の 64 ビットの Unicode ODBC ドライバーをサポートしています。 Linux 上の UnixODBC ドライバー マネージャーに依存します。 |
| OLE DB ソースと変換先 | のみ SQL Server の SQL Server Native Client 11.0 と Microsoft OLE DB プロバイダーをサポートします。 |
| | |

### <a name="supported-data-flow-transformations"></a>データ フロー変換をサポート
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

### <a name="data-flow-transformations-supported-with-limitations"></a>データ フローの変換が制限付きでサポート

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

