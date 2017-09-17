---
title: "拡張イベント ログの診断情報にアクセスする |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79e9468-2257-4536-91f1-73b008c376c3
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e6dfbd857905f0c0f444c44a9c9eb9813cc32ab2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>拡張イベント ログの診断情報へのアクセス」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、トレース ([ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)) が容易にできるように、サーバーの接続リングからの接続エラーなどの診断情報とクライアントのイベントを関連付けるために簡単に更新されました拡張イベント ログでバッファーやアプリケーションのパフォーマンス情報。 拡張イベント ログの読み取り方法の詳細については、次を参照してください。[イベント セッション データの表示](http://msdn.microsoft.com/library/hh710068(SQL.110).aspx)です。  
  
## <a name="details"></a>詳細  
 接続操作で、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]クライアントに送信接続 id。 接続が失敗した場合、接続リング バッファーにアクセスできます ([、接続リング バッファーによる SQL Server 2008 の接続のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=207752)) を見つけて、 **ClientConnectionID**フィールドと接続エラーに関する診断情報を取得します。 クライアント接続 ID は、エラーが発生した場合にのみリング バッファーに記録されます  (ログイン前のパケットを送信する前に接続に失敗した場合、クライアント接続 ID は生成されません)。クライアント接続 ID は 16 バイトの GUID です。 クライアント接続を検索することもできます。 場合、拡張イベント ターゲットの出力に ID、 **client_connection_id**アクションが拡張イベント セッションのイベントに追加します。 トレースを有効にして、接続コマンドを再実行し、観察、 **ClientConnectionID**フィールドに、トレースにさらにクライアント ドライバーの診断サポートが必要な場合です。  
  
 クライアントを取得する接続 ID を使用してプログラムで[ISQLServerConnection インターフェイス](../../connect/jdbc/reference/isqlserverconnection-interface.md)です。 接続 ID は接続関連の例外にも含まれます。  
  
 接続エラーが発生する場合、サーバーの BID トレース情報および接続リング バッファーに含まれるクライアント接続 ID を使用すると、クライアント接続をサーバー上の接続に関連付けることができます。 BID の詳細については、サーバーでトレースを参照してください[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)です。 ただし、データ アクセスのトレースに関する記事には適用されませんデータ アクセスのトレースの実行に関する情報も含まれています、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]; を参照してください[ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)データ アクセス トレースを使用して、その方法についての[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 JDBC Driver からは、スレッド固有のアクティビティ ID も送信されます。 アクティビティ ID は、TRACK_CAUSAILITY オプションを有効にしてセッションを開始した場合、拡張イベント セッションでキャプチャされます。 アクティブな接続に関するパフォーマンスの問題については、クライアントのトレース (ActivityID フィールド) からアクティビティ ID を取得し、このアクティビティ ID を拡張イベント出力で探すことができます。 拡張イベント内のアクティビティ ID とは、16 バイトの GUID (クライアント接続 ID の GUID とは異なる) の後に 4 バイトのシーケンス番号が付いたものです。 このシーケンス番号は、スレッド内の要求順序を表しています。 ActivityId は、SQL バッチ ステートメントおよび RPC 要求用に送信されます。 ActivityId をサーバーに送信できるようにするには、まず Logging.Properties ファイル内で次のキー/値ペアを指定する必要があります。  
  
```  
com.microsoft.sqlserver.jdbc.traceactivity = on  
```  
  
 以外の値のいずれかの`on`(大文字小文字を区別) が、ActivityId の送信を無効になります。  
  
 詳細については、次を参照してください。[ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)です。 このトレース フラグは、JDBC Driver で ActivityId をトレースおよび送信するかどうかを決定するために、対応する JDBC オブジェクト ロガーと共に使用されます。 Logging.Properties ファイルの更新に加えて、ロガー com.microsoft.sqlserver.jdbc を FINER 以上で有効にする必要があります。 特定のクラスによる要求に対してサーバーに ActivityId を送信する場合は、対応するクラス ロガーを FINER または FINEST で有効にする必要があります。 たとえば、クラスが SQLServerStatement であれば、ロガー com.microsoft.sqlserver.jdbc.SQLServerStatement を有効にします。  
  
 使用するサンプルを次に示します[!INCLUDE[tsql](../../includes/tsql_md.md)]RPC とバッチ操作でクライアントから送信するのには、リング バッファーに格納され、アクティビティ ID を記録する拡張イベント セッションを開始します。  
  
```  
create event session MySession on server  
add event connectivity_ring_buffer_recorded,  
add event sql_statement_starting (action (client_connection_id)),  
add event sql_statement_completed (action (client_connection_id)),  
add event rpc_starting (action (client_connection_id)),  
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーに関する問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
