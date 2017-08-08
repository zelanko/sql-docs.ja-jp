---
title: "[サーバーのプロパティ] ([詳細設定] ページ) - Reporting Services | Microsoft Docs"
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
f1_keywords:
- sql13.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b5cd82621ecd65bb56b8a5a2eb0314935fd3a37a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="server-properties-advanced-page---reporting-services"></a>[サーバーのプロパティ]\([詳細設定] ページ) - Reporting Services
  このページを使用して、レポート サーバーのシステム プロパティを設定します。 システム プロパティを設定する方法はいくつかあります。 このツールにはグラフィカル ユーザー インターフェイスが用意されているので、コードを記述しなくてもプロパティを設定できます。  
  
 このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]**をクリックします。 **[詳細設定]** をクリックするとこのページが開きます。  
  
## <a name="options"></a>オプション  
 **EnableMyReports**  
 個人用レポート機能が有効になっているかどうかを指定します。 値 **true** は、機能が有効になっていることを示します。  
  
 **MyReportsRole**  
 ユーザーの個人用レポート フォルダーに、セキュリティ ポリシーを作成する際に使用するロールの名前。 既定値は **My Reports Role**です。  
  
 **EnableClientPrinting**  
 レポート サーバーからのダウンロードに RSClientPrint ActiveX コントロールが使用可能かどうかを示します。 有効値は **true** および **false**です。 既定値は **true**です。 このコントロールに必要な追加設定に関する詳細については、「 [Reporting Services のクライアント側印刷機能の有効化と無効化](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)」を参照してください。  
  
 **EnableExecutionLogging**  
 レポート実行のログ記録が有効になっているかどうかを示します。 既定値は **true**です。 レポート サーバー実行ログの詳細については、「 [レポート サーバー ExecutionLog と ExecutionLog3 ビュー](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)」を参照してください。  
  
 **ExecutionLogDaysKept**  
 レポート実行情報を実行ログに保持する日数。 このプロパティの有効値は、 **-1** - **2**、**147**、**483**、**647**です。 値が **-1** の場合、エントリは実行ログ テーブルから削除されません。 既定値は **60**です。  
 
> [!NOTE] 
> **0** の値を設定すると、実行ログからすべてのエントリが*削除*されます。 **-1** の値を設定すると、実行ログのエントリは保持され、削除されません。
  
 **SessionTimeout**  
 セッションがアクティブな状態になっている期間 (秒単位)。 既定値は **600**です。  
  
 **SharePointIntegratedMode**  
 これは、サーバー モードを示す読み取り専用プロパティです。 この値が False の場合、レポート サーバーはネイティブ モードで実行されます。  
  
 **SiteName**  
 Web ポータルのページ タイトルに表示されるレポート サーバー サイトの名前。 既定値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。 このプロパティには空の文字列を指定できます。 最大長は 8,000 文字です。  
  
 **StoredParametersLifetime**  
 保存したパラメーターを保持できる最大日数を指定します。 有効値は **-1**、 **+1** ～ **2,147,483,647**です。 既定値は **180** 日です。  
  
 **StoredParametersThreshold**  
 レポート サーバーが保存できるパラメーター値の最大数を指定します。 有効値は **-1**、 **+1** ～ **2,147,483,647**です。 既定値は **1500**です。  
  
 **UseSessionCookies**  
 レポート サーバーがクライアント ブラウザーとの通信時にセッションクッキーを使用する必要があるかどうかを指定します。 既定値は **true**です。  
  
 **ExternalImagesTimeout**  
 この時間以内に外部画像ファイルを取得しないと接続がタイムアウトになる時間の長さを指定します。 既定値は **600** 秒です。  
  
 **SnapshotCompression**  
 スナップショットの圧縮方法を定義します。 既定値は **SQL**です。 有効な値は次のとおりです。  
  
 **SQL** = スナップショットは、レポート サーバー データベースへの格納時に圧縮されます。 これは現在の動作です。  
  
 **なし** = スナップショットは圧縮されません。  
  
 **すべて** = すべてのストレージ オプションのスナップショットが圧縮されます。このオプションには、レポート サーバー データベースやファイル システムが含まれます。  
  
 **SystemReportTimeout**  
 レポート サーバー名前空間で管理されているすべてのレポートの既定のレポート処理タイムアウト値 (秒単位)。 この値はレポート レベルでオーバーライドできます。 このプロパティを設定すると、レポート サーバーは指定された時間が経過した後、レポートの処理を停止しようとします。 有効値は **-1** ～ **2**、**147**、**483**、**647**です。 値に **-1**を設定すると、名前空間内のレポートが処理中にタイムアウトしません。 既定値は **1800**です。  
  
 **SystemSnapshotLimit**  
 レポートに格納されるスナップショットの最大数。 有効値は **-1** ～ **2**、**147**、**483**、**647**です。 値が **-1**の場合、スナップショットに制限はありません。  
  
 **EnableIntegratedSecurity**  
 Windows 統合セキュリティをレポート データ ソース接続でサポートするかどうかを決定します。 既定値は **True**です。 有効な値は次のとおりです。  
  
 **True** = Windows 統合セキュリティが有効になります。  
  
 **False** = Windows 統合セキュリティは無効になります。 Windows 統合セキュリティを使用するように構成されているレポート データ ソースは実行されません。  
  
 **EnableLoadReportDefinition**  
 ユーザーがレポート ビルダーのレポートからアドホック レポートを実行できるかどうかを指定するには、このオプションを選択します。 このオプションをオンにすると、レポート サーバーの **EnableLoadReportDefinition** プロパティが設定されます。  
  
 このオプションをオフにするとプロパティが False に設定され、データ ソースとしてレポート モデルを使用するレポートのクリックスルー レポートは生成されません。 LoadReportDefinition メソッドへの呼び出しをブロックします。  
  
 この機能を無効にすることで、悪意のあるユーザーが LoadReportDefinition 要求でレポート サーバーを過負荷にするサービス拒否攻撃の脅威を軽減することができます。  
  
 **EnableRemoteErrors**  
 リモート コンピューターからレポートを要求したユーザーに返されるエラー メッセージに、外部エラー情報 (レポート データ ソースに関するエラー情報など) を含めます。 有効値は **true** および **false**です。 既定値は **false**です。 詳細については、「[リモート エラーの有効化 (Reporting Services)](../../reporting-services/report-server/enable-remote-errors-reporting-services.md)」を参照してください。  
  
 **EnableReportDesignClientDownload**  
 レポート ビルダーのインストール パッケージをレポート サーバーからダウンロードできるかどうかを指定します。 この設定をオフにすると、レポート ビルダーの URL が機能しません。 詳細については、「 [レポート ビルダーへのアクセスの構成](../../reporting-services/report-server/configure-report-builder-access.md)」を参照してください。  
  
 **EditSessionCacheLimit**  
 レポート編集セッションでアクティブにできるデータ キャッシュ エントリの数を指定します。 既定の数は 5 です。  
  
 **EditSessionTimeout**  
 レポート編集セッションがタイムアウトするまでの秒数を指定します。 既定値は 7200 秒 (2 時間) です。  
  
 **EnableTestConnectionDetailedErrors**  
 ユーザーがレポート サーバーを使用してデータ ソース接続をテストする際に、クライアント コンピューターに詳細なエラー メッセージが送信されるようにするかどうかを指定します。 既定値は **true**です。 このオプションを **false**に設定した場合は、一般的なエラー メッセージだけが送信されます。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する (Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Reporting Services のプロパティ](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [レポート サーバーのシステム プロパティ](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
 [配置タスクおよび管理タスクのスクリプト作成](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
 [個人用レポートの有効化と無効化](../../reporting-services/report-server/enable-and-disable-my-reports.md)  
  
  

