---
title: "sp_trace_create (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_trace_create_TSQL
- sp_trace_create
dev_langs: TSQL
helpviewer_keywords: sp_trace_create
ms.assetid: f3a43597-4c5a-4520-bcab-becdbbf81d2e
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ca00a949b0fe0122f6aba9b8fecfa072374e96f3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sptracecreate-transact-sql"></a>sp_trace_create (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トレース定義を作成します。 新しいトレースは停止状態になります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_trace_create [ @traceid = ] trace_id OUTPUT   
          , [ @options = ] option_value   
          , [ @tracefile = ] 'trace_file'   
     [ , [ @maxfilesize = ] max_file_size ]  
     [ , [ @stoptime = ] 'stop_time' ]  
     [ , [ @filecount = ] 'max_rollover_files' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@traceid=** ] *trace_id*  
 によって割り当てられる番号[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しいトレースにします。 ユーザーの入力はすべて無視されます。 *trace_id*は**int**、既定値は NULL です。 ユーザーが使用して、 *trace_id*識別、変更、およびこのストアド プロシージャで定義されているトレースを制御する値。  
  
 [  **@options=** ] *option_value*  
 トレースのオプション セットを指定します。 *option_value*は**int**、既定値はありません。 ユーザーは複数のオプションの組み合わせを選択することもできます。これにはオプションの合計値を指定します。 たとえば、TRACE_FILE_ROLLOVER と SHUTDOWN_ON_ERROR の両方のオプションをオンにする次のように指定します。 **6**の*option_value*です。  
  
 次の表は、オプションとその説明および値の一覧です。  
  
|オプション名|オプション値|Description|  
|-----------------|------------------|-----------------|  
|TRACE_FILE_ROLLOVER|**2**|指定する場合、 *max_file_size*に達すると、現在のトレース ファイルが閉じられ、新しいファイルを作成します。 新しいレコードはすべて新しいファイルに書き込まれます。 新しいファイルの名前は以前のファイルと同じになりますが、その順番を示すため整数が追加されます。 たとえば、元のトレース ファイルの名前が filename.trc の場合、次のトレース ファイルの名前は順に filename_1.trc、filename_2.trc となります。<br /><br /> ロールオーバー トレース ファイルが作成されるたびに、ファイル名に追加される整数値は増加します。<br /><br /> SQL Server の既定値を使用して*max_file_size* (5 MB) の値を指定せず、このオプションが指定されている場合*max_file_size*です。|  
|SHUTDOWN_ON_ERROR|**4**|なんらかの理由によりトレースをファイルに書き込めない場合、SQL Server はシャットダウンします。 このオプションは、セキュリティ監査トレースを実行するときに役立ちます。|  
|TRACE_PRODUCE_BLACKBOX|**8**|サーバーで生成されたトレース情報の末尾にある 5 MB のレコードが、サーバーで保存されます。 TRACE_PRODUCE_BLACKBOX は、他のオプションと同時に指定できません。|  
  
 [  **@tracefile=** ] *'**trace_file**'*  
 トレースを書き込む場所とファイル名を指定します。 *trace_file*は**nvarchar (245)**既定値はありません。 *trace_file* (N 'C:\MSSQL\Trace\trace.trc') などのローカル ディレクトリまたは UNC 共有またはパスのいずれかを指定できます (N'\\\\*Servername*\\*Sharename*\\*ディレクトリ*\trace.trc')。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]追加、 **.trc**すべてのトレース ファイル名に拡張します。 場合、TRACE_FILE_ROLLOVER オプションと*max_file_size*指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]元のトレース ファイルが最大サイズに拡張する場合は、新しいトレース ファイルを作成します。 新しいファイルに同じ名前が、元のファイルは、_ *n* 以降で、その順番を示すために追加された**1**です。 たとえば、最初のトレース ファイルの名前は**filename.trc**、2 番目のトレース ファイルの名前は**filename_1.trc**です。  
  
 TRACE_FILE_ROLLOVER オプションを使用する場合、元のトレース ファイル名にアンダースコア文字を使用しないことをお勧めします。 アンダースコアを使用した場合、次の動作が発生します。  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]自動的に負荷をしませんまたは (これらのファイルのロール オーバー オプションが構成されている) 場合は、ロール オーバー ファイルを読み込むことを確認します。  
  
-   Fn_trace_gettable 関数はロール オーバー ファイルを読み込めません (を使用して指定されている場合、 *number_files*引数) 元のファイル名がアンダー スコアと数値が終了します。 ただし、この状況は、ファイルがロールオーバーされるときに自動的に追加されたアンダースコアおよび数値については該当しません。  
  
> [!NOTE]  
>  このような動作に対処するには、元のファイル名のアンダースコアを削除してトレース ファイルの名前を変更します。 たとえば、元のファイルの名前は**my_trace.trc**、ロール オーバー ファイルの名前は、 **my_trace_1.trc**、ファイルの名前を変更することができます**mytrace.trc**と**mytrace_1.trc**内のファイルを開く前に[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。  
  
 *trace_file* TRACE_PRODUCE_BLACKBOX オプションを使用する場合は指定できません。  
  
 [  **@maxfilesize=** ] *max_file_size*  
 トレース ファイルの最大サイズを MB 単位で指定します。 *その結果、max_file_size*は**bigint**、既定値は**5**です。  
  
 ファイルへの記録に使用されるディスク領域がで指定された量を超えた場合にトレースを停止場合、このパラメーターを指定して、TRACE_FILE_ROLLOVER オプションを指定せず、 *max_file_size*です。  
  
 [  **@stoptime=** ] **'***stop_time***'**  
 トレースを停止する日付と時刻を指定します。 *stop_time*は**datetime**、既定値は NULL です。 この値を NULL にすると、トレースを手動で停止するか、サーバーがシャットダウンするまで、トレースは実行されます。  
  
 両方*stop_time*と*max_file_size*指定すると、TRACE_FILE_ROLLOVER がないと指定すると、トレースを最重要、指定した停止時刻またはファイルの最大サイズに達したときにします。 場合*stop_time*、 *max_file_size*、し、TRACE_FILE_ROLLOVER を指定すると、トレースがドライブがいっぱいにならないと仮定すると指定された停止時に、トレースを停止します。  
  
 [  **@filecount=** ] **'***max_rollover_files***'**  
 同じ基本ファイル名で保持するトレース ファイルの最大数を指定します。 *max_rollover_files*は**int**、1 よりも大きいです。 このパラメーターは、TRACE_FILE_ROLLOVER オプションを指定した場合のみ有効です。 ときに*max_rollover_files*が指定されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に保た以上*max_rollover_files*新しいトレース ファイルを開く前に、最も古いトレース ファイルを削除することによってトレース ファイル。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]基本ファイル名に番号を追加して、トレース ファイルの世代を追跡します。  
  
 たとえば、ときに、 *trace_file*パラメーターを指定"c:\mytrace"と"c:\mytrace_123.trc"の名前を持つファイルは"c:\mytrace_124.trc"のファイルよりも古いします。 場合*max_rollover_files*がセットを 2 に SQL Server は、ファイル"c:\mytrace_123.trc"を削除し、"c:\mytrace_125.trc"トレース ファイルを作成する前にします。  
  
 注意して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各を削除するだけの試行が 1 回、ファイルし、別のプロセスによって使用されているファイルを削除できません。 このため、トレースの実行中に別のアプリケーションによってトレース ファイルが使用されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではそれらのトレース ファイルがファイル システムに残されることがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 次の表は、このストアド プロシージャの完了時に返されるコード値を示しています。  
  
|リターン コード|Description|  
|-----------------|-----------------|  
|0|エラーなし。|  
|1|不明なエラーです。|  
|10|オプションが無効。 指定したオプションが一致しない場合に返されます。|  
|12|ファイルが作成されていない。|  
|13|メモリ不足。 指定した操作を実行するための十分なメモリがない場合に返されます。|  
|14|停止時刻が無効。 指定した停止時刻が既に過ぎている場合に返されます。|  
|15|パラメーターが無効。 ユーザーが一致しないパラメーターを指定した場合に返されます。|  
  
## <a name="remarks"></a>解説  
 **sp_trace_create**は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって実行される操作の多くを実行するストアド プロシージャ**xp_trace _\*** 拡張ストアド プロシージャの SQL Server の以前のバージョンで使用できます。 使用して**sp_trace_create**の代わりにします。  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_setqueuecreateinfo**  
  
-   **xp_trace_setqueuedestination**  
  
 **sp_trace_create**のみのトレース定義を作成します。 このストアド プロシージャを使用してトレースを開始したり変更することはできません。  
  
 ストアド プロシージャのすべての SQL トレースのパラメーター (**sp_trace_xx**) は、厳密に型指定されています。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
 **Sp_trace_create**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントでは、トレース ファイルのフォルダーに対する書き込み権限が必要です。 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントが管理者ではない、トレース ファイルがあるコンピューターへの書き込み権限を付与する必要があります明示的に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。  
  
> [!NOTE]  
>  作成したトレース ファイルを自動的に読み込むことができます**sp_trace_create**を使用してテーブルに、 **fn_trace_gettable**システム関数です。 このシステム関数を使用する方法については、次を参照してください。 [sys.fn_trace_gettable &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md).  
  
 トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)」を参照してください。  
  
 **TRACE_PRODUCE_BLACKBOX**は次の特性があります。  
  
-   ロールオーバー トレースです。 既定値*file_count*は 2 ですが、ユーザーを使用してオーバーライドできます*filecount*オプション。  
  
-   既定値*file_size*他のトレースは 5 MB と変更できます。  
  
-   ファイル名を指定することはできません。 ファイルとして保存されます: **N'%SQLDIR%\MSSQL\DATA\blackbox.trc'**  
  
-   トレースに含まれるのは、次のイベントとその列のみです。  
  
    -   **RPC の開始**  
  
    -   **バッチの開始**  
  
    -   **例外**  
  
    -   **注意**  
  
-   このトレースからイベントまたは列を追加または削除することはできません。  
  
-   このトレースのフィルターを指定することはできません。  
  
## <a name="permissions"></a>Permissions  
 ユーザーに ALTER TRACE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sp_trace_generateevent &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [SQL トレース (SQL Trace)](../../relational-databases/sql-trace/sql-trace.md)  
  
  
