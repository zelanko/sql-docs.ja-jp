---
title: "ALTER EVENT SESSION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EVENT SESSION
- ALTER_EVENT_SESSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- extended events [SQL Server], Transact-SQL
- ALTER EVENT SESSION statement
ms.assetid: da006ac9-f914-4995-a2fb-25b5d971cd90
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 593be40520403888b5ad2584515820f1935bb270
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-event-session-transact-sql"></a>ALTER EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  イベント セッションの開始および停止、またはイベント セッションの構成変更を行います。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER EVENT SESSION event_session_name  
ON SERVER  
{  
    [ [ {  <add_drop_event> [ ,...n] }     
       | { <add_drop_event_target> [ ,...n ] } ]   
    [ WITH ( <event_session_options> [ ,...n ] ) ]  
    ]  
    | [ STATE = { START | STOP } ]  
}  
  
<add_drop_event>::=  
{  
    [ ADD EVENT <event_specifier>   
         [ ( {   
                 [ SET { event_customizable_attribute = <value> [ ,...n ] } ]  
                 [ ACTION ( { [event_module_guid].event_package_name.action_name [ ,...n ] } ) ]  
                 [ WHERE <predicate_expression> ]  
        } ) ]  
   ]   
   | DROP EVENT <event_specifier> }  
  
<event_specifier> ::=  
{  
[event_module_guid].event_package_name.event_name  
}  
  
<predicate_expression> ::=   
{  
    [ NOT ] <predicate_factor> | {( <predicate_expression> ) }   
    [ { AND | OR } [ NOT ] { <predicate_factor> | ( <predicate_expression> ) } ]   
    [ ,...n ]  
}  
  
<predicate_factor>::=   
{  
    <predicate_leaf> | ( <predicate_expression> )  
}  
  
<predicate_leaf>::=  
{  
      <predicate_source_declaration> { = | < > | ! = | > | > = | < | < = } <value>   
    | [event_module_guid].event_package_name.predicate_compare_name ( <predicate_source_declaration>, <value> )   
}  
  
<predicate_source_declaration>::=   
{  
    event_field_name | ( [event_module_guid].event_package_name.predicate_source_name )  
}  
  
<value>::=   
{  
    number | 'string'  
}  
  
<add_drop_event_target>::=  
{  
    ADD TARGET <event_target_specifier>  
        [ ( SET { target_parameter_name = <value> [ ,...n] } ) ]  
    | DROP TARGET <event_target_specifier>  
}  
  
<event_target_specifier>::=  
{  
    [event_module_guid].event_package_name.target_name  
}  
  
<event_session_options>::=  
{  
    [    MAX_MEMORY = size [ KB | MB] ]  
    [ [,] EVENT_RETENTION_MODE = { ALLOW_SINGLE_EVENT_LOSS | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS } ]  
    [ [,] MAX_DISPATCH_LATENCY = { seconds SECONDS | INFINITE } ]  
    [ [,] MAX_EVENT_SIZE = size [ KB | MB ] ]  
    [ [,] MEMORY_PARTITION_MODE = { NONE | PER_NODE | PER_CPU } ]  
    [ [,] TRACK_CAUSALITY = { ON | OFF } ]  
    [ [,] STARTUP_STATE = { ON | OFF } ]  
}  
```  
  
## <a name="arguments"></a>引数  
  
|||  
|-|-|  
|項目|定義|  
|*event_session_name*|既存のイベント セッションの名前を指定します。|  
|状態 = スタート &#124;です。停止|イベント セッションを開始または停止します。 この引数は、ALTER EVENT SESSION がイベント セッション オブジェクトに適用されたときだけ有効です。|  
|イベントの追加\<event_specifier >|によって識別されるイベントを関連付ける\<event_specifier > イベント セッションにします。|
|[*event_module_guid*]*event_package_name.event_name。*|イベント パッケージ内のイベントを指定します。<br /><br /> -   *event_module_guid*イベントを含むモジュールの GUID です。<br />-   *event_package_name*アクション オブジェクトを含むパッケージです。<br />-   *event_name*イベント オブジェクトです。<br /><br /> イベントは、object_type 'event' として sys.dm_xe_objects ビューに表示されます。|  
|設定 { *event_customizable_attribute*= \<値 > [,...*n*] }|カスタマイズ可能なイベントの属性を指定します。 Sys.dm_xe_object_columns ビューに表示されるカスタマイズ可能な属性としては、column_type 'customizable' および object_name = *event_name*です。|  
|アクション ({[*event_module_guid*]*. event_package_name.action_name* [ **、**.*n*] } )|イベント セッションに関連付けるアクションを指定します。<br /><br /> -   *event_module_guid*イベントを含むモジュールの GUID です。<br />-   *event_package_name*アクション オブジェクトを含むパッケージです。<br />-   *action_name*アクション オブジェクトです。<br /><br /> アクションは、object_type 'action' として sys.dm_xe_objects ビューに表示されます。|  
|ここで\<predicate_expression >|イベントを処理する必要がありますを決定するために使用する述語式を指定します。 場合\<predicate_expression > が true の場合、イベントの処理アクションおよびセッションのターゲットによって、さらにします。 場合\<predicate_expression > が false の場合、イベントは、セッションのアクションおよびターゲットによって処理される前にセッションによって削除されます。 述語式は 3,000 文字に制限され、これにより文字列引数が制限されます。|
|*event_field_name*|述語ソースを識別するイベント フィールドの名前を指定します。|  
|[event_module_guid].event_package_name.predicate_source_name|グローバル述語ソースの名前を指定します。<br /><br /> -   *event_module_guid*イベントを含むモジュールの GUID です。<br />-   *event_package_name*述語オブジェクトを含むパッケージです。<br />-   *predicate_source_name* object_type 'pred_source' として sys.dm_xe_objects ビューに定義されています。|  
|[*event_module_guid*] です。*event_package_name*.*predicate_compare_name*|イベントに関連付ける述語オブジェクトの名前を指定します。<br /><br /> -   *event_module_guid*イベントを含むモジュールの GUID です。<br />-   *event_package_name*述語オブジェクトを含むパッケージです。<br />-   *predicate_compare_name*は、object_type 'pred_compare' として sys.dm_xe_objects ビューに定義されているグローバル ソースです。|  
|DROP EVENT \<event_specifier >|によって識別されるイベントを削除 *\<event_specifier >*です。 \<event_specifier > イベント セッションで有効にする必要があります。|  
|ターゲットの追加\<event_target_specifier >|によって識別されるターゲットを関連付けます\<event_target_specifier > イベント セッションにします。|
|[*event_module_guid*] です。*event_package_name*.*target_name*|イベント セッションのターゲットの名前を指定します。ただし、<br /><br /> -   *event_module_guid*イベントを含むモジュールの GUID です。<br />-   *event_package_name*アクション オブジェクトを含むパッケージです。<br />-   *target_name*アクションです。 アクションは、object_type 'target' として sys.dm_xe_objects ビューに表示されます。|  
|設定 { *target_parameter_name*= \<値 > [,...*n*] }|ターゲット パラメーターを設定します。 Sys.dm_xe_object_columns ビューに表示されるターゲットのパラメーターとしては、column_type 'customizable' および object_name = *target_name*です。<br /><br /> **注:** リング バッファー ターゲットを使用している場合、max_memory ターゲット パラメーターを 2048 KB に設定し、XML 出力のデータの切り捨てを回避することをお勧めします。 ターゲットの種類を使用する場合の詳細については、次を参照してください。 [SQL Server 拡張イベント ターゲット](http://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)です。|  
|ドロップ ターゲット\<event_target_specifier >|によって識別されるターゲットを削除\<event_target_specifier >。 \<event_target_specifier > イベント セッションで有効にする必要があります。|  
|EVENT_RETENTION_MODE = { **ALLOW_SINGLE_EVENT_LOSS** &#124;です。ALLOW_MULTIPLE_EVENT_LOSS &#124;です。NO_EVENT_LOSS}|イベントの削除を処理するために使用するイベント保有モードを指定します。<br /><br /> **ALLOW_SINGLE_EVENT_LOSS**<br /> セッションから単独のイベントを削除できます。 単独のイベントは、すべてのイベント バッファーがいっぱいになったときだけ削除されます。 イベント バッファーがいっぱいになったときに 1 つのイベントが失われる許容可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]処理後のイベント ストリーム内のデータの損失を最小限に抑えながら、パフォーマンスの特性。<br /><br /> ALLOW_MULTIPLE_EVENT_LOSS<br /> 複数のイベントでいっぱいのイベント バッファーをセッションから削除できます。 削除されるイベントの数は、セッションに割り当てられているメモリ サイズ、メモリのパーティション分割、およびバッファー内のイベントのサイズによって異なります。 このオプションを使用すると、イベント バッファーがすぐにいっぱいになるときにサーバーのパフォーマンスに与える影響を最小限に抑えることができますが、多数のイベントがセッションから削除される可能性があります。<br /><br /> NO_EVENT_LOSS<br /> イベントの削除は許可されません。 このオプションは、発生したすべてのイベントを保持することを確認します。 このオプションを使用すると、イベント バッファーに空き領域がするまで待機するイベントを発生させるすべてのタスクが強制します。 その結果、イベント セッションがアクティブになっている間、検知できる程度のパフォーマンスの問題が発生することがあります。 バッファーからイベントがフラッシュされるのを待機する間、ユーザーの接続に遅延が生じる可能性があります。|  
|MAX_DISPATCH_LATENCY = {*秒*秒 &#124;です。**無限**}|イベント セッション ターゲットにディスパッチする前にメモリ内のイベントをバッファリングする時間を指定します。 最小待機値は 1 秒です。 ただし、0 を使用すると、INFINITE 待機を指定できます。 既定では、この値は 30 秒に設定されます。<br /><br /> *秒*(秒)<br /> ターゲットへのバッファーのフラッシュを開始する前に待つ秒数を指定します。 *秒*整数します。<br /><br /> **無限**<br /> バッファーがいっぱいのとき、またはイベント セッションが閉じるときだけ、バッファーをターゲットにフラッシュします。<br /><br /> **注:** MAX_DISPATCH_LATENCY = 0 SECONDS と MAX_DISPATCH_LATENCY = INFINITE は同じです。|  
|MAX_EVENT_SIZE =*サイズ*[サポート技術情報 (&) #124 です。**MB** ]|イベントの最大許容サイズを指定します。 MAX_EVENT_SIZE は、MAX_MEMORY よりも大きな単独のイベントを許可するように設定する必要があります。MAX_MEMORY よりも小さな値を設定した場合はエラーが発生します。 *サイズ*自然数であり、キロバイト (KB) またはメガバイト (MB) の値を指定できます。 場合*サイズ*最小許容サイズは 64 KB をキロバイト単位で指定します。 MAX_EVENT_SIZE 設定されている場合、2 つのバッファーの*サイズ*MAX_MEMORY に加えてが作成されます。 つまり、イベントのバッファリングに使用されるメモリの合計量は MAX_MEMORY + 2 * MAX_EVENT_SIZE となります。|  
|MEMORY_PARTITION_MODE = { **NONE** &#124;です。PER_NODE &#124;です。PER_CPU}|イベント バッファーを作成する場所を指定します。<br /><br /> **NONE**<br /> 内で 1 つのバッファー セットが作成される、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。<br /><br /> 1 つのノードの各 NUMA ノードのバッファー セットが作成されます。<br /><br /> -CPU ごとの CPU ごとのバッファー セットが作成されます。|  
|TRACK_CAUSALITY オプション = {ON (&) #124 です。**OFF** }|因果関係を追跡するかどうかを指定します。 有効な場合、因果関係により、異なるサーバー接続上の関連イベントを一緒に関連付けることができます。|  
|STARTUP_STATE = {ON (&) #124 です。**OFF** }|このイベント セッションを自動的に開始するかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を開始します。<br /><br /> 場合 STARTUP_STATE = ON の場合にのみ、イベント セッションは開始[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は停止し、再起動します。<br /><br /> = イベント セッションは起動時に開始します。<br /><br /> **オフ**= イベント セッションは起動時に開始されません。|  
  
## <a name="remarks"></a>解説  
 ADD 引数と DROP 引数は同じステートメントで一緒に使用できません。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY EVENT SESSION 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、イベント セッションを開始し、いくつかのライブ セッション統計を取得します。次に、既存のセッションに 2 つのイベントを追加します。  
  
```  
-- Start the event session  
ALTER EVENT SESSION test_session  
ON SERVER  
STATE = start;  
GO  
-- Obtain live session statistics   
SELECT * FROM sys.dm_xe_sessions;  
SELECT * FROM sys.dm_xe_session_events;  
GO  
  
-- Add new events to the session  
ALTER EVENT SESSION test_session ON SERVER  
ADD EVENT sqlserver.database_transaction_begin,  
ADD EVENT sqlserver.database_transaction_end;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)   
 [DROP EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-event-session-transact-sql.md)   
 [SQL Server 拡張イベント ターゲット](http://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)   
 [sys.server_event_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)   
 [sys.dm_xe_objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)   
 [sys.dm_xe_object_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)  
  
  
