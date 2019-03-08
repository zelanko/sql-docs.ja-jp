---
title: Azure Data Studio での Spark ジョブを実行します。
titleSuffix: SQL Server 2019 big data clusters
description: Azure Data Studio で SQL Server のビッグ データ クラスターで Spark ジョブを送信します。
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c1d439c13b06b305c814813eeca7cb9bf8aa53c5
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2019
ms.locfileid: "57578242"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Azure Data Studio での SQL Server のビッグ データ クラスターで Spark ジョブを送信します。

ビッグ データ クラスターの主なシナリオの 1 つは、SQL Server 2019 プレビューの Spark ジョブを送信する機能です。 Spark ジョブの送信機能では、SQL Server 2019 ビッグ データ クラスターへの参照を含むローカル Jar、Py ファイルを送信できます。 HDFS ファイル システムに既にあるは、Jar または Py のファイルを実行することもできます。 

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 ビッグ データ ツール](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **kubectl**

- [ビッグ データ クラスターの HDFS/Spark ゲートウェイに接続して Azure Data Studio](connect-to-big-data-cluster.md)します。

## <a name="open-spark-job-submission-dialog"></a>Spark ジョブの送信 ダイアログを開きます
Spark ジョブの送信 ダイアログを開くのいくつかの方法はあります。 方法には、ダッシュ ボードで、オブジェクト エクスプ ローラー、およびコマンド Palate のコンテキスト メニューが含まれます。

+ をクリックして**Spark ジョブを新しい**ダッシュ ボードを Spark ジョブの送信ダイアログを開きます。

    ![ダッシュ ボードをクリックしてメニューを送信します。](./media/submit-spark-job/new-spark-job.png)
 
+ オブジェクト エクスプ ローラーで、クラスターを右クリックし、選択**Submit Spark Job**コンテキスト メニュー。 Spark ジョブの送信ダイアログが開きます。  
 
    ![クラスターを右クリックしてメニューを送信します。](./media/submit-spark-job/submit-spark-job.png)

+ オブジェクト エクスプ ローラー/Py Jar ファイルを右クリックし、選択**Submit Spark Job**コンテキスト メニュー。 あらかじめ Jar/Py フィールドで Spark ジョブの送信ダイアログが開きます。 
 
    ![ファイルを右クリックしてメニューを送信します。](./media/submit-spark-job/submit-spark-job-2.png)

+ コマンドを使用して**Submit Spark Job** (Windows) で Ctrl + Shift + P と Cmd + Shift + P (Mac) で入力してコマンド パレットから。

    ![Windows でのメニュー コマンド パレットを送信します。](./media/submit-spark-job/submit-spark-job-3.png)

    ![Mac でのメニュー コマンド パレットを送信します。](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Spark ジョブを送信します。 
Spark ジョブの送信ダイアログは、次のように表示されます。 ジョブ名、JAR/Py ファイル パス、メイン クラスは、およびその他のフィールドを入力します。 Jar ファイル]、[ローカル コンピューターから、または HDFS から Py ファイル ソース可能性があります。 ジョブには、Spark Jar、Py ファイルまたは追加のファイルを参照する場合はクリックして **[詳細設定]** タブし、対応するファイルのパスを入力します。 クリックして**送信**Spark ジョブを送信します。
 
![新しい spark ジョブ ダイアログ ボックス](./media/submit-spark-job/submit-spark-job-section.png)

![詳細設定 ダイアログ](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Spark ジョブの送信を監視します。
Spark ジョブを送信すると、左側のタスクの履歴で Spark ジョブの送信と実行の状態情報が表示されます。 進行状況とログの詳細についてはでも表示されます、**出力**下部のウィンドウ。
+ Spark ジョブが進行中、ときに、**タスク履歴**パネルと**出力**ウィンドウは、進行状況を更新します。

![進行中の spark ジョブの監視](./media/submit-spark-job/monitor-spark-job-submission.png)

+ Spark ジョブの場合で正常に完了することができますリンクを参照して Spark UI と Yarn UI で、**出力**ウィンドウ。 詳細については、リンクをクリックすることができます。

![出力で Spark ジョブのリンク](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>次のステップ
SQL Server のビッグ データ クラスターと関連するシナリオの詳細については、次を参照してください。[ビッグ データの SQL Server クラスターを新](big-data-cluster-overview.md)でしょうか。

