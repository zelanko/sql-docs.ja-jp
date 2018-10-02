---
title: system_health セッションの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8fd041b5756847abd9f516b98e457b44194be0e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660870"
---
# <a name="use-the-systemhealth-session"></a>system_health セッションの使用
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  system_health セッションは、既定で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に含まれている拡張イベント セッションです。 このセッションは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の起動時に自動的に開始されます。実行中にパフォーマンスに大きな影響が及ぶことはありません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のパフォーマンスの問題をトラブルシューティングするのに役立つシステム データを収集します。 そのため、このセッションを停止または削除しないことをお勧めします。  
  
 このセッションでは、次の情報を収集します。  
  
-   重大度が 20 以上のエラーが発生したすべてのセッションの sql_text と session_id。  
  
-   メモリ関連のエラーが発生したすべてのセッションの sql_text とsession_id。 エラーには、17803、701、802、8645、8651、8657、8902 などがあります。  
  
-   応答していないスケジューラの問題の記録 (これらはエラー 17883 として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに書き込まれます)。  
  
-   検出されたすべてのデッドロック。  
  
-   ラッチ (またはその他の注目する必要があるリソース) での待機時間が 15 秒を超えるすべてのセッションの callstack、sql_text、および session_id。  
  
-   ロックでの待機時間が 30 秒を超えるすべてのセッションの callstack、sql_text、および session_id。  
  
-   プリエンプティブ待機のために長時間待機しているすべてのセッションの callstack、sql_text、および session_id。 待機時間は、待機の種類によって異なります。 プリエンプティブ待機とは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が外部の API 呼び出しを待機している状態です。  
  
-   CLR の割り当てと仮想の割り当ての失敗に対する呼び出し履歴と session_id。  
  
-   メモリ ブローカー、スケジューラ モニター、メモリ ノード OOM、セキュリティ、接続性に関する ring_buffer イベント。  
  
-   sp_server_diagnostics からのシステム コンポーネントの結果。  
  
-   scheduler_monitor_system_health_ring_buffer_recorded によって収集されたインスタンスの正常性。  
  
-   CLR 割り当ての失敗。  
  
-   connectivity_ring_buffer_recorded を使用する接続のエラー。  
  
-   security_error_ring_buffer_recorded を使用するセキュリティのエラー。  
  
## <a name="viewing-the-session-data"></a>セッション データの表示  
 このセッションでは、リング バッファー ターゲットを使用して、データを格納します。 セッション データを表示するには、次のクエリを使用します。  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
イベント ファイルからセッション データを表示するには、Management Studio の拡張イベント ユーザー インターフェイスを使用します。 詳細については、「 [Advanced Viewing of Target Data from Extended Events in SQL Server](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md)」 (SQL Server での拡張イベントからのターゲット データの詳細表示) を参照してください。
  
## <a name="restoring-the-systemhealth-session"></a>system_health セッションの復元  
 system_health セッションを削除した場合、クエリ エディターで **u_tables.sql** ファイルを実行することでそのセッションを復元できます。 このファイルは次のフォルダーにあります (C: は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プログラム ファイルのインストール先ドライブを表しています)。  
  
 C:\Program Files\Microsoft SQL Server\MSSQL13.\<*instanceid*>\MSSQL\Install  
  
 セッションを復元したら、ALTER EVENT SESSION ステートメントを使用するか、オブジェクト エクスプローラーで **[拡張イベント]** ノードを使用して、セッションを開始する必要があります。 ただし、そのようにして開始しない場合でも、次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動したときにセッションは自動的に開始されます。  
  
## <a name="see-also"></a>参照  
 [拡張イベントのツール](../../relational-databases/extended-events/extended-events-tools.md)  
  
  
