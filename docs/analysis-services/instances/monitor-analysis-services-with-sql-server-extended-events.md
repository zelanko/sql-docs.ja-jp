---
title: Analysis Services と SQL Server 拡張イベントの監視 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4b24903ae17cc97ea1a87f912271cf63a55714b5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="monitor-analysis-services-with-sql-server-extended-events"></a>SQL Server 拡張イベントを使用した Analysis Services の監視
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  拡張イベント (*xEvents*) は、わずかなシステム リソースを運用サーバーとテスト サーバーの両方の問題を診断するための理想的なツールに変える、軽量のトレースおよびパフォーマンス監視システムです。 また、拡張性が高く、詳細な構成が可能で、SQL Server 2016 では、新しい組み込みのツール サポートにより使用が簡単です。 SQL Server Management Studio で Analysis Services インスタンスに接続すると、SQL Server Profiler を使用するようにライブ トレースを構成、実行、および監視することができます。 優れたツールを追加することで、SQL Server Profiler から xEvent に置き換える合理性が高まり、データベース エンジンと Analysis Services ワークロードの問題を同等に診断できるようになります。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]だけでなく  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 拡張イベントのセッションも、以前のリリースでサポートされていたように XMLA スクリプトで構成することができます。  
  
 「 [拡張イベント](../../relational-databases/extended-events/extended-events.md)」で定義されているように、特定のコンシューマーを対象としたすべての Analysis Services イベントをキャプチャできます。  
  
> [!NOTE]  
>  SQL Server 2016 Analysis Services の xEvent の詳細については、この [早わかりビデオ](https://www.youtube.com/watch?v=ja2mOHWRVC0&index=1&list=PLv2BtOtLblH1YvzQ5YnjfQFr_oKEvMk19) を見るか、 [ブログ投稿](http://blogs.msdn.com/b/analysisservices/archive/2015/09/22/using-extended-events-with-sql-server-analysis-services-2016-cpt-2-3.aspx) を参照してください。  
  
  
##  <a name="bkmk_ssas_extended_events_ssms"></a> Management Studio を使用して Analysis Services を構成する  
 Management Studio は、表形式インスタンスと多次元インスタンスの両方で、ユーザーが開始した xEvent セッションを格納する新しい管理フォルダーを提供します。 一度に複数のセッションを実行することができます。 ただし、現在の実装では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 拡張イベント ユーザー インターフェイスが既存のセッションの更新または再生をサポートしていません。  
  
 ![ssas_extended_events_ssms_start](../../analysis-services/instances/media/ssas-extended-events-ssms-start.png "ssas_extended_events_ssms_start")  
  
 **イベントを選択する**  
  
 キャプチャするイベントを既に把握している場合、最も簡単にイベントをトレースに追加する方法は、イベントを検索することです。 それ以外の場合、通常は次のイベントが操作の監視で使用されます。  
  
-   **CommandBegin** と **CommandEnd**。  
  
-   **QueryBegin**、 **QueryEnd**、および **QuerySubcubeVerbose** (サーバーに送信された MDX または DAX クエリ全体が表示されます)。さらに、クエリにより消費されたリソースと、返される行数の統計を示す **ResourceUsage** 。  
  
-   **ProgressReportBegin** と **ProgressReportEnd** (処理中の操作用)。  
  
-   **AuditLogin** および **AuditLogout** (クライアント アプリケーションが Analysis Services に接続しているユーザー ID をキャプチャする)。  
  
 **データ ストレージを選択する**  
  
 セッションは、Management Studio のウィンドウでライブ ストリーミングするか、Power Query または Excel を使用して以後の分析のためにファイルに保存することができます。  
  
-   **event_file** では、セッション データが .xel ファイルに保存されます。  
  
-   **event_stream** では、 Management Studio の **[ライブ データ監視]** オプションが有効になります。  
  
-   **ring_buffer** では、サーバーが実行されている間のセッション データがメモリに保存されます。 サーバーが再起動すると、セッション データは破棄されます。  
  
 **イベント フィールドを追加する**  
  
 必要な情報が簡単にわかるように、セッションはイベント フィールドが含まれるように構成してください。  
  
 ダイアログ ボックスの一番端に **[構成]** オプションがあります。  
  
 ![ssas-xevents-configure](../../analysis-services/instances/media/ssas-xevents-configure.PNG "ssas-xevents-configure")  
  
 [構成] の [イベント フィールド] タブで **[TextData]** を選択して、このフィールドがサーバーで実行されているクエリを含む戻り値を示した状態でイベントの隣に表示されるようにします。  
  
 必要なイベントとデータ ストレージのセッションを構成したら、[スクリプト] ボタンをクリックして、ファイル、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の新しいクエリ、クリップボードを含む、サポートされる送信先のいずれかに構成を送信します。  
  
 **セッションを更新する**  
  
 セッションを作成したら、作成したセッションが表示されるように、Management Studio の [セッション] フォルダーを更新してください。 event_stream を構成した場合は、セッション名を右クリックして **[ライブ データ監視]** を選択すると、サーバーの利用状況をリアルタイムで監視できます。  
  
##  <a name="bkmk_script_start"></a> Analysis Services で拡張イベントを開始する XMLA スクリプト  
 拡張イベントのトレースは、以下のような XMLA のオブジェクト作成スクリプト コマンドを使用して有効にします。  
  
```  
<Execute …>  
   <Command>  
      <Batch …>  
         <Create …>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session …>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" …/>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 ユーザーは、トレースのニーズに応じて、次の要素を定義します。  
  
 *trace_id*  
 このトレースの一意識別子を定義します。  
  
 *trace_name*  
 このトレースに付ける名前を指定します (通常は、人間が判読できるトレースの定義です)。 *trace_id* の値を名前として使用するのが一般的です。  
  
 *AS_event*  
 公開する Analysis Services イベントを指定します。 イベントの名前については、「 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md) 」を参照してください。  
  
 *data_filename*  
 イベント データを含むファイルの名前を指定します。 この名前には、トレースを繰り返し送信する場合にデータが上書きされないように、タイムスタンプを使用したサフィックスが付けられます。  
  
 *metadata_filename*  
 イベント メタデータを含むファイルの名前を指定します。 この名前には、トレースを繰り返し送信する場合にデータが上書きされないように、タイムスタンプを使用したサフィックスが付けられます。  
  
  
##  <a name="bkmk_script_stop"></a> Analysis Services で拡張イベントを停止する XMLA スクリプト  
 拡張イベントのトレース オブジェクトを停止するには、以下のような XMLA のオブジェクト削除スクリプト コマンドを使用して、そのオブジェクトを削除する必要があります。  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch …>  
         <Delete …>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 ユーザーは、トレースのニーズに応じて、次の要素を定義します。  
  
 *trace_id*  
 削除するトレースの一意識別子を定義します。  
  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
