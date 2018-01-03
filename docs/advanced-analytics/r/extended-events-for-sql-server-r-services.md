---
title: "SQL Server の Machine Learning のサービスの拡張イベント |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/21/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e90e057-aacb-4adc-8da6-64861f4e87df
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b08e48eb6a53d40eefbed2a0503c4f92a10f8e66
ms.sourcegitcommit: ed9335fe62c0c8d94ee87006c6957925d09ee301
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extended-events-for-sql-server-machine-learning-services"></a>SQL Server の Machine Learning のサービスの拡張イベント

SQL Server に関連する操作のトラブルシューティングで使用する拡張イベントのセットを提供する、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]Python または R ジョブを送信するとともに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="sql-server-events-for-machine-learning"></a>機械学習の SQL Server イベント

SQL Server に関するイベントの一覧を表示するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から次のクエリを実行します。

```SQL
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

拡張イベントの使用に関する概要については、次を参照してください。[拡張イベントのツール](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools)です。

> [!TIP]
> SQL Server によって生成される、拡張イベントの新しいを再試行してください[SSMS の XEvent プロファイラー](https://docs.microsoft.com/sql/relational-databases/extended-events/use-the-ssms-xe-profiler)です。 Management Studio のこの新機能の拡張イベントは、ライブ ビューアーが表示されます、小さい関与するレベルを SQL Server のようなプロファイラー トレースよりもします。

## <a name="additional-events-specific-to-machine-learning-components"></a>Machine learning のコンポーネントに固有のイベントの追加

その他の拡張イベントに関連するおよびなど SQL Server Machine Learning のサービスで使用されるコンポーネントの使用可能な[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]、R ランタイムを起動するサテライト プロセスである bxlserver です。 これらの追加拡張イベント、外部プロセスから起動され、ため、外部のユーティリティを使用するとキャプチャする必要があります。

これを行う方法の詳細についてを参照してください、[外部プロセスからイベントを収集](#bkmk_externalevents)です。

##  <a name="bkmk_xeventtable"></a>拡張イベントの表

|イベント|Description|注|  
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
|satellite_data_send_start|データ転送の開始時に発生します。| データ転送は、最初のデータ チャンクを送信する直前に開始します。|  
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
  
###  <a name="bkmk_externalevents"></a>外部プロセスからのイベントの収集

SQL Server の Machine Learning のサービスは、SQL Server プロセスの外部で実行している一部のサービスを開始します。 これらの外部プロセスに関連するイベントをキャプチャするには、するには、イベント トレース構成ファイルを作成し、プロセスの実行可能ファイルと同じディレクトリにファイルを配置します。  
  
+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    スタートパッドに関連するイベントをキャプチャするには、Binn ディレクトリに SQL Server インスタンスの *.config* ファイルを配置します。  既定のインストールでは、これは、次のようになります。

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`」をご覧ください。  
  
+ **BXLServer**は R、Python などの外部のスクリプト言語による SQL 拡張機能をサポートしているサテライト プロセスです。 各外部の言語のインスタンスである BxlServer の個別のインスタンスが起動します。
  
    BXLServer に関連するイベントをキャプチャするには、配置、 *.config* R または Python のインストール ディレクトリ内のファイルです。  既定のインストールでは、これは、次のようになります。
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`です。  

    **Python:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`です。

構成ファイルは、"[name].xevents.xml" の形式を使用した実行可能ファイルと同じ名前にする必要があります。 つまり、次のようにファイルに名前を付ける必要があります。

+ `Launchpad.xevents.xml`
+ `bxlserver.xevents.xml`

構成ファイル自体は、次の形式になります。

```xml
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

+ トレースを構成するのには、編集、*セッション名*プレース ホルダー、ファイル名のプレース ホルダー (`[SessionName].xel`)、およびキャプチャする、たとえば、イベントの名前`[XEvent Name 1]`、 `[XEvent Name 1]`)。  
+ イベント パッケージのタグの任意の数は見えますが、および name 属性が正しい限り収集されます。

### <a name="example-capturing-launchpad-events"></a>例: スタートパッド イベントのキャプチャ

次の例では、スタート パッド サービスのイベント トレースの定義を示します。

```xml
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

+ Binn ディレクトリに SQL Server インスタンスの *.config* ファイルを配置します。
+ このファイルの名前である必要があります`Launchpad.xevents.xml`です。

### <a name="example-capturing-bxlserver-events"></a>例: BXLServer イベントのキャプチャ  

次の例に、BXLServer 実行可能ファイルのイベント トレースの定義を示します。
  
```xml
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

+ BXLServer 実行可能ファイルと同じディレクトリに、*.config* ファイルを配置します。
+ このファイルの名前である必要があります`bxlserver.xevents.xml`です。

## <a name="see-also"></a>参照

[Machine Learning のサービスのカスタム管理 Studio のレポート](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)
