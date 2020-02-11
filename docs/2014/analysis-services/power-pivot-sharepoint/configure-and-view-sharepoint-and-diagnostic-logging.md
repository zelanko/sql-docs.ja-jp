---
title: SharePoint ログファイルと診断ログの構成と表示 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 85f62d29-cdc6-45b3-be1f-ff1182939858
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f05edb30344b63781a89540ade8de4743bb715e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071852"
---
# <a name="configure-and-view-sharepoint-log-files--and-diagnostic-logging-powerpivot-for-sharepoint"></a>SharePoint ログ ファイルと診断ログの構成と表示 (PowerPivot for SharePoint)
  
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー操作、イベント、およびメッセージは、SharePoint ログ ファイルに記録されます。 このトピックでは、ログ記録レベルの構成とログ ファイルの情報の表示について説明します。 ログ ファイルに記録される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー イベントを制御できます。 また、ログに記録されるメッセージの重大度も制御できます。 詳細については、「 [&#40;PowerPivot for SharePoint の使用状況データ収集の構成](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)」を参照してください。  
  
 このトピックの内容:  
  
-   [ログファイルの場所](#bkmk_filelocation)  
  
-   [個々のイベントカテゴリの診断ログレベルを変更する](#bkmk_modifyloglevels)  
  
-   [SharePoint ログファイルを表示する方法](#bkmk_how2viewlogfiles)  
  
##  <a name="bkmk_filelocation"></a>ログファイルの場所  
 既定では、SharePoint ログ ファイルは次の場所に保存されます。  
  
 `C:\Program files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS`  
  
 LOGS フォルダーには、ログ ファイル (`.log`)、データ ファイル (`.txt`)、および使用状況ファイル (`.usage`) が保存されています。 SharePoint トレース ログのファイル名前付け規則では、サーバー名の後に日付とタイム スタンプが続きます。 SharePoint トレース ログは定期的に作成され、IISRESET が実行された場合も作成されます。 一般に、24 時間内で多数のトレース ログが作成されます。  
  
##  <a name="bkmk_modifyloglevels"></a>個々のイベントカテゴリの診断ログレベルを変更する  
 既定では、PowerPivot イベントの ULS ログは *"中"* に設定されています。 この設定は、SQL Server 2012 の新しい設定です。 サーバーを以前のリリースからアップグレードした場合、ログ レベルはまだ SQL Server 2008 R2 のデフォルト レベルの *"詳細"* が設定されている場合があります。 PowerPivot サーバーの使用状況に対する ULS ログを確認することに慣れている場合、この変更によって PowerPivot サーバーの操作に関する情報が少なくなっていることがわかります。  
  
 
  *"高"* タイプの例外を除くすべての PowerPivot メッセージは、詳細カテゴリに分類されます。 サーバーのルーチン処理 (接続、要求、クエリ レポートなど) のログ エントリが必要な場合、ログ レベルを詳細に変更する必要があります。  
  
 個々のイベント カテゴリに対する診断ログ記録レベルを変更するには、次の手順を実行します。  
  
1.  SharePoint サーバーの全体管理で **[監視]** をクリックします。  
  
2.  
  **[診断ログの構成]** をクリックします。  
  
3.  
  **[PowerPivot サービス]** までスクロールします。  
  
4.  カテゴリを展開し、個々のカテゴリを選択します。  
  
     **アプリケーションページ要求**は、PowerPivot データソースを読み込んでファーム内[!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]の他のサーバーと通信するために、サービスアプリケーションによってトリガーされるイベントを指定します。  
  
     **要求の処理**では、ファーム内のサーバーに読み込まれた PowerPivot データベースに対するクエリ要求によってトリガーされるイベントを指定します。  
  
     **使用**して、PowerPivot 使用状況データ収集に関連するイベントを指定します。  
  
5.  [イベント ログの記録対象となる重要度の最も低いイベント] で、 **[なし]** を選択してカテゴリのイベント ログ記録を無効にするか、 **[エラー]** を選択してログの記録対象をエラーのみに制限します。  
  
6.  
  **[詳細]** をクリックして、すべてのイベントをイベント ログに記録します。  
  
7.  [トレース ログの記録対象となる重要度の最も低いイベント] で、 **[なし]** を選択してカテゴリのトレースを無効にするか、 **[エラー]** を選択してトレースの対象をエラーのみに制限します。  
  
8.  
  **[詳細]** をクリックして、すべてのイベントをトレース ログに記録します。  
  
9. **[OK]** をクリックします。  
  
##  <a name="bkmk_how2viewlogfiles"></a>SharePoint ログファイルを表示する方法  
 ログ ファイルはテキスト ファイルであり、 テキスト エディターで開くことができます。 サードパーティのログ ビューアー アプリケーションを使用することもできます。  
  
#### <a name="use-a-text-editor"></a>テキスト エディターの使用  
 テキスト エディターを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー エラーをトラブルシューティングする場合は、次のヒントを参考にすると、ファイルで関連する情報を見つけることができます。  
  
-   
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのパブリッシュ、表示、または更新に関連するエラーの場合は、ログ ファイルでブックの名前を検索します。  
  
-   エラーに相関 ID が示されている場合は、ID をコピーしてログ ファイルで検索用語として使用します。  
  
-   「高」または「例外」のエラー状態を検索します。 "PowerPivot サービス" を検索します。  
  
-   エラーの発生日時を把握している場合は、日付と時刻の情報を使用して、スクロールするエントリの範囲を絞り込みます。  
  
#### <a name="use-a-log-viewer-application"></a>ログ ビューアー アプリケーションの使用  
 テキスト エディターを使用してトレース ログを個別に表示できますが、いくつかのログ ファイルを同時に表示できるログ ビューアー アプリケーションの方が便利です。 サードパーティのいくつかのログ ビューアー アプリケーションは、Codeplex サイトからダウンロードでき、1 つのワークスペースで複数のトレース ログを表示できます。  
  
 次の手順には、Codeplex からダウンロードできる一般的な SharePoint ULS Log Viewer のリンクを示します。  
  
1.  CodePlex サイトの「 [SharePoint LogViewer](http://sharepointlogviewer.codeplex.com) 」または「 [SharePoint ULS Log Viewer](https://go.microsoft.com/fwlink/?LinkId=150052) 」に移動します。  
  
2.  [**ダウンロード**] タブをクリックします。  
  
3.  実行可能ファイルをクリックします。 
  **SharePointLogViewer.exe** または **ULS Viewer 2.0 Binary**のいずれかです。  
  
4.  使用許諾契約書を読み、同意します。  
  
5.  
  **[保存]** をクリックして、ソフトウェアをローカル システムにダウンロードします。  
  
     SharePoint ULS Log Viewer をダウンロードする場合は、ULSViewer.zip をダウンロード フォルダーに保存します。  
  
6.  ダウンロード フォルダーで、ULSViewer.zip を右クリックして、 **[すべて展開]** をクリックします。  
  
7.  展開先フォルダーを指定し、 **[展開]** をクリックします。  
  
8.  展開されたプログラム ファイルを含むフォルダーで、 **[ULSViewer]** をダブルクリックし、アプリケーションを実行します。  
  
9. アプリケーション ウィンドウの左上隅にあるフォルダー アイコンをクリックします。  
  
10. \Program files\Common Files\Microsoft Shared\Web Server Extensions\14\Logs を参照します。  
  
11. 1 つ以上のトレース ログを選択します。 既定では、トレース ログ ファイル名は、コンピューター名、日付、時刻の情報で構成されています。 ファイルの種類は、テキスト ドキュメントです。  
  
12. 
  **[開く]** をクリックし、ファイルが読み込まれるまで待機します。  
  
13. 組み込みフィルターを使用して、重大度、プロセス、カテゴリ、またはユーザー定義のテキスト ファイルに基づいてレコードを選択します。 また、列見出しをクリックして並べ替え順を変更することもできます。  
  
#### <a name="entries-for-powerpivot-services"></a>PowerPivot サービスのエントリ  
 次の表では、SharePoint ログ ファイルで検出される可能性が最も高い [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー操作のエントリについて説明します。  
  
|プロセス|領域|カテゴリ|Level|Message|詳細|  
|-------------|----------|--------------|-----------|-------------|-------------|  
|w3wp.exe|[PowerPivot サービス]|使用法|Verbose|現時点では要求の統計は存在せず、ログに記録するものはありません。|サービスは、事前に定義された間隔でクエリ応答統計を使用状況イベントとして使用状況データ収集システムに報告します。 このメッセージは、報告するクエリ統計がないことを示しています。|  
|w3wp.exe|[PowerPivot サービス]|Web フロント エンド|Verbose|データソース =\<*パス*のアプリケーションサーバーの検索を開始しています>|接続要求を受信すると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスは使用できる [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] を識別して要求を処理します。 ファーム内にサーバーが 1 台しかない場合は、すべての要求をローカル サーバーが受け取ります。|  
|w3wp.exe|[PowerPivot サービス]|Web フロント エンド|Verbose|アプリケーション サーバーの検索に成功しました。|要求は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションに割り当てられました。|  
|w3wp.exe|[PowerPivot サービス]|Web フロント エンド|Verbose|\< *Powerpivot データ source*> の要求をにリダイレクトし[!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]ています。|要求は [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]に転送されました。|  
|w3wp.exe|[PowerPivot サービス]|[要求の処理]|Verbose|ユーザー名\<*SharePoint ユーザー*> の要求をデータベースにリダイレクトしています|
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースへの権限を借用した接続が、SharePoint ユーザーの代わりに作成されました。|  
  
## <a name="see-also"></a>参照  
 [PowerPivot 使用状況データ収集](power-pivot-usage-data-collection.md)   
 [SQL Server セットアップログファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [&#40;PowerPivot for SharePoint の使用状況データ収集の構成](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
