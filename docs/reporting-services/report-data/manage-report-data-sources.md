---
title: "レポート データ ソースを管理する | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レポート [Reporting Services], データ"
  - "パブリッシュされたレポート [Reporting Services], データ ソース接続"
  - "共有データ ソース [Reporting Services]"
  - "データ ソース [Reporting Services], 管理"
ms.assetid: 0475aded-c8fe-4337-a2b5-4df0ec4c46af
caps.latest.revision: 52
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 52
---
# レポート データ ソースを管理する
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート、レポート モデル、およびデータ ドリブン サブスクリプションが外部データ ソースからデータを取得します。 レポート サーバーは外部データ ソースに接続するために、レポート、モデル、またはサブスクリプションで定義または参照されているデータ ソース接続情報を使用します。 データ ソース接続プロパティは常に、レポートやモデルの作成時にそれらと共に定義されますが、レポートやモデルをレポート サーバーにパブリッシュした後は、それらとは別に管理できます。  
  
 レポート データ ソースを管理するには、ネイティブ モードのレポート サーバーの場合はレポート マネージャーを使用し、レポート サーバーを SharePoint 統合モードで配置した場合は SharePoint サイト上のアプリケーション ページを使用します。  
  
 データ ソース接続の管理には次のようなタスクが含まれます。このトピックで、これらのタスクについて説明します。  
  
-   接続文字列を変更する。  
  
-   資格情報を変更する。  
  
-   レポート サーバー上の共有データ ソースを作成および使用する (埋め込みデータ ソースから共有データ ソースへの切り替えを含む)。  
  
-   レポート、モデル、または使用する任意の共有データ ソースに対する権限を設定して、データ ソース プロパティへのアクセスを制御する。  
  
 クエリの変更はデータ ソース接続の管理には含まれません。 レポートやモデルのクエリを変更するには、レポート作成ツールを使用してレポートやモデルの定義に変更を加える必要があります。  
  
## マネージ プロパティ : データ ソースの種類、接続文字列、および資格情報  
 レポート サーバー上で管理できるデータ ソース プロパティは次のとおりです。  
  
|プロパティ|Description|管理する方法|  
|--------------|-----------------|----------------------|  
|[データ ソースの種類]|外部データに対して使用するレポート サーバーのデータ処理拡張機能を指定します。 データ プロセッサには、SQL Server、Analysis Services、Oracle などがあります。|データ ソースの種類は構成可能なため、マネージ プロパティです。 ただし、データ ソースの種類を構成するのは、新しい共有データ ソースを作成する場合だけにしてください。<br /><br /> パブリッシュされたレポートやモデルのプロパティ ページでデータ ソースの種類を変更しないでください。変更すると、ほぼ間違いなく接続が無効になります。 レポートやモデルで必要とされるデータ構造が別のデータ プラットフォームでも同じになることはまずありません。|  
|[接続文字列]|外部データ ソースへの初期接続を確立します。 レポートでは、静的な接続文字列を使用することも、動的な接続文字列を使用することもできます。<br /><br /> *静的な接続文字列*とは、レポートが実行されるたびに同じデータ ソースに接続するために常に使用される一連の値です。<br /><br /> *動的な接続文字列*とは、使用するデータ ソースをユーザーが実行時に選択できるようにするためにレポートに組み込まれる式です。 レポート デザイナーでレポートを作成するときに、式とデータ ソース選択一覧をレポートに組み込む必要があります。|接続文字列の変更は、データ ソースを別のコンピューターに移動する場合や、テスト データを使用して作成したレポートを、実稼働データベースを使用して配置する場合などに便利です。<br /><br /> 静的な接続文字列を管理する場合は、元の文字列を別の文字列に置き換えることができます。<br /><br /> レポート マネージャーまたは SharePoint サイトで動的な接続文字列を管理する場合は、静的な接続文字列に置き換えることしかできません。 式そのものを編集したり、データ ソース選択一覧を変更したりすることはできません。 式や有効な値の一覧を変更するには、レポート定義を編集して、レポート サーバーにパブリッシュし直す必要があります。 詳細については、「[データ接続、データ ソース、接続文字列 (レポート ビルダーと SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」を参照してください。|  
|[資格情報]|データ ソースのデータを読み取る権限を持っているユーザーの名前とパスワードを指定します。<br /><br /> データ ソースで認証がサポートされていない場合は (データ ソースがファイル システム上の XML ファイルの場合など)、自動実行アカウントを構成して、レポート サーバーが資格情報を渡さずに外部データ ソースに接続できるようにすることが可能です。|資格情報の管理では、ユーザー アカウントを更新したり、有効期限が切れたパスワードを更新したりすることができます。<br /><br /> そのほか、資格情報の取得方法を変更することもできます (実行時に資格情報の入力をユーザーに求めるなど)。<br /><br /> ユーザーがレポートをサブスクライブできるようにする場合は、保存された資格情報を使用するようにレポートを構成する必要があります。|  
  
## 共有データ ソースの作成と使用  
 データ ソース プロパティが埋め込まれたレポートをパブリッシュする場合は、共有データ ソース プロパティに切り替えることを検討してください。 資格情報や接続文字列を 1 つのページで更新できるので、共有データ ソースの方が管理が容易です。 そのデータ ソースを使用するすべてのレポート、モデル、およびデータ ドリブン サブスクリプションに、変更がすぐに反映されます。 また、共有データ ソースをオフラインにすると、レポートやサブスクリプションが事実上一時停止されるため、発生した問題のトラブルシューティングや調査を行っている間にそれらが実行されないようにすることができます。  
  
## データ ソース プロパティへのアクセスの制御  
 既定では、レポートを管理するための権限があれば誰でもレポートのすべてのプロパティを設定できます。これには、データ ソースの種類、接続文字列、資格情報、および接続情報の取得方法 (レポートに埋め込まれているか、共有データ ソースから取得するか) を決定するプロパティも含まれます。 ネイティブ モードのレポート サーバーのデータ ソース プロパティへのアクセスを制御するタスクと権限の詳細については、「[共有データ ソース アイテムをセキュリティで保護する](../../reporting-services/security/secure-shared-data-source-items.md)」と「[レポートとリソースの保護](../../reporting-services/security/secure-reports-and-resources.md)」を参照してください。  
  
 SharePoint ライブラリのアイテムのプロパティを表示および編集する権限は、サイトの管理者によって決定されます。 データ ソース接続プロパティを制御するアクセス許可については、「[レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)」を参照してください。  
  
## レポート サーバーでデータ ソース プロパティを操作する方法  
 データ ソース プロパティの作成や変更を行うには、さまざまなツールを使用できます。 次の表に、それらの方法およびツールと、詳しい手順へのリンクを示します。  
  
|タスク|ツール|リンク|  
|----------|----------|----------|  
|接続文字列の例を表示する。||[データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|データ ソースに接続するための資格情報を取得する方法を選択する。||[レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)|  
|データ ソース接続プロパティをレポート定義 (.rdl) ファイルに追加する。|レポート デザイナー|[埋め込みデータ ソースまたは共有データ ソースを作成する (SSRS)](../Topic/Create%20an%20Embedded%20or%20Shared%20Data%20Source%20\(SSRS\).md)|  
|共有データ ソース (.rds) ファイルをレポート プロジェクトに追加する/そのファイルへのリンクを設定する。|レポート デザイナー|[共有データ ソースを作成、変更、および削除する (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)|  
|ユーザーが実行時に選択できるデータ ソースの定義済み一覧を作成する。 ユーザーがレポートを要求すると、データ ソースの一覧が表示されます。 ユーザーは、レポートを実行する前に、使用するデータ ソースを選択する必要があります。 レポートにデータ ソース選択一覧を追加するには式を使用します。<br /><br /> これは、動的データ ソース接続と呼ばれます。|レポート デザイナー|[データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|レポート サーバー上の共有データ ソース アイテムを作成する。|レポート マネージャー|[共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)|  
|サブスクリプションやレポート スナップショットを作成するために必要な資格情報を格納する。|レポート マネージャー|[Store Credentials in a Reporting Services Data Source](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)|  
|パブリッシュされたレポートのデータ ソース接続プロパティを編集する。|レポート マネージャー|[レポートのデータ ソースのプロパティを構成する (レポート マネージャー)](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)|  
|レポート サーバー上の共有データ ソース アイテムを作成する。|SharePoint サイト|[共有データ ソースを作成および管理する (Reporting Services の SharePoint 統合モード)](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)|  
|既存の .odc 接続情報をレポートで使用する。|SharePoint サイト|[レポートで Office Data Connection (.odc) を使用する (Reporting Services の SharePoint 統合モード)](../../reporting-services/report-data/use an office data connection (.odc) with reports.md)|  
  
> [!NOTE]  
>  レポート データ ソースへのデータ ソース接続の管理と、レポート サーバー データベースへのレポート サーバー接続の管理は異なります。 内部データ ストアへのレポート サーバーの接続の詳細については、「[レポート サーバー データベース接続の構成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。  
  
## 参照  
 [レポートまたはモデルを共有データ ソースにバインドする (SSRS)](../../reporting-services/report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Store Credentials in a Reporting Services Data Source](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)   
 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Reporting Services でサポートされるデータ ソース (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)   
 [レポート サーバー コンテンツの管理 (SSRS ネイティブ モード)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  