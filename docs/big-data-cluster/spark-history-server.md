---
title: Spark アプリケーションのデバッグ/診断します。
titleSuffix: SQL Server big data clusters
description: Spark History Server を使用して、デバッグおよび SQL Server 2019 ビッグ データ クラスター上で実行されている Spark アプリケーションを診断します。
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cba788fcb61dddce54d8b0c4ad4f2ca87ea0906d
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728397"
---
# <a name="debug-and-diagnose-spark-applications-on-sql-server-big-data-clusters-in-spark-history-server"></a>デバッグと Spark History Server の SQL Server のビッグ データ クラスター上で Spark アプリケーションの診断

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Spark History Server の拡張を使用して、デバッグおよび SQL Server 2019 (プレビュー) のビッグ データ クラスターで Spark アプリケーションを診断する方法のガイダンスを提供します。 これらのデバッグと診断機能は、Spark History Server に組み込まれており、Microsoft を利用しました。 拡張機能には、データ タブと グラフ タブと診断 タブが含まれています。データ タブで、ユーザーは Spark ジョブの入力と出力データを確認できます。 グラフ タブでは、ユーザーは、データ フローをチェックして、ジョブ グラフを再生します。 [診断] タブは、ユーザーはデータ スキュー、時間のずれおよび Executor の利用状況の分析を参照できます。

## <a name="get-access-to-spark-history-server"></a>Spark History Server へのアクセスを取得します。

オープン ソースから、Spark 履歴サーバーのユーザー エクスペリエンスは、情報、ジョブに固有のデータとビッグ データ クラスターのジョブ グラフやデータ フローの対話型の視覚化を含むが強化されています。 

### <a name="open-the-spark-history-server-web-ui-by-url"></a>Spark History Server Web URL で UI を開く
開いている、次の URL を参照して、Spark History Server を交換して`<Ipaddress>`と`<Port>`ビッグ データ クラスター固有の情報。 詳細についてを参照できます。[SQL Server のビッグ データ クラスターをデプロイします。](quickstart-big-data-cluster-deploy.md)

```
https://<Ipaddress>:<Port>/gateway/default/sparkhistory
```

Spark History Server web UI をようになります。

![Spark History Server](./media/apache-azure-spark-history-server/spark-history-server.png)


## <a name="data-tab-in-spark-history-server"></a>Spark History Server では、[データ] タブ
ジョブ ID を選択し、クリックして**データ**ツール メニューの データ ビューを取得します。

+ チェック、**入力**、**出力**と**テーブル操作**を個別にタブを選択します。

    ![Spark History Server のデータ タブ](./media/apache-azure-spark-history-server/sparkui-data-tabs.png)

+ ボタンをクリックしてすべての行をコピー**コピー**します。

    ![すべての行をコピーします。](./media/apache-azure-spark-history-server/sparkui-data-copy.png)

+ ボタンをクリックして、すべてのデータを CSV ファイルとして保存**csv**します。

    ![データを CSV ファイルとして保存します。](./media/apache-azure-spark-history-server/sparkui-data-save.png)

+ フィールドにキーワードを入力して検索**検索**、検索結果がすぐに表示されます。

    ![キーワードを使用した検索します。](./media/apache-azure-spark-history-server/sparkui-data-search.png)

+ テーブルを並べ替え、詳細については、表示する行を展開するプラス記号をクリックします。 または行を折りたたむにマイナス記号をクリックします。 列ヘッダーをクリックします。

    ![データ テーブルの機能](./media/apache-azure-spark-history-server/sparkui-data-table.png)

+ ボタンをクリックして、1 つのファイルをダウンロード**部分的なダウンロード**選択したファイルがローカルの場所にダウンロードし、右側にある配置します。 ファイルがこれ以上存在しない場合、エラー メッセージを表示する新しいタブが開きます。

    ![データ行をダウンロードします。](./media/apache-azure-spark-history-server/sparkui-data-download-row.png)

+ 完全なパスまたは相対パスを選択してコピー、**完全パスのコピー**、**相対パスのコピー**ダウンロード メニューを展開します。 Azure data lake ストレージのファイルの**Azure ストレージ エクスプ ローラーで開く**が Azure Storage Explorer を起動します。 サインインするときに、正確なフォルダーを探します。

    ![完全なまたは相対パスをコピーします。](./media/apache-azure-spark-history-server/sparkui-data-copy-path.png)

+ 1 つのページに表示する行多くをテーブルの下に移動の数がすぎるときにページをクリックします。 

    ![[データ] ページ](./media/apache-azure-spark-history-server/sparkui-data-page.png)

+ ポイントすると、ツールヒントを表示するデータの横にある疑問符または詳細情報を取得するには、疑問符をクリックします。

    ![データの詳細](./media/apache-azure-spark-history-server/sparkui-data-more-info.png)

+ クリックすると、問題とフィードバックを送信**フィードバックをお寄せ**します。

    ![グラフのフィードバック](./media/apache-azure-spark-history-server/sparkui-graph-feedback.png)

## <a name="graph-tab-in-spark-history-server"></a>Spark History Server の [グラフ] タブ

ジョブ ID を選択し、クリックして**グラフ**[ツール] メニュー、ジョブ グラフ ビューを取得します。

+ 生成されたジョブのグラフで、ジョブの概要を確認します。 

+ 既定ではすべてのジョブを表示して、によってフィルタ処理できます**ジョブ ID**します。

    ![グラフのジョブ ID](./media/apache-azure-spark-history-server/sparkui-graph-jobid.png)

+ まま**進行状況**既定値として。 ユーザーが選択してデータ フローを確認できます**読み取り**または * * のドロップダウン リストで Written ***表示**します。

    ![グラフの表示](./media/apache-azure-spark-history-server/sparkui-graph-display.png)

    グラフ ノードの表示、ヒートマップを表示する色。

    ![グラフのヒートマップ](./media/apache-azure-spark-history-server/sparkui-graph-heatmap.png)

+ クリックして、ジョブを再生、**再生**ボタンをクリックし、[停止] ボタンをクリックして、いつでも停止できます。 タスクの表示を再生するときに、別の状態を表示する色。

    + 緑色は成功しました。ジョブが正常に完了しました。
    + オレンジ色の再試行。ジョブの最終結果には影響しません、失敗したタスクのインスタンス。 これらのタスクが重複していますか、後で成功する可能性がある再試行インスタンス。
    + 青の実行:タスクが実行されています。
    + 待機中の場合は白またはスキップします。実行するには、タスクが待機しているまたはステージがスキップされます。
    + 赤が失敗しました。タスクが失敗しました。

    ![グラフの色のサンプルを実行しています。](./media/apache-azure-spark-history-server/sparkui-graph-color-running.png)
 
    白色のステージをスキップした表示します。
    ![色のサンプルのグラフをスキップ](./media/apache-azure-spark-history-server/sparkui-graph-color-skip.png)

    ![グラフの色のサンプル、失敗しました](./media/apache-azure-spark-history-server/sparkui-graph-color-failed.png)
 
    > [!NOTE]
    > 各ジョブの再生が許可されます。 ジョブが不完全で、再生はサポートされていません。


+ マウス スクロール入力/出力、ジョブ グラフをズームまたはをクリックして**に合わせてズーム**画面に合わせるようにします。
 
    ![合わせてグラフのズーム](./media/apache-azure-spark-history-server/sparkui-graph-zoom2fit.png)

+ ツールヒントがある場合に失敗したタスク、表示するグラフのノードをポイントし、登壇ステージのページを開く をクリックします。

    ![グラフのツールヒント](./media/apache-azure-spark-history-server/sparkui-graph-tooltip.png)

+ ツールヒントとタスクを満たしている場合に表示される小さいアイコン ジョブ グラフ タブの段階になります、条件の下。
    + データ スキュー: データの読み込みサイズ > 平均データ読み取りのこのステージ内のすべてのタスクのサイズ * > 10 MB のサイズを 2 とデータの読み取り
    + 時間のずれ: 実行時間 > この段階内のすべてのタスクの平均実行時間 * 2 と実行時間 > 2 分

    ![グラフの傾斜アイコン](./media/apache-azure-spark-history-server/sparkui-graph-skew-icon.png)

+ ジョブ グラフのノードの各段階の次の情報が表示されます。
    + ID。
    + 名前または説明します。
    + 合計タスク数。
    + 読み取られたデータ: 入力サイズ、および shuffle の合計サイズの読み取り。
    + データの書き込み: 出力のサイズとシャッフルの合計サイズを記述します。
    + 実行時間: 開始時刻、最初の試行と前回の試行の完了時間までの時間。
    + 行数: 入力のレコードの合計レコードを出力、シャッフル読み取りレコードおよびレコードの書き込みをシャッフルします。
    + 進行状況。

    > [!NOTE]
    > 既定では、ジョブ グラフのノード (ステージの実行時間) を除く各ステージの前回の試行からの情報が表示されますが、グラフの再生中には、ノードによって各試行の情報が表示されます。

    > [!NOTE]
    > 読み取りと書き込みを使用して 1 のデータ サイズの MB = 1000 KB = 1000 * 1000 バイトです。

+ クリックすると、問題とフィードバックを送信**フィードバックをお寄せ**します。

    ![グラフのフィードバック](./media/apache-azure-spark-history-server/sparkui-graph-feedback.png)


## <a name="diagnosis-tab-in-spark-history-server"></a>Spark History Server での診断 タブ
ジョブ ID を選択し、クリックして**診断**[ツール] メニュー、ジョブの診断ビューを取得します。 診断タブが含まれています**データ スキュー**、**時間のずれ**、および**Executor の利用状況分析**します。
    
+ 確認、**データ スキュー**、**時間のずれ**と**Executor の利用状況分析**をそれぞれのタブを選択します。

    ![診断タブ](./media/apache-azure-spark-history-server/sparkui-diagnosis-tabs.png)

### <a name="data-skew"></a>データ スキュー
をクリックして**データ スキュー**タブの対応する指定されたパラメーターに基づいて傾斜したタスクが表示されます。 

+ **パラメーターを指定する**-最初のセクションには、データ スキューを検出するために使用されると、パラメーターが表示されます。 組み込みの規則は次のとおりです。読み取られたタスク データが読み取られる、タスクの平均データの 3 回より大きいと、読み取られたタスク データは 10 MB を超える。 傾斜したタスクの独自の規則を定義する場合、パラメーターを選択できます、**傾斜したステージ**、および**Char 傾斜**セクションはそれに応じて更新されます。 

+ **ステージの傾斜**-2 番目のセクションには、ステージで、上記で指定した条件を満たすタスクが傾斜が表示されます。 ステージに 1 つ以上の傾斜したタスクがある場合、傾斜したステージ テーブルには最も傾斜タスク (たとえば、データ傾斜の最大データ) のみが表示されます。 

    ![データ スキュー セクション 2](./media/apache-azure-spark-history-server/sparkui-diagnosis-dataskew-section2.png)

+ **グラフの傾斜**- 傾斜ステージ テーブルの行を選択すると、タスクのディストリビューションの詳細は、データの読み取りと実行時間に基づくスキューのグラフが表示されます。 傾斜のタスクが赤でマークされているされ、通常のタスクは、青色でマークされます。 パフォーマンスの考慮事項に関するグラフには、最大 100 個のサンプル タスクのみが表示されます。 右下のパネルには、タスクの詳細が表示されます。

    ![データ スキューの 3 番目のセクション](./media/apache-azure-spark-history-server/sparkui-diagnosis-dataskew-section3.png)

### <a name="time-skew"></a>時間のずれ
**時間のずれ** タブには、タスクの実行時間に基づく傾斜のタスクが表示されます。 

+ **パラメーターを指定する**-最初のセクションには、時間のずれを検出するために使用されると、パラメーターが表示されます。 時間のずれを検出するために既定の条件が: タスクの実行時間が 3 回の平均実行時間よりも大きいと、タスクの実行時間が 30 秒より大きい。 ニーズに基づいたパラメーターを変更することができます。 **傾斜したステージ**と**グラフの傾斜**と同じように、対応するステージとタスクの情報を表示、**データ スキュー**上記 タブ。

+ をクリックして**時間のずれ**、フィルター処理された結果は表示**傾斜したステージ**セクションで設定したパラメーターに従ってセクション**パラメーターの指定**。 1 つの項目をクリックします。**傾斜したステージ**セクションで、対応するグラフが 3 番目のセクション、ドラフトとタスクの詳細が右下のパネルに表示されます。

    ![時間のずれセクション 2](./media/apache-azure-spark-history-server/sparkui-diagnosis-timeskew-section2.png)

### <a name="executor-usage-analysis"></a>実行プログラムの利用状況分析
実行プログラムの使用状況グラフは、Spark ジョブの実際の実行プログラムの割り当てと実行状態を視覚化します。  

+ クリックして**Executor の利用状況分析**executor の使用状況に関する次の 4 つの型曲線をドラフトいますし。 含まれている**割り当てられている Executor**、**実行プログラムを実行している**、 **Executor をアイドル**、および**Executor インスタンスの最大**します。 割り当てられている executor は、に関する各「実行プログラムの追加」または「実行プログラムが削除済み」のイベントが向上または低下 executor を割り当てられています。 「イベントのタイムライン」は、比較の詳細については、[ジョブ] タブで確認できます。

    ![Executor タブ](./media/apache-azure-spark-history-server/sparkui-diagnosis-executors.png)

+ 選択するか、すべての下書きの対応するコンテンツの選択を解除する色のアイコンをクリックします。

    ![グラフを選択します。](./media/apache-azure-spark-history-server/sparkui-diagnosis-select-chart.png)


## <a name="known-issues"></a>既知の問題
Spark History Server では、次の既知の問題があります。

+ 現時点でのみ動作 2.3 の Spark クラスター。

+ RDD を使用して入力/出力データは、[データ] タブでは表示されません。

## <a name="next-steps"></a>次の手順

* [HDInsight の Spark クラスターのリソースを管理します。](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-resource-manager)
* [Spark の設定を構成します。](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-settings)
