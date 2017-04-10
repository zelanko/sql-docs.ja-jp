---
title: "Manage a Running Process | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "report processing [Reporting Services], status information"
  - "jobs [Reporting Services]"
  - "ジョブの確認"
  - "canceling jobs"
  - "user jobs [Reporting Services]"
  - "system jobs [Reporting Services]"
  - "report processing [Reporting Services], managing running processes"
  - "processes [Reporting Services]"
  - "scanning processes [Reporting Services]"
  - "status information [Reporting Services]"
  - "report processing [Reporting Services]"
  - "canceling subscriptions"
  - "report servers [Reporting Services], jobs"
  - "data-driven subscriptions"
  - "displaying jobs"
  - "サブスクリプション [Reporting Services], 実行中のプロセス"
ms.assetid: 473e574e-f1ff-4ef9-bda6-7028b357ac42
caps.latest.revision: 53
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 53
---
# Manage a Running Process
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバーで実行中のジョブの状態を監視します。 レポート サーバーは、一定の間隔で、実行中のジョブをスキャンし、レポート サーバー データベース (SharePoint モードの場合はサービス アプリケーション データベース) に状態情報を書き込みます。 リモートまたはローカル データベース サーバーでのクエリの実行、レポート処理、およびレポート表示のいずれかが行われている場合、ジョブは実行中です。  
  
 *ユーザー ジョブ* と *システム ジョブ*の両方を管理できます。  
  
-   ユーザー ジョブは、各ユーザーまたはサブスクリプションによって開始されます。 このジョブには、要求時のレポートの実行、レポート履歴スナップショットの要求、レポート スナップショットの手動作成、および標準のサブスクリプションの処理が含まれます。  
  
-   システム ジョブは、レポート サーバーによって開始されます。 システム ジョブには、スケジュールされたレポート実行スナップショット、スケジュールされたレポート履歴スナップショット、およびデータ ドリブン サブスクリプションが含まれます。  
  
 レポートの処理時間およびリソースの使用は、レポート、クエリの複雑さ、データ量、およびレポートに対して指定された表示形式により、大きく異なります。 ローカル データ ソースに対する単純なクエリを有するレポートは、通常、ミリ秒単位で完了し、管理または調整の必要はありません。 これに対し、PDF または Excel で表示されるサイズの大きいレポートでは、ハードウェア リソース、配信オプション、および並行して他の処理が実行されているかどうかにより、相当な処理時間を要する場合があります。 レポート サーバーでは、時間のかかる処理の多くは、レポートの表示操作処理と、クエリ処理の完了を待機している処理です。 コンピューターをオフラインにしたり、完了までに長時間かかっている実行中のジョブを停止する場合、レポート処理を取り消すことが必要になる場合があります。  
  
 キャンセルできる処理は次のとおりです。  
  
-   オンデマンドのレポート処理。  
  
-   スケジュールされたレポート処理。  
  
-   個々のユーザーが所有する標準サブスクリプション。  
  
 ジョブのキャンセルでは、レポート サーバーで実行中の処理だけが取り消されます。 レポート サーバーは、他のコンピューター上のデータ処理を管理しないため、他のシステム上で孤立したそれ以降のクエリ処理については、手動で取り消す必要があります。 実行に長時間かかるクエリが自動的にシャットダウンされるようなクエリのタイムアウト値を指定することを検討してください。 詳細については、「[レポートおよび共有データセット処理のタイムアウト値の設定 (SSRS)](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)」を参照してください。 レポートを一時的に停止する方法の詳細については、「[レポートとサブスクリプションの処理を無効化または一時停止する](../../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md)」を参照してください。  
  
> [!NOTE]  
>  まれに、サーバーを再起動して処理を取り消す必要が生じる場合があります。 SharePoint モードの場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションをホストしているアプリケーション プールの再起動が必要になる場合があります。 詳細については、「[レポート サーバー サービスの開始と停止](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)」を参照してください。  
  
 このトピックの内容  
  
-   [ジョブの表示とキャンセル (ネイティブ モード)](#bkmk_native)  
  
-   [ジョブの表示とキャンセル (SharePoint モード)](#bkmk_sharepoint)  
  
-   [プログラムによるジョブの管理](#bkmk_programmatically)  
  
##  <a name="bkmk_native"></a> ジョブの表示とキャンセル (ネイティブ モード)  
 レポート サーバーで実行中のジョブは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して表示したり取り消したりできます。 現在実行中のジョブの一覧を取得したり、最新のジョブ ステータスをレポート サーバー データベースから取得したりするには、ページを更新する必要があります。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からレポート サーバーに接続する際、[ジョブ] フォルダーを開くと、現在レポート サーバー コンピューターで処理中のレポートを一覧表示できます。 [ジョブのプロパティ] ページに、各ジョブのステータス情報が表示されます。 [レポート サーバー ジョブのキャンセル] ダイアログ ボックスを開くことによって、すべてのジョブのステータス情報を確認できます。  
  
 レポート サーバーで実行中のジョブは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して表示したり取り消したりできます。 現在実行中のジョブの一覧を取得したり、最新のジョブ ステータスをレポート サーバー データベースから取得したりするには、ページを更新する必要があります。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からレポート サーバーに接続する際、[ジョブ] フォルダーを開くと、現在レポート サーバー コンピューターで処理中のレポートを一覧表示できます。 [ジョブのプロパティ] ページに、各ジョブのステータス情報が表示されます。 [レポート サーバー ジョブのキャンセル] ダイアログ ボックスを開くことによって、すべてのジョブのステータス情報を確認できます。  
  
 モデルの生成、モデルの処理、またはデータ ドリブン サブスクリプションについては、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で一覧表示したり取り消したりすることはできません。 モデルの生成またはモデルの処理を取り消す手段は、Reporting Services には用意されていません。 ただし、このトピックで紹介している手順に従うことによって、データ ドリブン サブスクリプションをキャンセルできます。  
  
### レポート処理またはサブスクリプションを取り消す方法  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からレポート サーバーに接続します。 詳細については、「[Management Studio でレポート サーバーに接続する方法](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)」を参照してください。  
  
2.  **[ジョブ]** フォルダーを開きます。  
  
3.  レポートを右クリックし、**[ジョブの取り消し]** をクリックします。  
  
### データ ドリブン サブスクリプションを取り消す方法  
  
1.  テキスト エディターで RSReportServer.config ファイルを開きます。  
  
2.  **IsNotificationService**を探します。  
  
3.  **False**に設定します。  
  
4.  ファイルを保存します。  
  
5.  レポート マネージャーで、レポートの [サブスクリプション] タブまたは **[個人用サブスクリプション]** からデータ ドリブン サブスクリプションを削除します。  
  
6.  サブスクリプションを削除したら、RSReportServer.config ファイルで **IsNotificationService** を探し、 **True**に設定します。  
  
7.  ファイルを保存します。  
  
### ジョブ ステータスの取得間隔の設定  
 実行中のジョブは、レポート サーバーの一時データベースに格納されます。 RSReportServer.config ファイルで構成設定を変更し、レポート サーバーによる実行中のジョブをスキャンする頻度と実行ジョブの状態を新規から実行中に変更するまでの間隔を制御できます。 **RunningRequestsDbCycle** 設定では、レポート サーバーによって実行中である処理のスキャンの頻度を指定します。 既定では、状態情報は 60 秒ごとに記録されます。 **RunningRequestsAge** 設定では、ジョブが新規から実行中に遷移するまでの間隔を指定します。  
  
##  <a name="bkmk_sharepoint"></a> ジョブの表示とキャンセル (SharePoint モード)  
 SharePoint モードでの配置のジョブの管理は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションごとに、SharePoint サーバーの全体管理を使用して行います。  
  
#### SharePoint モードでジョブを管理するには  
  
1.  SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]**をクリックします。  
  
2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前を見つけてクリックし、アプリケーションの管理ページを開きます。  
  
3.   **[ジョブの管理]**をクリックします。  
  
4.  **[ジョブ ID]** をクリックして、ジョブの詳細を表示します。  
  
5.  または、ジョブのボックスをクリックして **[削除]** をクリックし、ジョブをキャンセルします。 ジョブを削除しても、サブスクリプションは削除されません。  
  
##  <a name="bkmk_programmatically"></a> プログラムによるジョブの管理  
 ジョブは、プログラムまたはスクリプトを使用して管理できます。 詳細については、「<xref:ReportService2010.ReportingService2010.ListJobs%2A>」と「<xref:ReportService2010.ReportingService2010.CancelJob%2A>」を参照してください。  
  
## 参照  
 [[レポート サーバー ジョブのキャンセル] (Management Studio)](../Topic/Cancel%20Report%20Server%20Jobs%20\(Management%20Studio\).md)   
 [[ジョブのプロパティ] (Management Studio)](../Topic/Job%20Properties%20\(Management%20Studio\).md)   
 [Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [レポート マネージャー (SSRS ネイティブ モード)](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [レポート サーバーのパフォーマンスの監視](../../reporting-services/report-server/monitoring-report-server-performance.md)  
  
  