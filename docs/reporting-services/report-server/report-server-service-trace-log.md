---
title: "レポート サーバー サービスのトレース ログ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs [Reporting Services], trace
- traces [Reporting Services]
- system information [Reporting Services]
- versions [Reporting Services]
ms.assetid: 2fde08b2-137d-4f4b-88e5-216030216e0d
caps.latest.revision: 52
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 37d44eeb29ad4e2acfd4f9618c755f2c5d8b9b28
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="report-server-service-trace-log"></a>Report Server Service Trace Log
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート サーバーのトレース ログは、レポート サーバー サービスの操作の詳細な情報が含まれる ASCII テキスト ファイルです。  このファイル内の情報には、レポート サーバー Web サービス、web ポータル、およびバック グラウンド処理によって実行された操作が含まれます。 トレース ログ ファイルには、他のログ ファイルに記録されている冗長な情報、およびトレース ログ以外からは入手できない追加情報が含まれています。 トレース ログ情報は、レポート サーバーを含むアプリケーションをデバッグしている場合、またはイベント ログや実行ログに書き込まれた特定の問題を調査している場合に役立ちます。 たとえば、サブスクリプションに関する問題をトラブル シューティングしている場合です。  
 
##  <a name="bkmk_view_log"></a> レポート サーバー のログ ファイルの場所  
 トレース ログ ファイルは`ReportServerService_<timestamp>.log`と`Microsoft.ReportingServices.Portal.WebHost_<timestamp>.log`られ、次のフォルダー内に存在します。  
  
 `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`  
  
 トレース ログが作成されます毎日、午前 0 時 (ローカル時刻) の後に発生する最初のエントリで開始し、サービスを再起動するたびにします。 タイムスタンプには、協定世界時 (UTC) が使用されます。 このファイルは EN-US 形式です。 既定では、トレース ログのサイズの上限は 32 MBであり、14 日後に削除されます。  
  
 Microsoft Power Query を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ログ ファイルを表示する方法を示す短いビデオを表示します。  
  
[![Power Query および SSRS ログ ファイルについて説明するビデオを見る](../../reporting-services/report-server/media/generic-video-thumbnail.png)](https://technet.microsoft.com/library/sql-server-reporting-services-log-files-and-microsoft-power-query.aspx)  [Microsoft Power Query を使用して Reporting Services のログ ファイルを表示する](https://technet.microsoft.com/library/sql-server-reporting-services-log-files-and-microsoft-power-query.aspx)
  
##  <a name="bkmk_trace_configuration_settings"></a> トレースの構成設定  
 構成ファイルでトレース ログの動作を管理する**ReportingServicesService.exe.config**です。 構成ファイルは次のフォルダー パスにあります。  
  
 `\Program Files\Microsoft SQL Server\MSRS13.<instance name>\Reporting Services\ReportServer\bin`で管理されています。  
  
 次の例では、 **RStrace** の設定の XML 構造を示しています。 **DefaultTraceSwitch** の値によって、ログに追加される情報の種類が決まります。 **Components** 属性を除き、 **RStrace** の値は構成ファイル間で同じになります。  
  
```  
  \<system.diagnostics>
    <switches>
      <add name="DefaultTraceSwitch" value="3" />
    </switches>
  \</system.diagnostics>
  <RStrace>
    <add name="FileName" value="ReportServerService_" />
    <add name="FileSizeLimitMb" value="32" />
    <add name="KeepFilesForDays" value="14" />
    <add name="Prefix" value="appdomain, tid, time" />
    <add name="TraceListeners" value="file" />
    <add name="TraceFileMode" value="unique" />
    <add name="Components" value="all:3" />
  </RStrace>
```  
  
 次の表では、各設定に関する情報を示します。  
  
|設定|Description|値|  
|-------------|-----------------|------------|  
|**RStrace**|エラーおよびトレースに使用される名前空間を指定します。||  
|**DefaultTraceSwitch**|ReportServerService トレース ログにレポートされる情報のレベルを指定します。 各レベルには、そのレベルより低いすべてのレベルでレポートされる情報が含まれます。 トレースを無効にすることはお勧めしません。|以下の値が有効です。<br /><br /> <br /><br /> 0= トレースの無効化。 ReportServerService ログ ファイルは既定で有効になります。 オフにする場合は、トレース レベルを 0 に設定します。<br /><br /> 1= 例外および再起動<br /><br /> 2= 例外、再起動、警告<br /><br /> 3= 例外、再起動、警告、状態メッセージ (既定)<br /><br /> 4= 詳細モード|  
|**FileName**|ログ ファイル名の最初の部分を指定します。 **Prefix** で指定した値が付加されて、完全な名前になります。||  
|**FileSizeLimitMb**|トレース ログのサイズの上限を指定します。 ファイルは MB 単位で測定されます。<br /><br /> トレース レベル (0 ～ 4) を設定して、ログに記録される内容を制御することにより、ファイル サイズを制御することができます。 また、トレースするコンポーネントを指定することもできます。 14 日間の有効期限が切れる前にログ ファイルが最大サイズに達すると、古いエントリが新しいエントリに置き換えられます。|正しい値は、0 から整数型の最大値までです。 既定値は 32 です。 0 または負の値を指定した場合、レポート サーバーでは値が 1 として扱われます。|  
|**KeepFilesForDays**|トレース ログ ファイルを削除するまでの保持期間を日数で指定します。|正しい値は、0 から整数型の最大値までです。 既定値は 14 です。 0 または負の値を指定した場合、レポート サーバーでは値が 1 として扱われます。|  
|**Prefix**|あるログのインスタンスを別のログのインスタンスと区別するために生成する値を指定します。|既定では、トレース ログ ファイル名にタイムスタンプの値が追加されます。 この値は、「appdomain、tid, 時間」に設定されます。 この設定は変更しないでください。|  
|**TraceListeners**|トレース ログ コンテンツの出力先を指定します。 複数の出力先を指定する場合、各出力先をコンマで区切ってください。|以下の値が有効です。<br /><br /> <br /><br /> DebugWindow<br /><br /> File (既定値)<br /><br /> StdOut|  
|**TraceFileMode**|トレース ログに 24 時間データを含めるかどうかを指定します。 コンポーネントごとに、毎日 1 つ、一意のトレース ログが必要です。|この値は、"Unique (既定値)" に設定されます。 この値は変更しないでください。|  
|**コンポーネント カテゴリ**|トレース ログ情報の生成対象となるコンポーネントおよびトレース レベルを次の形式で指定します。<br /><br /> \<コンポーネント名 >:\<tracelevel ><br /><br /> コンポーネント (**all**、 **RunningJobs**、 **SemanticQueryEngine**、 **SemanticModelGenerator**) のすべてまたは一部を指定できます。 特定のコンポーネントに関する情報を生成しない場合は、そのコンポーネントのトレースを無効にできます (たとえば "SemanticModelGenerator:0")。 **all**の場合は、トレースを無効にしないでください。<br /><br /> 各セマンティック クエリに対して生成される Transact-SQL ステートメントを表示する場合は、"SemanticQueryEngine:4" を設定できます。 Transact-SQL ステートメントは、トレース ログに記録されます。 次の例では、Transact-SQL ステートメントをログに追加する構成設定を示しています。<br /><br /> \<名前の追加「コンポーネント」の値を = ="all, SemanticQueryEngine:4"/>|コンポーネントのカテゴリには次の値を設定できます。<br /><br /> <br /><br /> 特定のカテゴリに分類されないすべてのプロセスに対する通常のレポート サーバーの利用状況を追跡するには、**All** を使用します。<br /><br /> 実行中のレポートまたはサブスクリプションの操作を追跡するには、**RunningJobs** を使用します。<br /><br /> ユーザーがモデルベースのレポートでアドホック データ探索を実行する場合に処理されるセマンティック クエリを追跡するには、**SemanticQueryEngine** を使用します。<br /><br /> モデルの生成を追跡するには、**SemanticModelGenerator** を使用します。<br /><br /> レポート サーバーの HTTP ログ ファイルを有効にするには、**http** を使用します。 詳しくは、「 [Report Server HTTP Log](../../reporting-services/report-server/report-server-http-log.md)」をご覧ください。|  
|コンポーネント カテゴリの**tracelevel** 値|\<コンポーネント名 >:\<tracelevel ><br /><br /> <br /><br /> コンポーネントにトレース レベルを追加しない場合は、 **DefaultTraceSwitch** に指定された値が使用されます。 たとえば、"all,RunningJobs,SemanticQueryEngine,SemanticModelGenerator" と指定すると、すべてのコンポーネントで既定のトレース レベルが使用されます。|トレース レベルの有効な値は次のとおりです。<br /><br /> <br /><br /> 0= トレースの無効化<br /><br /> 1= 例外および再起動<br /><br /> 2= 例外、再起動、警告<br /><br /> 3= 例外、再起動、警告、状態メッセージ (既定)<br /><br /> 4= 詳細モード<br /><br /> レポート サーバーの既定値は "all:3" です。|  
  
##  <a name="bkmk_add_custom"></a> ダンプ ファイルの場所を指定するカスタム構成設定の追加  
 カスタム設定を追加して、Windows ワトソン博士ツールでダンプ ファイルを格納する際に使用する場所を設定できます。 カスタム設定は **Directory**です。 次の例では、この構成設定を **RStrace** セクションに指定する方法を示しています。  
  
```  
<add name="Directory" value="U:\logs\" />  
```  
  
 詳細については、 [Web サイトの](http://support.microsoft.com/?kbid=913046) サポート技術情報の記事 913046 [!INCLUDE[msCoName](../../includes/msconame-md.md)] を参照してください。  
  
##  <a name="bkmk_log_file_fields"></a> ログ ファイル フィールド  
 トレース ログでは、次のフィールドを確認できます。  
  
-   オペレーティング システム、バージョン、プロセッサ数、およびメモリなどのシステム情報  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンポーネント情報およびバージョン情報  
  
-   アプリケーション ログに記録されたイベント  
  
-   レポート サーバーによって生成された例外  
  
-   レポート サーバーによって記録されたリソースへの低レベルの警告  
  
-   受信 SOAP エンベロープおよび要約された送信 SOAP エンベロープ  
  
-   HTTP ヘッダー、スタック トレース、およびデバッグ トレースの情報  
  
 トレース ログの情報を確認して、レポートが配信されたかどうか、レポートの受信者、および配信の試行回数を判断できます。 また、トレース ログには、レポートの処理中に有効なレポート実行操作および環境変数も記録されます。 トレース ログには、エラーおよび例外も記録されます。 たとえば、レポートのタイムアウト エラーが見つかる場合があります ( **ThreadAbortExceptions** エントリとして表示されます)。  

## <a name="previous-versions"></a>以前のバージョン
[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]の以前のリリースでは、複数のトレース ログ ファイル (アプリケーションごとに 1 つ) が存在しました。 次のファイルは廃止されており、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以上のバージョンでは作成されなくなりました。
+ Reportserverwebapp _*\<タイムスタンプ >*.log
+ Reportserver _*\<タイムスタンプ >*.log
+ Reportserverservice_main*\<タイムスタンプ >*.log
  
## <a name="see-also"></a>参照  
 [Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [エラーとイベントのリファレンス &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
 他に質問しますか。 [Reporting Services のフォーラムを再試行してください。](http://go.microsoft.com/fwlink/?LinkId=620231)
  

