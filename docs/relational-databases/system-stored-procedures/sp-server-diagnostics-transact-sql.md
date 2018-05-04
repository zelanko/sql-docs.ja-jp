---
title: sp_server_diagnostics (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_server_diagnostics
- sp_server_diagnostics_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_diagnostics
ms.assetid: 62658017-d089-459c-9492-c51e28f60efe
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 13571e7743d8287e0cdff084aede2f524bc91f66
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spserverdiagnostics-transact-sql"></a>sp_server_diagnostics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

潜在的な障害を検出するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に関する診断データと正常性の情報をキャプチャします。 プロシージャは繰り返しモードで実行され、結果は定期的に送信されます。 このプロシージャは、通常の接続または DAC 接続から呼び出すことができます。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_server_diagnostics [@repeat_interval =] 'repeat_interval_in_seconds'   
```  
  
## <a name="arguments"></a>引数  
 [ **@repeat_interval** =] **'***repeat_interval_in_seconds***'**  
 正常性の情報を送信するためにストアド プロシージャが繰り返し実行される期間を示します。  
  
 *repeat_interval_in_seconds*は**int**既定値は 0 です。 有効なパラメーター値は 0、または 5 以上の任意の値です。 完全なデータを返すには、ストアド プロシージャを少なくとも 5 秒間実行する必要があります。 ストアド プロシージャを繰り返しモードで実行するための最小値は 5 秒です。  
  
 このパラメーターが指定されていない場合、または指定した値が 0 の場合、このストアド プロシージャはデータを 1 回返して終了します。  
  
 指定した値が最小値よりも小さい場合、エラーが発生し、データは返されません。  
  
 指定した値が 5 以上の場合、このストアド プロシージャは、手動でキャンセルされるまで繰り返して正常性状態を返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
**sp_server_diagnostics**次の情報を返します  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|**creation_time**|**datetime**|行の作成のタイムスタンプを示します。 単一の行セットの各行は、同じタイムスタンプを持っています。|  
|**component_type**|**sysname**|行の情報を含んでいるかどうかを示す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レベルのコンポーネントまたは Always On 可用性グループのインスタンスします。<br /><br /> インスタンス (instance)<br /><br /> Always On: AvailabilityGroup|  
|**component_name**|**sysname**|コンポーネントの名前または可用性グループの名前を示します。<br /><br /> システム<br /><br /> リソース (resource)<br /><br /> query_processing<br /><br /> io_subsystem<br /><br /> イベント<br /><br /> *\<可用性グループの名前 >*|  
|**状態**|**int**|コンポーネントの正常性状態を示します。<br /><br /> 0<br /><br /> 1<br /><br /> 2<br /><br /> 3|  
|**state_desc**|**sysname**|状態列について説明します。 状態列の値に対応する説明は、次のとおりです。<br /><br /> 0: 不明<br /><br /> 1: クリーン<br /><br /> 2: 警告<br /><br /> 3: エラー|  
|**data**|**varchar (max)**|コンポーネントに固有のデータを指定します。|  
  
 5 つのコンポーネントの説明は以下のとおりです。  
  
-   **システム**: スピンロック、深刻な処理の条件、応答していないタスク、ページ フォールト、および CPU 使用率でシステムの観点からデータを収集します。 この情報から、全体的な正常性状態の推奨設定が生成されます。  
  
-   **リソース**: 物理メモリと仮想メモリ、バッファー プール、ページ、キャッシュ、およびその他のメモリ オブジェクトで、リソースの観点からデータを収集します。 この情報は、全体的なヘルス状態推奨設定を生成します。  
  
-   **query_processing**: クエリの処理の観点から、ワーカー スレッド、タスク、データが収集される待機の種類、CPU 負荷の高いセッション、およびブロックしているタスクです。 この情報は、全体的なヘルス状態推奨設定を生成します。  
  
-   **io_subsystem**: IO でデータを収集します。 このコンポーネントは診断データのほかに、IO サブシステムのみについてクリーンまたは警告の正常性状態を生成します。  
  
-   **イベント**: データを収集してエラーとリング バッファーの例外に関する詳細情報を含む、サーバーによって記録された対象のイベントに、ストアド プロシージャからのサーフェスに関するリング バッファー イベント メモリ ブローカー、スケジューラ モニター、メモリ不足バッファー プール、スピンロック、セキュリティ、および接続します。 イベント状態としては、常に 0 が表示されます。  
  
-   **\<可用性グループの名前 >**: 指定された可用性グループのデータを収集 (場合 component_type ="常に : AvailabilityGroup") です。  
  
## <a name="remarks"></a>解説  
障害の観点からは、system、resource、query_processing の各コンポーネントは障害の検出に利用され、io_subsystem および events コンポーネントは診断目的のみに利用されます。  
  
次の表は、各コンポーネントと関連する正常性状態をマップしたものです。  
  
|Components|クリーン (1)|警告 (2)|エラー (3)|不明 (0)|  
|----------------|-----------------|-------------------|-----------------|--------------------|  
|システム|x|x|x||  
|リソース (resource)|x|x|x||  
|query_processing|x|x|x||  
|io_subsystem|x|x|||  
|イベント||||x|  
  
各行の (x) は、そのコンポーネントに対して有効な正常性状態を表します。 たとえば、io_subsystem はクリーンまたは警告として表示されます。 エラー状態は表示されません。  
 
> [!NOTE]
> Sp_server_diagnostics 内部プロシージャの実行は、優先順位の高いプリエンプティブなスレッドで実装されます。
  
## <a name="permissions"></a>権限  
サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
拡張セッションを使用して正常性の情報をキャプチャし、SQL Server の外部にあるファイルに保存することをお勧めします。 これにより、障害が発生した場合でも正常性の情報にアクセスできます。 次の例は、イベント セッションからの出力をファイルに保存します。  
```sql  
CREATE EVENT SESSION [diag]  
ON SERVER  
           ADD EVENT [sp_server_diagnostics_component_result] (set collect_data=1)  
           ADD TARGET [asynchronous_file_target] (set filename='c:\temp\diag.xel');  
GO  
ALTER EVENT SESSION [diag]  
      ON SERVER STATE = start;  
GO  
```  
  
以下のクエリの例は、拡張セッションのログ ファイルを読み取ります。  
```sql  
SELECT  
    xml_data.value('(/event/@name)[1]','varchar(max)') AS Name  
  , xml_data.value('(/event/@package)[1]', 'varchar(max)') AS Package  
  , xml_data.value('(/event/@timestamp)[1]', 'datetime') AS 'Time'  
  , xml_data.value('(/event/data[@name=''component_type'']/value)[1]','sysname') AS Sysname  
  , xml_data.value('(/event/data[@name=''component_name'']/value)[1]','sysname') AS Component  
  , xml_data.value('(/event/data[@name=''state'']/value)[1]','int') AS State  
  , xml_data.value('(/event/data[@name=''state_desc'']/value)[1]','sysname') AS State_desc  
  , xml_data.query('(/event/data[@name="data"]/value/*)') AS Data  
FROM   
(  
      SELECT  
                        object_name as event  
                        ,CONVERT(xml, event_data) as xml_data  
       FROM    
      sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log\*.xel', NULL, NULL, NULL)  
)   
AS XEventData  
ORDER BY time;  
```  
  
次の例は、sp_server_diagnostics の出力を非繰り返しモードでテーブルにキャプチャします。  
```sql  
CREATE TABLE SpServerDiagnosticsResult  
(  
      create_time DateTime,  
      component_type sysname,  
      component_name sysname,  
      state int,  
      state_desc sysname,  
      data xml  
);  
INSERT INTO SpServerDiagnosticsResult  
EXEC sp_server_diagnostics; 
```  

次のクエリ例では、テーブルから出力の概要を読み取ります。  
```sql  
SELECT create_time,
       component_name,
       state_desc 
FROM SpServerDiagnosticsResult;  
``` 

次のクエリ例では、テーブルの各コンポーネントから詳細な出力の一部を読み取ります。  
```sql  
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult 
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult 
where component_name like 'resource'
go

-- Nonpreemptive waits
select waits.evt.value('(@waitType)','varchar(100)') as 'Wait_Type',
   waits.evt.value('(@waits)','bigint') as 'Waits',
   waits.evt.value('(@averageWaitTime)','bigint') as 'Avg_Wait_Time',
   waits.evt.value('(@maxWaitTime)','bigint') as 'Max_Wait_Time'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/topWaits/nonPreemptive/byDuration/wait') AS waits(evt)
where component_name like 'query_processing'
go

-- Preemptive waits
select waits.evt.value('(@waitType)','varchar(100)') as 'Wait_Type',
   waits.evt.value('(@waits)','bigint') as 'Waits',
   waits.evt.value('(@averageWaitTime)','bigint') as 'Avg_Wait_Time',
   waits.evt.value('(@maxWaitTime)','bigint') as 'Max_Wait_Time'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/topWaits/preemptive/byDuration/wait') AS waits(evt)
where component_name like 'query_processing'
go

-- CPU intensive requests
select cpureq.evt.value('(@sessionId)','bigint') as 'SessionID',
   cpureq.evt.value('(@command)','varchar(100)') as 'Command',
   cpureq.evt.value('(@cpuUtilization)','bigint') as 'CPU_Utilization',
   cpureq.evt.value('(@cpuTimeMs)','bigint') as 'CPU_Time_ms'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/cpuIntensiveRequests/request') AS cpureq(evt)
where component_name like 'query_processing'
go

-- Blocked Process Report
select blk.evt.query('.') as 'Blocked_Process_Report_XML'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/blockingTasks/blocked-process-report') AS blk(evt)
where component_name like 'query_processing'
go

-- IO
select data.value('(/ioSubsystem/@ioLatchTimeouts)[1]','bigint') as 'Latch_Timeouts',
   data.value('(/ioSubsystem/@totalLongIos)[1]','bigint') as 'Total_Long_IOs'
from SpServerDiagnosticsResult 
where component_name like 'io_subsystem'
go

-- Event information
select xevts.evt.value('(@name)','varchar(100)') as 'xEvent_Name',
   xevts.evt.value('(@package)','varchar(100)') as 'Package',
   xevts.evt.value('(@timestamp)','datetime') as 'xEvent_Time',
   xevts.evt.query('.') as 'Event Data'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/events/session/RingBufferTarget/event') AS xevts(evt)
where component_name like 'events'
go  
``` 
  
## <a name="see-also"></a>参照  
 [フェールオーバー クラスター インスタンスのフェールオーバー ポリシー](../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
