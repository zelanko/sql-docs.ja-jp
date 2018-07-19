# 概要

## [SQL Server Machine Learning Services とは](what-is-sql-server-machine-learning.md)
### [データベース内分析](r/sql-server-r-services.md)
### [スタンドアロン サーバー](r/r-server-standalone.md)
## [新しい機能](what-s-new-in-sql-server-machine-learning-services.md)
## [エディション別の機能](r/differences-in-r-features-between-editions-of-sql-server.md)

# [アーキテクチャ](architecture-overview-machine-learning.md)
## [R](r/architecture-overview-sql-server-r.md)
### [R の相互運用性](r/r-interoperability-in-sql-server.md)
### [R 統合を実現するコンポーネント](r/new-components-in-sql-server-to-support-r.md)
### [R のセキュリティ](r/security-overview-sql-server-r.md)
## [Python](python/architecture-overview-sql-server-python.md)
### [Machine Learning Services での Python](python/sql-server-python-services.md)
### [Python の相互運用性](python/python-interoperability.md)
### [Python をサポートするコンポーネント](python/new-components-in-sql-server-to-support-python-integration.md)
### [Python のセキュリティ](python/security-overview-sql-server-python-services.md)
<!-- ### [How To Create a Resource Pool for Python](python/how-to-create-a-resource-pool-for-python.md)-->
<!-- ### [Extended Events for Python](python/extended-events-for-python.md)-->
<!-- ### [DMVs for Python](python/dmvs-for-python.md)-->
<!-- ### [Resource Governance for Python](python/resource-governance-for-python.md)-->

# Install 

## SQL Server 2017
### [データベース内分析](install/sql-machine-learning-services-windows-install.md)
### [スタンドアロン サーバー](install/sql-machine-learning-standalone-windows-install.md)
## SQL Server 2016
### [R Services (データベース内)](install/sql-r-services-windows-install.md)
### [R Server (スタンドアロン)](install/sql-r-standalone-windows-install.md)
## [トレーニング済みモデル](r/install-pretrained-models-sql-server.md)
## [コマンド プロンプトのセットアップ](install/sql-ml-component-commandline-install.md)
## [オフラインのセットアップ (インターネットなし)](install/sql-ml-component-install-without-internet-access.md)
## [R および Python のアップグレード](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
## [R ツールの設定](r/set-up-a-data-science-client.md)
## [Python ツールの設定](python/setup-python-client-tools-sql.md)

# クイック スタート

## R
### [R と SQL での Hello World](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
### [入力と出力の処理](tutorials/rtsql-working-with-inputs-and-outputs.md)
### [データ型とオブジェクトの処理](tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
### [予測モデルの作成](tutorials/rtsql-create-a-predictive-model-r.md)
### [モデルからの予測とプロット](tutorials/rtsql-predict-and-plot-from-model.md)

# [チュートリアル](tutorials/machine-learning-services-tutorials.md)
## [R](tutorials/sql-server-r-tutorials.md)
### [データベース内分析について](tutorials/sqldev-in-database-r-for-sql-developers.md)
#### [1 - データとスクリプトの取得](tutorials/sqldev-download-the-sample-data.md)
#### [2 - 環境の設定](r/sqldev-import-data-to-sql-server-using-powershell.md)
#### [3 - データの視覚化](tutorials/sqldev-explore-and-visualize-the-data.md)
#### [4 - データの機能の作成](tutorials/sqldev-create-data-features-using-t-sql.md)
#### [5 - トレーニングと SQL への保存](r/sqldev-train-and-save-a-model-using-t-sql.md)
#### [6 - 結果の予測](tutorials/sqldev-operationalize-the-model.md)

### [データ サイエンスのエンド ツー エンド チュートリアル](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
#### [データの準備](tutorials/walkthrough-prepare-the-data.md)
#### [SQL を使用したデータの探索](tutorials/walkthrough-view-and-explore-the-data.md)
#### [R を使用したデータの要約](tutorials/walkthrough-view-and-summarize-data-using-r.md)
#### [グラフとプロットの作成](tutorials/walkthrough-create-graphs-and-plots-using-r.md)
#### [データの機能の作成](tutorials/walkthrough-create-data-features.md)
#### [モデルの構築と保存](tutorials/walkthrough-build-and-save-the-model.md)
#### [モデルの配置と使用](tutorials/walkthrough-deploy-and-use-the-model.md)

### [RevoScaleR の詳細情報](tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
#### [データベースとアクセス許可の作成](tutorials/deepdive-work-with-sql-server-data-using-r.md)
#### [RxSqlServerData を使用したデータ オブジェクトの作成](tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
#### [クエリおよびデータの変更](tutorials/deepdive-query-and-modify-the-sql-server-data.md)
#### [コンピューティング コンテキストの定義](tutorials/deepdive-define-and-use-compute-contexts.md)
#### [R スクリプトの作成と実行](tutorials/deepdive-create-and-run-r-scripts.md)
#### [データの視覚化](tutorials/deepdive-visualize-sql-server-data-using-r.md)
#### [モデルを作成する](tutorials/deepdive-create-models.md)
#### [新しいデータのスコア付け](tutorials/deepdive-score-new-data.md)
#### [データの変換](tutorials/deepdive-transform-data-using-r.md)
#### [rxImport を使用してメモリにデータを読み込む](tutorials/deepdive-load-data-into-memory-using-rximport.md)
#### [rxDataStep を使用したテーブルの作成](tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
#### [rxDataStep を使用したチャンク分析の実行](tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
#### [ローカル計算コンテキストでデータを分析する](tutorials/deepdive-analyze-data-in-local-compute-context.md)
#### [SQL Server と XDF ファイル間のデータの移動](tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
#### [簡単なシミュレーションを作成する](tutorials/deepdive-create-a-simple-simulation.md)

## [Python](tutorials/sql-server-python-tutorials.md)
### [T-SQL を使用した Python の実行](tutorials/run-python-using-t-sql.md)
#### [ストアド プロシージャで Python をラップする](tutorials/wrap-python-in-tsql-stored-procedure.md)
#### [SQL Server の Python モデルからトレーニングおよびスコア付けする](tutorials/train-score-using-python-in-tsql.md)
#### [SQL Server の計算コンテキストで revoscalepy を使用してモデルを作成する](tutorials/use-python-revoscalepy-to-create-model.md)
### [データベース内分析について](tutorials/sqldev-in-database-python-for-sql-developers.md)
#### [データとスクリプトの取得](tutorials/sqldev-py1-download-the-sample-data.md)
#### [データのインポート](tutorials/sqldev-py2-import-data-to-sql-server-using-powershell.md)
#### [データの調査と視覚化](tutorials/sqldev-py3-explore-and-visualize-the-data.md)
#### [データの機能の作成](tutorials/sqldev-py4-create-data-features-using-t-sql.md)
#### [モデルのトレーニングと保存](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)
#### [モデルを運用する](tutorials/sqldev-py6-operationalize-the-model.md)

# [サンプル](https://github.com/Microsoft/sql-server-samples)

# [ソリューション](tutorials/data-science-scenarios-and-solution-templates.md)

# [操作方法](r/sql-server-machine-learning-tasks.md)

## パッケージの管理
### [既定のパッケージ](r/installing-and-managing-r-packages.md)
### [パッケージ情報の取得](r/determine-which-packages-are-installed-on-sql-server.md)
### [新しい Python パッケージのインストール](python/install-additional-python-packages-on-sql-server.md)
### [新しい R パッケージのインストール](r/install-additional-r-packages-on-sql-server.md)
#### [R パッケージ マネージャーの使用](r/use-r-package-managers-on-sql-server.md)
#### [T-SQL の使用](r/install-r-packages-tsql.md)
#### [RevoScaleR の使用](r/use-revoscaler-to-manage-r-packages.md)
##### [リモートの R パッケージ管理を有効にする](r/r-package-how-to-enable-or-disable.md)
##### [R パッケージの同期](r/package-install-uninstall-and-sync.md)
#### [miniCRAN リポジトリの作成](r/create-a-local-package-repository-using-minicran.md)
#### [R パッケージを使用するためのヒント](r/packages-installed-in-user-libraries.md)

## データ探索と予測モデリング
### [R ライブラリとデータ型](r/r-libraries-and-data-types.md)
### [Python ライブラリとデータ型](python/python-libraries-and-data-types.md)
### [ネイティブのスコアリング](sql-native-scoring.md)
### [リアルタイム スコアリング](real-time-scoring.md)
### [R を使用した予測モデリング](r/data-exploration-and-predictive-modeling-with-r.md)
### [リアルタイムまたはネイティブのスコアリングを実行する方法](r/how-to-do-realtime-scoring.md)
### [ODBC を使用して R オブジェクトを読み込む](r/save-and-load-r-objects-from-sql-server-using-odbc.md)
### [Machine Learning Services で使用する R コードの変換](r/converting-r-code-for-use-in-sql-server.md)
### [rxExecBy を使用して複数のモデルを作成する](r/creating-multiple-models-using-rxexecby.md)
### [R での OLAP キューブからのデータの使用](r/using-data-from-olap-cubes-in-r.md)
### [sqlrutils を使用してストアド プロシージャを作成する](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## [パフォーマンス]
### [R のパフォーマンス チューニング - 概要](r/sql-server-r-services-performance-tuning.md)
### [R のパフォーマンス チューニング - SQL Server の構成](r/sql-server-configuration-r-services.md)
### [R のパフォーマンス チューニング - R およびデータの最適化](r/r-and-data-optimization-r-services.md)
### [R のパフォーマンス チューニング - 結果](r/performance-case-study-r-services.md)
### [R コード プロファイル関数の使用](r/using-r-code-profiling-functions.md)

## 管理
### [R の構成と管理](r/configuration-sql-server-r-services.md)
### [Machine Learning Services の高度な構成オプション](r/configure-and-manage-advanced-analytics-extensions.md)
### [SQL Server での R ランタイムのセキュリティに関する考慮事項](r/security-considerations-for-the-r-runtime-in-sql-server.md)
### [SQL Server Machine Learning Services のユーザー アカウント プールを変更する](r/modify-the-user-account-pool-for-sql-server-r-services.md)
### [データベース ユーザーとしての SQLRUserGroup の追加](r/add-sqlrusergroup-to-database.md)
### [Web サービスを使用したモデルのデプロイと使用](operationalization-with-mrsdeploy.md)
### [ソリューションの管理および監視](r/managing-and-monitoring-r-solutions.md)
### [Machine Learning Services のリソース管理](r/resource-governance-for-r-services.md)
### [Machine Learning 用のリソース プールの作成](r/how-to-create-a-resource-pool-for-r.md)
### [Machine Learning Services の拡張イベント](r/extended-events-for-sql-server-r-services.md)
### [PREDICT ステートメントを監視するための拡張イベント](xe-event-predict-tsql.md)
### [Machine Learning Services の DMV](r/dmvs-for-sql-server-r-services.md)
### [R コード プロファイル関数の使用](r/using-r-code-profiling-functions.md)
### [Management Studio でカスタム レポートを使用して Machine Learning Services を監視する](r/monitor-r-services-using-custom-reports-in-management-studio.md)

# [パッケージ リファレンス](r/machine-learning-services-r-reference.md)

## [SQL の MicrosoftML](using-the-microsoftml-package.md)
## [SQL の RevoScaleR](r/revoscaler-overview.md)
## [SQL Server データ用の RevoScaleR 関数リスト](r/scaler-functions-for-working-with-sql-server-data.md)
## [SQL の sqlrutils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
## [SQL の olapR](r/how-to-create-mdx-queries-using-olapr.md)
## [SQL の revoscalepy](python/what-is-revoscalepy.md)

# リソース

## [既知の問題](known-issues-for-sql-server-machine-learning-services.md)
## [リリース ノート](https://docs.microsoft.com/sql/sql-server/sql-server-2017-release-notes)
## [仮想マシンをセットアップする](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)
## [トラブルシューティング](machine-learning-troubleshooting-faq.md)
### [データ コレクション](data-collection-ml-troubleshooting-process.md)
### [インストールとアップグレードのエラー](r/upgrade-and-installation-faq-sql-server-r-services.md)
### [スタート パッドや外部スクリプトの実行エラー](common-issues-external-script-execution.md)
### [R スクリプトのエラー](r-script-execution-errors.md)

## ブログ
### [SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/)
### [R Server](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/)
### [Machine Learning](https://blogs.technet.microsoft.com/machinelearning/)

## フォーラム
### [SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/home?category=sqlserver)
### [Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?forum=MicrosoftR)
