---
title: Azure Data Studio とは
titleSuffix: Azure Data Studio
description: Azure Data Studio は、無料の軽量ツール、SQL Server、Azure SQL Database、および Azure SQL Data Warehouse を管理するために、Windows、macOS、および Linux で実行されているです。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: overview
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.openlocfilehash: 1484d0bf2598cc3db8314c088b081ccd9327f5fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801919"
---
# <a name="what-is-azure-data-studio"></a>Azure Data Studio とは何ですか。

Azure Data Studio クロス プラットフォームは、オンプレミスの Microsoft ファミリを使用してデータのプロフェッショナル向けのツールのデータベースし、クラウドの Windows、MacOS、Linux でのデータ プラットフォーム。

SQL Operations Studio のプレビューの名前でリリースされていた、Azure Data Studio は、Intellisense、コード スニペット、ソース管理の統合、および統合ターミナルを最新のエディターのエクスペリエンスを提供します。 これは設計されていますを考慮して、データ プラットフォームのユーザーとでクエリの結果セットとカスタマイズ可能なダッシュ ボードのグラフ作成で構築されました。

**[ダウンロードとインストール [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)**


## <a name="sql-code-editor-with-intellisense"></a>IntelliSense を備えた SQL コード エディター

[!INCLUDE[name-sos](../includes/name-sos-short.md)] コーディング エクスペリエンスを日常的なタスクの複数のタブ ウィンドウ、豊富な SQL エディター、IntelliSense、キーワード補完、コード スニペット、コード ナビゲーション、およびソース管理などの組み込み機能を簡単に、キーボード フォーカスされた最新の SQL を提供しています(Git) を統合します。 オンデマンドでの SQL クエリを実行、表示テキスト、JSON、または Excel として結果を保存します。 データの編集、お気に入りのデータベースの接続を整理し、使い慣れたオブジェクト ブラウジング操作でデータベース オブジェクトを参照します。 SQL エディターを使用する方法については、次を参照してください。[データベース オブジェクトを作成するには、SQL エディターを使用して](tutorial-sql-editor.md)します。

## <a name="smart-sql-code-snippets"></a>スマート SQL コード スニペット

SQL コード スニペットでは、データベース、テーブル、ビュー、ストアド プロシージャ、ユーザー、ログイン、ロールなどを作成し、既存のデータベース オブジェクトを更新する適切な SQL 構文を生成します。 開発やテスト目的で、データベースのコピーをすばやく作成および生成し、実行するスマート スニペットを使用して作成し、スクリプトを挿入します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)] カスタムの SQL コード スニペットを作成する機能を提供します。 詳細についてを参照してください。[コード スニペットを作成および使用](code-snippets.md)します。


## <a name="customizable-server-and-database-dashboards"></a>カスタマイズ可能なサーバーとデータベースのダッシュ ボード

監視し、データベース パフォーマンスのボトルネックを迅速にトラブルシューティングの豊富なカスタマイズ可能なダッシュ ボードを作成します。 洞察のウィジェットとデータベース (およびサーバー) のダッシュ ボードの詳細については、次を参照してください。[サーバーと洞察のウィジェットでのデータベースの管理](insight-widgets.md)します。

## <a name="connection-management-server-groups"></a>接続の管理 (サーバー グループ)

サーバー グループは、サーバーおよびデータベースを使用する接続情報を整理する方法を提供します。 詳細については、次を参照してください。[サーバー グループ](server-groups.md)します。

## <a name="integrated-terminal"></a>統合ターミナル

お気に入りのコマンド ライン ツールを使用して (たとえば、Bash、PowerShell、sqlcmd、bcp、ssh で接続) 内で適切な統合ターミナル ウィンドウで、[!INCLUDE[name-sos](../includes/name-sos-short.md)]ユーザー インターフェイス。 統合ターミナルの詳細については、次を参照してください。[統合ターミナル](integrated-terminal.md)します。

## <a name="extensibility-and-extension-authoring"></a>拡張機能と拡張機能の作成

強化、[!INCLUDE[name-sos](../includes/name-sos-short.md)]基本インストールの機能を拡張することによって発生します。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] 拡張機能を作成するためのサポートだけでなく、データの管理アクティビティの機能拡張ポイントを提供します。

機能拡張の詳細については[!INCLUDE[name-sos](../includes/name-sos-short.md)]を参照してください[Extensibility](extensibility.md)します。
拡張機能を作成する方法については、次を参照してください。[拡張機能作成](extension-authoring.md)です。

## <a name="feature-comparison-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) での機能の比較

**場合は、Azure Data Studio を使用します。**
- MacOS または Linux で実行する必要があります。
- SQL Server 2019 のビッグ データ クラスターに接続します。
- ほとんどの編集、またはクエリの実行時間を費やす
- 結果セットを視覚化してグラフを簡単にする必要があります。
- Sqlcmd または Powershell を使用して、統合ターミナルを使用して、ほとんどの管理タスクを実行することができます。
- ウィザードのエクスペリエンスを最小限に抑える必要があります。
- 詳細な管理を構成する必要はありません。

**場合は、SQL Server Management Studio を使用します。**
- データベース管理タスクのほとんどの時間を費やす
- 管理の詳細な構成を行う
- ユーザー管理、脆弱性評価、セキュリティ機能の構成など、セキュリティの管理を行う
- SQL Server クエリ ストアをレポートの使用します。
- 作成する必要がありますパフォーマンス チューニング アドバイザーとダッシュ ボードの使用
- Dacpac のインポート/エクスポートを行う
- 登録済みサーバーへのアクセスし、Windows 上のサービスに、SQL Server を制御する必要があります。

### <a name="shell"></a>Shell

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|Azure サインイン|はい|はい|
|ダッシュボード|はい||
|拡張機能|はい||
|統合ターミナル|はい||
|オブジェクト エクスプローラー|はい|はい|
|オブジェクト スクリプト作成|はい|はい|
|プロジェクト システム|はい||
|テーブルから選択します|はい|はい|
|ソース コード管理|はい||
|作業ウィンドウ|はい||
|テーマ|はい||
|ダーク モード|はい||
|Azure リソース エクスプ ローラー|[プレビュー]||
|スクリプト生成ウィザード||はい|
|Import\Export DACPAC||はい|
|オブジェクトのプロパティ||はい|
|テーブル デザイナー (Table Designer)||はい|


### <a name="query-editor"></a>クエリ エディター

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|グラフ ビューアー|はい||
|CSV、JSON、XLSX に結果をエクスポートします。|はい||
|IntelliSense|はい|はい|
|スニペット|はい|はい|
|プランを表示します。|[プレビュー]|はい|
|クライアント統計||はい|
|ライブ クエリ統計||はい|
|[クエリ オプション]||はい|
|[結果をファイルに出力]||はい|
|[結果をテキストで表示]||はい|
|空間ビューアー||はい|
|sqlcmd||はい|

### <a name="operating-system-support"></a>オペレーティング システムのサポート

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|Linux|はい||
|macOS|はい||
|Windows|はい|はい|

### <a name="data-engineering"></a>データ エンジニア リング

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|ウィザードの外部テーブルを作成します。|[プレビュー]||
|HDFS の統合|[プレビュー]||
|ノートブック|[プレビュー]||

### <a name="database-administration"></a>データベースの管理

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|バックアップ/復元|はい|はい|
|フラット ファイルのインポート|[プレビュー]|はい|
|SQL エージェント|[プレビュー]|はい|
|SQL Profiler|[プレビュー]|はい|
|Always On||はい|
|Always Encrypted||はい|
|データのコピー ウィザード||はい|
|チューニング アドバイザーのデータ||はい|
|エラー ログの表示||はい|
|メンテナンス プラン||はい|
|マルチ サーバー クエリ||はい|
|ポリシー ベースの管理||はい|
|PolyBase||はい|
|クエリ ストア||はい|
|[登録済みサーバー]||はい|
|のレプリケーション||はい|
|セキュリティの管理||はい|
|Service Broker||はい|
|SQL Mail||はい|
|テンプレート エクスプローラー||はい|
|脆弱性評価||はい|
|XEvent 管理||はい|

## <a name="next-steps"></a>次のステップ

- [ダウンロードとインストール [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)
- [接続し、SQL Server のクエリ](quickstart-sql-server.md)
- [Azure SQL Database 接続およびクエリ](quickstart-sql-database.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]