---
title: Analysis Services トレース イベント |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2db55ea54e82b86f32d4bb7ff47dccc68c08fd0
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-trace-events"></a>Analysis Services トレース イベント
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Microsoft SQL Server Analysis Services (SSAS) インスタンスのアクティビティは、インスタンスによって生成されるトレース イベントを取得し、分析することで追跡できます。  トレース イベントは、関連するトレース イベントをより簡単に見つけることができるようにグループ化されます。  各トレース イベントには、イベントに関連するデータのセットが含まれています。データのすべての部分がすべてのイベントに関連するわけではありません。  
  
 トレース イベントは、 **[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]** を使用して開始し、キャプチャすることができます (「 [SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)」を参照)。また、XMLA コマンドから **SQL Server 拡張イベント** として開始し、後で分析することもできます (「 [SQL Server 拡張イベントを使用した Analysis Services の監視](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)」を参照)。  
  
 各イベント カテゴリとそのカテゴリに含まれるイベントを次の表で説明します。 各表には次の列があります。  
  
**イベント ID**  
 イベントの種類を識別する整数値です。 この値は、テーブルまたは XML ファイルに変換されたトレースを読み取ってイベントの種類をフィルター選択する場合に役立ちます。  
  
**イベント名**  
 Analysis Services クライアント アプリケーションでイベントに与えられる名前です。  
  
**イベントの説明**  
 イベントの簡潔な説明です。  
  
 **[Command イベントのイベント カテゴリ](../../analysis-services/trace-events/command-events-event-category.md)**  
  
 コマンドのイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|15|Command Begin|コマンド開始。|  
|16|Command End|コマンド終了。|  
  
 **[Discover イベントのイベント カテゴリ](../../analysis-services/trace-events/discover-events-event-category.md)**  
  
 検出要求のイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|36|Discover Begin|検出要求の開始。|  
|38|Discover End|検出要求の終了。|  
  
 **[サーバー状態検出イベント カテゴリ](../../analysis-services/trace-events/discover-server-state-event-category.md)**  
  
 サーバー状態検出のイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|サーバー状態検出の開始。|  
|34|Server State Discover Data|サーバー状態検出の応答の内容。|  
|35|Server State Discover End|サーバー状態検出の終了。|  
  
 **[エラーと警告イベント カテゴリ](../../analysis-services/trace-events/errors-and-warnings-event-category.md)**  
  
 サーバー エラーのイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|17|エラー|サーバー エラー。|  
  
 **[ファイルの読み込みと保存のイベント カテゴリ](../../analysis-services/trace-events/file-load-and-save-event-category.md)**  
  
 ファイルの読み込みおよび保存操作のレポートのイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|90|ファイルの読み込みの開始|ファイルの読み込みの開始。|  
|91|ファイルの読み込みの終了|ファイルの読み込みの終了。|  
|92|ファイルの保存の開始|ファイルの保存の開始。|  
|93|ファイルの保存の終了|ファイルの保存の終了|  
|94|ページアウトの開始|ページアウトの開始。|  
|95|ページアウトの終了|ページアウトの終了|  
|96|ページインの開始|ページインの開始。|  
|97|ページインの終了|ページインの終了|  
  
 **[ロック イベント カテゴリ](../../analysis-services/trace-events/lock-events-category.md)**  
  
 ロック関連のイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|メタデータ ロックのデッドロック。|  
|51|Lock Timeout|メタデータ ロックのタイムアウト。|  
|52|Lock Acquired|Lock Acquired|  
|53|Lock Released|Lock Released|  
|54|Lock Waiting|Lock Waiting|  
  
 **[Notification イベントのイベント カテゴリ](../../analysis-services/trace-events/notification-events-event-category.md)**  
  
 通知イベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|39|Notification|通知イベント。|  
|40|User Defined|ユーザー定義イベント。|  
  
 **[Progress Reports イベント カテゴリ](../../analysis-services/trace-events/progress-reports-event-category.md)**  
  
 進行状況レポートのイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|進行状況レポートの開始。|  
|6|Progress Report End|進行状況レポートが終了しました。|  
|7|Progress Report Current|進行状況レポートを実行中です。|  
|8|Progress Report Error|進行状況レポート エラーです。|  
  
 **[Queries イベント カテゴリ](../../analysis-services/trace-events/queries-events-category.md)**  
  
 クエリのイベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|クエリ開始。|  
|10|クエリの終了|クエリ終了。|  
  
 **[クエリ処理イベント カテゴリ](../../analysis-services/trace-events/query-processing-events-category.md)**  
  
 クエリ実行のプロセス中の主要イベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|70|Query Cube Begin|キューブのクエリの開始。|  
|71|Query Cube End|キューブのクエリの終了。|  
|72|Calculate Non Empty Begin|空以外の計算の開始。|  
|73|Calculate Non Empty Current|空以外の計算の現在の状態。|  
|74|Calculate Non Empty End|空以外の計算の終了。|  
|75|Serialize Results Begin|結果のシリアル化の開始。|  
|76|Serialize Results Current|結果のシリアル化の現在の状態。|  
|77|Serialize Results End|結果のシリアル化の終了。|  
|78|Execute MDX Script Begin|MDX スクリプトの実行の開始。|  
|79|Execute MDX Script Current|MDX スクリプトの実行の現在の状態。 非推奨。|  
|80|Execute MDX Script End|MDX スクリプトの実行の終了。|  
|81|Query Dimension|クエリ ディメンション。|  
|11|Query Subcube|使用法に基づく最適化用のサブキューブのクエリ。|  
|12|Query Subcube Verbose|詳細情報を指定してサブキューブをクエリします。 このイベントを有効にすると、パフォーマンスが低下する場合があります。|  
|60|Get Data From Aggregation|集計からデータを取得することによってクエリに応答します。 このイベントを有効にすると、パフォーマンスが低下する場合があります。|  
|61|Get Data From Cache|キャッシュの 1 つからデータを取得することによってクエリに応答します。 このイベントを有効にすると、パフォーマンスが低下する場合があります。|  
|82|VertiPaq SE Query Begin|VertiPaq SE クエリ。|  
|83|VertiPaq SE Query End|VertiPaq SE クエリ。|  
|84|Resource Usage|コマンドおよびクエリの終了後のレポートの読み取り、書き込み、CPU 使用率。|  
|85|VertiPaq SE Query Cache Match|VertiPaq SE クエリ キャッシュの使用状況|  
|98|Direct Query Begin|直接クエリの開始。|  
|99|Direct Query End|直接クエリの終了。|  
  
 **[セキュリティ監査イベント カテゴリ](../../analysis-services/trace-events/security-audit-event-category.md)**  
  
 データベース監査イベント クラスのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|1|Audit Login|SQL Server のインスタンスを実行するサーバーへの接続をクライアントが要求したときなど、トレースが開始された後の接続イベントをすべて収集します。|  
|2|Audit Logout|クライアントが切断コマンドを発行したときなど、トレースが開始された後の切断イベントをすべて収集します。|  
|4|Audit Server Starts And Stops|サービスのシャットダウン、起動、一時停止のアクティビティを記録します。|  
|18|Audit Object Permission Event|オブジェクト権限の変更を記録します。|  
|19|Audit Admin Operations Even|サーバーのバックアップ/復元/同期/アタッチ/デタッチ/イメージ読み込み/イメージ保存を記録します。|  
  
 [Session イベントのイベント カテゴリ](../../analysis-services/trace-events/session-events-event-category.md)  
  
 セッション イベントのコレクションです。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|41|Existing Connection|既存のユーザー接続。|  
|42|Existing Session|既存のセッション。|  
|43|Session Initialize|セッションの初期化。|  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
  
