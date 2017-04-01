---
title: "SQL Server R Services の拡張イベント | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e90e057-aacb-4adc-8da6-64861f4e87df
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# SQL Server R Services の拡張イベント
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 関連する操作のトラブルシューティングで使用する拡張イベントのセットを提供、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] に R のジョブが送信または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
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

  
##  <a name="a-namebkmkxeventtablea-table-of-extended-events"></a><a name="bkmk_xeventtable"></a> 拡張イベントのテーブル  
  
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
|satellite_data_chunk_sent|サテライト接続が 1 つのデータ チャンクの送信を完了したときに発生します。|イベントが送信されると、SNI パケット usedm の数の列数の行の数を報告しの経過時間 (ミリ秒)、チャンクを送信中にします。 情報は、どれ時間だけがかかったの受け渡しの異なる種類のデータ、およびパケットの数を使用するのに役立ちます。|  
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
  
###  <a name="a-namebkmkexternaleventsa-collecting-events-from-external-processes"></a><a name="bkmk_externalevents"></a> 外部プロセスからイベントの収集  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] SQL Server プロセスの外部で実行されているいくつかのサービスを開始します。 これらの外部プロセスに関連するイベントをキャプチャするには、イベント トレース構成ファイルを作成し、プロセスの実行可能ファイルと同じディレクトリにこのファイルを配置する必要があります。  
  
-   **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
     スタート パッドに関連するイベントをキャプチャするには、配置、 *.config* SQL Server インスタンスの Binn ディレクトリにファイルです。  は、既定のインストール:   `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`です。  
  
-   **BXLServer** SQL 拡張性の R とその他の外部のスクリプト言語をサポートするサテライト プロセスです。  
  
     BXLServer に関連するイベントをキャプチャするには、配置、 *.config* R のインストール ディレクトリ内のファイルです。  は、既定のインストール:   `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`です。  
  
> [!IMPORTANT]   構成ファイルは、"[name].xevents.xml" の形式を使用した実行可能ファイルと同じ名前にする必要があります。 つまり、次のようにファイルに名前を付ける必要があります。  
>   
> - Launchpad.xevents.xml  
> - bxlserver.xevents.xml  
  
 構成ファイル自体は、次の形式になります。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
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
  
 **注意:**  
  
-   トレースを構成するのには、編集、 *セッション名* プレース ホルダーをファイル名のプレース ホルダー (`[SessionName].xel`)、およびキャプチャするイベントの名前 (など `[XEvent Name 1]`, 、`[XEvent Name 1]`)。  
  
-   任意の数の `event package` タグは見えますが、および name 属性が適切に収集します。  
  
### <a name="example-capturing-launchpad-events"></a>例: スタートパッド イベントのキャプチャ  
 次の例に、スタートパッド サービスのイベント トレースの定義を示します。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
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
  
 **注意:**  
  
-   場所、 *.config* SQL Server インスタンスの Binn ディレクトリにファイルです。  
  
-   このファイルには、 *Launchpad.xevents.xml*という名前を付ける必要があります。  
  
### <a name="example-capturing-bxlserver-events"></a>例: BXLServer イベントのキャプチャ  
 次の例に、BXLServer 実行可能ファイルのイベント トレースの定義を示します。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
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
  
 **注意:**  
  
-   場所、 *.config* BXLServer 実行可能ファイルと同じディレクトリ内のファイルです。  
  
-   このファイルには、 *bxlserver.xevents.xml*という名前を付ける必要があります。  
  
## <a name="see-also"></a>参照
[R のサービスのカスタム管理 Studio のレポート](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md)  
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [管理と監視 R ソリューション](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  