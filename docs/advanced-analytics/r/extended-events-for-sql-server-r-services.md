---
title: "SQL Server R Services の拡張イベント | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e90e057-aacb-4adc-8da6-64861f4e87df
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 814dacf2dbc7f3be05ad163c8c7162acf53fe404
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="extended-events-for-sql-server-r-services"></a>SQL Server R Services の拡張イベント
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に送信される R ジョブに関するトラブルシューティング処理で使用する一連の拡張イベントを提供します。  
  
 SQL Server に関するイベントの一覧を表示するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から次のクエリを実行します。  
  
```  
select o.name as event_name, o.description  
  from sys.dm_xe_objects o  
  join sys.dm_xe_packages p  
    on o.package_guid = p.guid  
 where o.object_type = 'event'  
   and p.name = 'SQLSatellite';  
```  
  
 ただし、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の一部の追加拡張イベントは、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]や R ランタイムを起動するサテライト プロセスである BXLServer などの外部プロセスからのみ起動されます。 これらのイベントをキャプチャする方法の詳細については、「 [Collecting Events from External Processes](#bkmk_externalevents)」を参照してください。  
  
 拡張イベントの一般的な情報については、「 [SQL Server Extended Events Sessions](../../relational-databases/extended-events/sql-server-extended-events-sessions.md)」を参照してください。  

  
##  <a name="bkmk_xeventtable"></a> 拡張イベントの表  
  
|イベント|説明|新しく使用する機能|  
|-----------|-----------------|---------|  
|connection_accept|新しい接続が受け入れられたときに発生します。 このイベントは、すべての接続試行をログに記録するために役立ちます。||  
|failed_launching|起動に失敗しました。|エラーを示します。|  
|satellite_abort_connection|接続の中止レコード||  
|satellite_abort_received|中止メッセージがサテライト接続経由で受信したときに発生します。||  
|satellite_abort_sent|中止メッセージがサテライト接続経由で送信されたときに発生します。||  
|satellite_authentication_completion|TCP または名前付きパイプ経由の接続の認証が完了したときに発生します。||  
|satellite_authorization_completion|TCP または名前付きパイプ経由の接続の承認が完了したときに発生します。||  
|satellite_cleanup|サテライトがクリーンアップを呼び出したときに発生します。|外部プロセスからのみ起動されます。 外部プロセスからイベントを収集する手順を参照してください。|  
|satellite_data_chunk_sent|サテライト接続が 1 つのデータ チャンクの送信を完了したときに発生します。|イベントにより、送信された行数と列数、使用された SNI パケット数、チャンクの送信にかかった時間 (ミリ秒) が報告されます。 この情報は、さまざまな型のデータを渡すためにかかった時間と、使用されたパケット数を理解するのに役立ちます。|  
|satellite_data_receive_completion|サテライト接続経由でクエリに必要なすべてのデータが受信されたときに発生します。|外部プロセスからのみ起動されます。 外部プロセスからイベントを収集する手順を参照してください。|  
|satellite_data_send_completion|サテライト接続経由でセッションに必要なすべてのデータが送信されたときに発生します。||  
|satellite_data_send_start|データ転送の開始時 (最初のデータ チャンクが送信される直前に) に発生します。||  
|satellite_error|Sql サテライト エラーのトレースに使われます||  
|satellite_invalid_sized_message|メッセージのサイズが正しくありません。||  
|satellite_message_coalesced|ネットワーク レイヤーでのメッセージ結合のトレースに使われます||  
|satellite_message_ring_buffer_record|メッセージ リング バッファー レコード||  
|satellite_message_summary|メッセージングに関する概要情報||  
|satellite_message_version_mismatch|メッセージのバージョン フィールドが一致しません||  
|satellite_messaging|メッセージング イベント (バインド、バインド解除など) のトレースに使われます||  
|satellite_partial_message|ネットワーク レイヤーでの部分的なメッセージのトレースに使われます||  
|satellite_schema_received|スキーマ メッセージが受信され、SQL によって読み取られたときに発生します。||  
|satellite_schema_sent|スキーマ メッセージが、サテライトによって送信されたときに発生します。|外部プロセスからのみ起動されます。 外部プロセスからイベントを収集する手順を参照してください。|  
|satellite_service_start_posted|サービス開始メッセージがスタートパッドに投稿されたときに発生します。|これにより、スタートパッドに外部プロセスを起動するように指示し、新しいセッションの ID が含まれます。|  
|satellite_unexpected_message_received|予期しないメッセージを受信したときに発生します。|エラーを示します。|  
|stack_trace|プロセスのメモリ ダンプが要求されたときに発生します。|エラーを示します。|  
|trace_event|トレース目的で使用されます|これらのイベントには、SQL Server、スタートパッド、および外部プロセスのトレース メッセージを含めることができます。 これには、R からの stdout と stderr への出力が含まれます。|  
|launchpad_launch_start|スタートパッドがサテライトの起動を開始したときに発生します。|スタートパッドからのみ起動されます。 launchpad.exe からイベントを収集する手順を参照してください。|  
|launchpad_resume_sent|スタートパッドがサテライトを起動し、再開メッセージを SQL Server に送信したときに発生します。|スタートパッドからのみ起動されます。 launchpad.exe からイベントを収集する手順を参照してください。|  
|satellite_data_chunk_sent|サテライト接続が 1 つのデータ チャンクの送信を完了したときに発生します。|列数、行数、パケット数、チャンクの送信にかかった時間に関する情報を格納します。|  
|satellite_sessionId_mismatch|メッセージのセッション ID が予期されたものではありません||  
  
###  <a name="bkmk_externalevents"></a> Collecting Events from External Processes  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、SQL Server プロセスの外部で実行するいくつかのサービスを開始します。 これらの外部プロセスに関連するイベントをキャプチャするには、イベント トレース構成ファイルを作成し、プロセスの実行可能ファイルと同じディレクトリにこのファイルを配置する必要があります。  
  
-   **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
     スタートパッドに関連するイベントをキャプチャするには、Binn ディレクトリに SQL Server インスタンスの *.config* ファイルを配置します。  既定のインストールでは、これは `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn` です。  
  
-   **BXLServer** は R と他の外部スクリプト言語による SQL 拡張機能をサポートしているサテライト プロセスです。  
  
     BXLServer に関連するイベントをキャプチャするには、R インストール ディレクトリに *.config* ファイルを配置します。  既定のインストールでは、これは `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64` です。  
  
> [!IMPORTANT]
>   構成ファイルは、"[name].xevents.xml" の形式を使用した実行可能ファイルと同じ名前にする必要があります。 つまり、次のようにファイルに名前を付ける必要があります。  
>   
> - Launchpad.xevents.xml  
> - bxlserver.xevents.xml  
  
 構成ファイル自体は、次の形式になります。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **注:**  
  
-   トレースを構成するには、*[session name]* プレースホルダー、ファイル名のプレースホルダー (`[SessionName].xel`)、キャプチャするイベントの名前 (`[XEvent Name 1]`、`[XEvent Name 1]` など) を編集します。  
  
-   任意の数の `event package` タグが含まれることがあり、それらは name 属性が正しい限り収集されます。  
  
### <a name="example-capturing-launchpad-events"></a>例: スタートパッド イベントのキャプチャ  
 次の例に、スタートパッド サービスのイベント トレースの定義を示します。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **注:**  
  
-   Binn ディレクトリに SQL Server インスタンスの *.config* ファイルを配置します。  
  
-   このファイルには、 *Launchpad.xevents.xml*という名前を付ける必要があります。  
  
### <a name="example-capturing-bxlserver-events"></a>例: BXLServer イベントのキャプチャ  
 次の例に、BXLServer 実行可能ファイルのイベント トレースの定義を示します。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **注:**  
  
-   BXLServer 実行可能ファイルと同じディレクトリに、*.config* ファイルを配置します。  
  
-   このファイルには、 *bxlserver.xevents.xml*という名前を付ける必要があります。  
  
## <a name="see-also"></a>参照
[R Services 向けの Management Studio カスタム レポート](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md)  
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [R ソリューションの管理と監視](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  

