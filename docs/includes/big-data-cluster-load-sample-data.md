### <a id="sampledata"></a> サンプル データを読み込む

SQL Server のビッグ データ クラスターのチュートリアルでは、サンプル データの共通セットを使用します。 ビッグ データ クラスター上でサンプル データを構成するのにには、次の手順を使用します。

1. SQL Server コマンド ライン ツールがいないかどうか (**sqlcmd**と**bcp**) リンクのいずれかでこれらのツールをインストール、インストールされている最初に。

   * **Windows**: [Windows 上の SQL Server のインストール コマンド ライン ツール](https://www.microsoft.com/download/details.aspx?id=53591)
   * **Linux**: [Linux 上の SQL Server のインストール コマンド ライン ツール](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-tools)

1. サンプル バックアップ ファイルをダウンロード[tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak)をコンピューターにします。

1. SQL Server 2019 のビッグ データ クラスターに移動します[samples ディレクトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster)します。

1. ダウンロード、[します。 ブートス トラップのサンプル](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql)Transact SQL スクリプト。

1. ダウンロードして、コマンドラインから次の 2 つのサンプル スクリプトのいずれかを実行します。

   * **Windows**:[ブートス トラップのサンプル-db.cmd](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd)
   * **Linux**:[ブートス トラップのサンプル-db.sh](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh)

   > [!TIP]
   > パラメーターなしでスクリプトを実行して、使用法の説明を取得できます。

このスクリプトでは、SQL Server のマスター インスタンスにサンプル データベースを復元しも記憶域プールでの HDFS にデータを読み込みます。