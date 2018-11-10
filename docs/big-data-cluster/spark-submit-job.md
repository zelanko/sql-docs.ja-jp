---
title: Azure Data Studio で SQL Server のビッグ データ クラスターで Spark ジョブの送信します。
description: Azure Data Studio で SQL Server のビッグ データ クラスターで Spark ジョブの送信します。
services: SQL Server 2019 big data cluster spark
ms.service: SQL Server 2019 big data cluster spark
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.custom: ''
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: 4ff29460ade2a3e32f3650d2c2701f22548bdb60
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221608"
---
# <a name="submit-spark-job-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Azure Data Studio で SQL Server のビッグ データ クラスターで Spark ジョブの送信します。

主なシナリオの 1 つは、SQL Server 2019 CTP 2.1 の Spark ジョブを送信する機能です。 Spark ジョブの送信機能では、SQL Server 2019 ビッグ データ クラスターへの参照を含むローカル Jar、Py ファイルを送信できます。 HDFS ファイル システムに既にあるは、Jar または Py のファイルを実行することもできます。 

## <a name="prerequisite"></a>前提条件 
SQL Server のビッグ データ ツールをインストールし、Spark ジョブを送信する前に、ビッグ データ クラスターに接続します。 インストールの詳細については、リンクを参照してください[ビッグ データ ツールの展開](deploy-big-data-tools.md)します。

## <a name="open-spark-job-submission-dialog"></a>Spark ジョブの送信 ダイアログを開きます
Spark ジョブの送信 ダイアログを開くのいくつかの方法はあります。 方法には、ダッシュ ボードで、オブジェクト エクスプ ローラー、およびコマンド Palate のコンテキスト メニューが含まれます。

+ をクリックして**Spark ジョブを新しい**ダッシュ ボードを Spark ジョブの送信ダイアログを開きます。

    ![ダッシュ ボードをクリックしてメニューを送信します。 ](./media/submit-spark-job/new-spark-job.png)
 
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

## <a name="next-steps"></a>次の手順
SQL Server のビッグ データ クラスターと関連するシナリオの詳細については、次を参照してください。[ビッグ データの SQL Server クラスターを新](big-data-cluster-overview.md)でしょうか。

