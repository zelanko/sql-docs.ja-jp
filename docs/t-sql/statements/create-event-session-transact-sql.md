---
title: "イベント セッション (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EVENT SESSION
- SESSION
- EVENT SESSION
- SESSION_TSQL
- EVENT_SESSION_TSQL
- CREATE_EVENT_SESSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- CREATE EVENT SESSION statement
ms.assetid: 67683027-2b0f-47aa-b223-604731af8b4d
caps.latest.revision: 65
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aaee13bce387e36c1dcb7d26f2dd983b8d36a661
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-event-session-transact-sql"></a>CREATE EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  イベントのソース、イベント セッション ターゲット、およびイベント セッション オプションを識別する拡張イベント セッションを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE EVENT SESSION event_session_name  
ON SERVER  
{  
    <event_definition> [ ,...n]  
    [ <event_target_definition> [ ,...n] ]  
    [ WITH ( <event_session_options> [ ,...n] ) ]  
}  
;  
  
<event_definition>::=  
{  
    ADD EVENT [event_module_guid].event_package_name.event_name   
         [ ( {   
                 [ SET { event_customizable_attribute = <value> [ ,...n] } ]  
                 [ ACTION ( { [event_module_guid].event_package_name.action_name [ ,...n] } ) ]  
                 [ WHERE <predicate_expression> ]  
        } ) ]  
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
  
<event_target_definition>::=  
{  
    ADD TARGET [event_module_guid].event_package_name.target_name  
        [ ( SET { target_parameter_name = <value> [ ,...n] } ) ]  
}  
  
<event_session_options>::=  
{  
    [    MAX_MEMORY = size [ KB | MB ] ]  
    [ [,] EVENT_RETENTION_MODE = { ALLOW_SINGLE_EVENT_LOSS | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS } ]  
    [ [,] MAX_DISPATCH_LATENCY = { seconds SECONDS | INFINITE } ]  
    [ [,] MAX_EVENT_SIZE = size [ KB | MB ] ]  
    [ [,] MEMORY_PARTITION_MODE = { NONE | PER_NODE | PER_CPU } ]  
    [ [,] TRACK_CAUSALITY = { ON | OFF } ]  
    [ [,] STARTUP_STATE = { ON | OFF } ]  
}  
```  
  
## <a name="arguments"></a>引数  
 *event_session_name*  
 イベント セッションのユーザー定義の名前を指定します。 *event_session_name*は、英数字、最大 128 文字を使用できますがのインスタンス内で一意である必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、規則に従う必要がありますと[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 イベントの追加 [ *event_module_guid* ].*event_package_name*.*event_name*  
 イベント セッションに関連付けるイベントを指定します。  
  
-   *event_module_guid*イベントを含むモジュールの GUID です。  
  
-   *event_package_name*アクション オブジェクトを含むパッケージです。  
  
-   *event_name*イベント オブジェクトです。  
  
 イベントは、object_type 'event' として sys.dm_xe_objects ビューに表示されます。  
  
 設定 { *event_customizable_attribute*= \<値 > [,...*n*] }  
 イベントのカスタマイズ可能な属性を設定できます。 Sys.dm_xe_object_columns ビューに表示されるカスタマイズ可能な属性としては、column_type 'customizable' および object_name = *event_name*です。  
  
 アクション ({[*event_module_guid*].*event_package_name*.*action_name* [ **、**.*n*] })  
 イベント セッションに関連付けるアクションを指定します。  
  
-   *event_module_guid*イベントを含むモジュールの GUID です。  
  
-   *event_package_name*アクション オブジェクトを含むパッケージです。  
  
-   *action_name*アクション オブジェクトです。  
  
 アクションは、object_type 'action' として sys.dm_xe_objects ビューに表示されます。  
  
 ここで\<predicate_expression > イベントを処理する必要がありますを決定するために使用する述語式を指定します。 場合\<predicate_expression > が true の場合、イベントの処理アクションおよびセッションのターゲットによって、さらにします。 場合\<predicate_expression > が false の場合、イベントは、セッションのアクションおよびターゲットによって処理される前にセッションによって削除されます。 述語式は 3,000 文字に制限され、これにより文字列引数が制限されます。 
  
 *event_field_name*  
 述語ソースを識別するイベント フィールドの名前を指定します。  
  
 [*event_module_guid*] です。*event_package_name*.*predicate_source_name*  
 グローバル述語ソースの名前を指定します。  
  
-   *event_module_guid*イベントを含むモジュールの GUID です。  
  
-   *event_package_name*述語オブジェクトを含むパッケージです。  
  
-   *predicate_source_name* object_type 'pred_source' として sys.dm_xe_objects ビューに定義されています。  
  
 [*event_module_guid*] です。*event_package_name*.*predicate_compare_name*  
 イベントに関連付ける述語オブジェクトの名前を指定します。  
  
-   *event_module_guid*イベントを含むモジュールの GUID です。  
  
-   *event_package_name*述語オブジェクトを含むパッケージです。  
  
-   *predicate_compare_name*は、object_type 'pred_compare' として sys.dm_xe_objects ビューに定義されているグローバル ソースです。  
  
 *number*  
 任意の数値型を含む**decimal**です。 制限として、使用可能な物理メモリの不足、または 64 ビット整数として表すのに大きすぎる数字が挙げられます。  
  
 '*文字列*'  
 述語の比較に必要な ANSI 文字列または Unicode 文字列です。 述語比較関数に対しては、暗黙の文字列型変換は行われません。 無効な型を渡すとエラーになります。  
  
 ターゲットの追加 [*event_module_guid*].*event_package_name*.*target_name*  
 イベント セッションに関連付けるターゲットを指定します。  
  
-   *event_module_guid*イベントを含むモジュールの GUID です。  
  
-   *event_package_name*アクション オブジェクトを含むパッケージです。  
  
-   *target_name*対象となっています。 ターゲットは、object_type 'target' として sys.dm_xe_objects ビューに表示されます。  
  
 設定 { *target_parameter_name*= \<値 > [,...*n*] }  
 ターゲット パラメーターを設定します。 Sys.dm_xe_object_columns ビューに表示されるターゲットのパラメーターとしては、column_type 'customizable' および object_name = *target_name*です。  
  
> [!IMPORTANT]  
>  リング バッファー ターゲットを使用している場合、max_memory ターゲット パラメーターを 2048 KB に設定し、XML 出力のデータの切り捨てを回避することをお勧めします。 ターゲットの種類を使用する場合の詳細については、次を参照してください。 [SQL Server 拡張イベント ターゲット](http://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)です。  
  
 使用 ( \<event_session_options > [,... *n* ])、イベント セッションで使用するオプションを指定します。  
  
 MAX_MEMORY =*サイズ*[KB |**MB** ]  
 イベントのバッファリング用にセッションに割り当てる最大メモリ容量を指定します。 既定値は、4 MB です。 *サイズ*自然数であり、キロバイト (KB) またはメガバイト (MB) の値を指定できます。  
  
 EVENT_RETENTION_MODE = { **ALLOW_SINGLE_EVENT_LOSS** |ALLOW_MULTIPLE_EVENT_LOSS |NO_EVENT_LOSS}  
 イベントの削除を処理するために使用するイベント保有モードを指定します。  
  
 **ALLOW_SINGLE_EVENT_LOSS**  
 セッションから単独のイベントを削除できます。 単独のイベントは、すべてのイベント バッファーがいっぱいになったときだけ削除されます。 イベント バッファーがいっぱいになったときに 1 つのイベントが失われる許容可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]処理後のイベント ストリーム内のデータの損失を最小限に抑えながら、パフォーマンスの特性。  
  
 ALLOW_MULTIPLE_EVENT_LOSS  
 複数のイベントでいっぱいのイベント バッファーをセッションから削除できます。 削除されるイベントの数は、メモリ、およびバッファー内のイベントのサイズのパーティション分割、セッションに割り当てられたメモリのサイズに依存するようです。 このオプションを使用すると、イベント バッファーがすぐにいっぱいになるときにサーバーのパフォーマンスに与える影響を最小限に抑えることができますが、多数のイベントがセッションから削除される可能性があります。  
  
 NO_EVENT_LOSS  
 イベントの削除は許可されません。 このオプションは、発生したすべてのイベントを保持することを確認します。 このオプションを使用すると、イベント バッファーに空き領域がするまで待機するイベントを発生させるすべてのタスクが強制します。 その結果、イベント セッションがアクティブになっている間、検知できる程度のパフォーマンスの問題が発生することがあります。 バッファーからイベントがフラッシュされるのを待機する間、ユーザーの接続に遅延が生じる可能性があります。  
  
 MAX_DISPATCH_LATENCY = {*秒*秒 |**無限**}  
 イベントをイベント セッション ターゲットにディスパッチする前にメモリにバッファリングする時間を指定します。 既定では、この値は 30 秒に設定されます。  
  
 *秒*(秒)  
 ターゲットへのバッファーのフラッシュを開始する前に待つ秒数を指定します。 *秒*整数します。 最小待機値は 1 秒です。 ただし、0 を使用すると、INFINITE 待機を指定できます。  
  
 **無限**  
 バッファーがいっぱいのとき、またはイベント セッションが閉じるときだけ、バッファーをターゲットにフラッシュします。  
  
> [!NOTE]  
>  MAX_DISPATCH_LATENCY = 0 SECONDS と MAX_DISPATCH_LATENCY = INFINITE は同じです。  
  
 MAX_EVENT_SIZE =*サイズ*[KB |**MB** ]  
 イベントの最大許容サイズを指定します。 MAX_EVENT_SIZE は、MAX_MEMORY よりも大きな単独のイベントを許可するように設定する必要があります。MAX_MEMORY よりも小さな値を設定した場合はエラーが発生します。 *サイズ*自然数であり、キロバイト (KB) またはメガバイト (MB) の値を指定できます。 場合*サイズ*最小許容サイズは 64 KB をキロバイト単位で指定します。 MAX_EVENT_SIZE 設定されている場合、2 つのバッファーの*サイズ*MAX_MEMORY に加えてが作成されます。 つまり、イベントのバッファリングに使用されるメモリの合計量は MAX_MEMORY + 2 * MAX_EVENT_SIZE となります。  
  
 MEMORY_PARTITION_MODE = { **NONE** |PER_NODE |PER_CPU}  
 イベント バッファーを作成する場所を指定します。  
  
 **NONE**  
 内で 1 つのバッファー セットが作成されます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 PER_NODE  
 NUMA ノードごとに 1 つのバッファー セットが作成されます。  
  
 PER_CPU  
 CPU ごとに 1 つのバッファー セットが作成されます。  
  
 TRACK_CAUSALITY オプション = {ON |**OFF** }  
 因果関係を追跡するかどうかを指定します。 有効な場合、因果関係により、異なるサーバー接続上の関連イベントを一緒に関連付けることができます。  
  
 STARTUP_STATE = {ON |**OFF** }  
 このイベント セッションを自動的に開始するかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を開始します。  
  
> [!NOTE]  
>  STARTUP_STATE = ON の場合、イベント セッションは SQL Server が停止後に再起動されたときにだけ開始されます。  
  
 ON  
 起動時にイベント セッションが開始されます。  
  
 **OFF**  
 イベント セッションは起動時に開始されません。  
  
## <a name="remarks"></a>解説  
 論理演算子の優先順位は、高い方から NOT、AND、OR です。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY EVENT SESSION 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、名前付きイベント セッションを作成する方法を示しています。`test_session`です。 この例では、2 つのイベントを追加し、Event Tracing for Windows ターゲットを使用しています。  
  
```  
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='test_session')  
    DROP EVENT session test_session ON SERVER;  
GO  
CREATE EVENT SESSION test_session  
ON SERVER  
    ADD EVENT sqlos.async_io_requested,  
    ADD EVENT sqlserver.lock_acquired  
    ADD TARGET package0.etw_classic_sync_target   
        (SET default_etw_session_logfile_path = N'C:\demo\traces\sqletw.etl' )  
    WITH (MAX_MEMORY=4MB, MAX_EVENT_SIZE=4MB);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [DROP EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-event-session-transact-sql.md)   
 [sys.server_event_sessions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)   
 [sys.dm_xe_objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)   
 [sys.dm_xe_object_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)  
  
  


