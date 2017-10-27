---
title: "レポート データ ソースの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reports [Reporting Services], data
- published reports [Reporting Services], data source connections
- shared data sources [Reporting Services]
- data sources [Reporting Services], managing
ms.assetid: 0475aded-c8fe-4337-a2b5-4df0ec4c46af
caps.latest.revision: 52
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9791cd34a321173e30bf2016956f02e54e62112c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="manage-report-data-sources"></a>レポート データ ソースを管理する
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート、レポート モデル、およびデータ ドリブン サブスクリプションが外部データ ソースからデータを取得します。 レポート サーバーは外部データ ソースに接続するために、レポート、モデル、またはサブスクリプションで定義または参照されているデータ ソース接続情報を使用します。 データ ソース接続プロパティは常に、レポートやモデルの作成時にそれらと共に定義されますが、レポートやモデルをレポート サーバーにパブリッシュした後は、それらとは別に管理できます。  
  
 レポート データ ソースを管理するには、ネイティブ モードのレポート サーバーの場合はレポート マネージャーを使用し、レポート サーバーを SharePoint 統合モードで配置した場合は SharePoint サイト上のアプリケーション ページを使用します。  
  
 データ ソース接続の管理には次のようなタスクが含まれます。このトピックで、これらのタスクについて説明します。  
  
-   接続文字列を変更する。  
  
-   資格情報を変更する。  
  
-   レポート サーバー上の共有データ ソースを作成および使用する (埋め込みデータ ソースから共有データ ソースへの切り替えを含む)。  
  
-   レポート、モデル、または使用する任意の共有データ ソースに対する権限を設定して、データ ソース プロパティへのアクセスを制御する。  
  
 クエリの変更はデータ ソース接続の管理には含まれません。 レポートやモデルのクエリを変更するには、レポート作成ツールを使用してレポートやモデルの定義に変更を加える必要があります。  
  
## <a name="managed-properties-data-source-type-connection-strings-and-credentials"></a>マネージ プロパティ : データ ソースの種類、接続文字列、および資格情報  
 レポート サーバー上で管理できるデータ ソース プロパティは次のとおりです。  
  
|プロパティ|Description|管理する方法|  
|--------------|-----------------|----------------------|  
|[データ ソースの種類]|外部データに対して使用するレポート サーバーのデータ処理拡張機能を指定します。 データ プロセッサには、SQL Server、Analysis Services、Oracle などがあります。|データ ソースの種類は構成可能なため、マネージ プロパティです。 ただし、データ ソースの種類を構成するのは、新しい共有データ ソースを作成する場合だけにしてください。<br /><br /> パブリッシュされたレポートやモデルのプロパティ ページでデータ ソースの種類を変更しないでください。変更すると、ほぼ間違いなく接続が無効になります。 レポートやモデルで必要とされるデータ構造が別のデータ プラットフォームでも同じになることはまずありません。|  
|[接続文字列]|外部データ ソースへの初期接続を確立します。 レポートでは、静的な接続文字列を使用することも、動的な接続文字列を使用することもできます。<br /><br /> *静的な接続文字列* とは、レポートが実行されるたびに同じデータ ソースに接続するために常に使用される一連の値です。<br /><br /> *動的な接続文字列* とは、使用するデータ ソースをユーザーが実行時に選択できるようにするためにレポートに組み込まれる式です。 レポート デザイナーでレポートを作成するときに、式とデータ ソース選択一覧をレポートに組み込む必要があります。|接続文字列の変更は、データ ソースを別のコンピューターに移動する場合や、テスト データを使用して作成したレポートを、実稼働データベースを使用して配置する場合などに便利です。<br /><br /> 静的な接続文字列を管理する場合は、元の文字列を別の文字列に置き換えることができます。<br /><br /> レポート マネージャーまたは SharePoint サイトで動的な接続文字列を管理する場合は、静的な接続文字列に置き換えることしかできません。 式そのものを編集したり、データ ソース選択一覧を変更したりすることはできません。 式や有効な値の一覧を変更するには、レポート定義を編集して、レポート サーバーにパブリッシュし直す必要があります。 詳細については、「 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」を参照してください。|  
|[資格情報]|データ ソースのデータを読み取る権限を持っているユーザーの名前とパスワードを指定します。<br /><br /> データ ソースで認証がサポートされていない場合は (データ ソースがファイル システム上の XML ファイルの場合など)、自動実行アカウントを構成して、レポート サーバーが資格情報を渡さずに外部データ ソースに接続できるようにすることが可能です。|資格情報の管理では、ユーザー アカウントを更新したり、有効期限が切れたパスワードを更新したりすることができます。<br /><br /> そのほか、資格情報の取得方法を変更することもできます (実行時に資格情報の入力をユーザーに求めるなど)。<br /><br /> ユーザーがレポートをサブスクライブできるようにする場合は、保存された資格情報を使用するようにレポートを構成する必要があります。|  
  
## <a name="creating-and-using-shared-data-sources"></a>共有データ ソースの作成と使用  
 データ ソース プロパティが埋め込まれたレポートをパブリッシュする場合は、共有データ ソース プロパティに切り替えることを検討してください。 資格情報や接続文字列を 1 つのページで更新できるので、共有データ ソースの方が管理が容易です。 そのデータ ソースを使用するすべてのレポート、モデル、およびデータ ドリブン サブスクリプションに、変更がすぐに反映されます。 また、共有データ ソースをオフラインにすると、レポートやサブスクリプションが事実上一時停止されるため、発生した問題のトラブルシューティングや調査を行っている間にそれらが実行されないようにすることができます。  
  
## <a name="controlling-access-data-source-properties"></a>データ ソース プロパティへのアクセスの制御  
 既定では、レポートを管理するための権限があれば誰でもレポートのすべてのプロパティを設定できます。これには、データ ソースの種類、接続文字列、資格情報、および接続情報の取得方法 (レポートに埋め込まれているか、共有データ ソースから取得するか) を決定するプロパティも含まれます。 ネイティブ モードのレポート サーバーのデータ ソース プロパティへのアクセスを制御するタスクと権限の詳細については、「 [共有データ ソース アイテムをセキュリティで保護する](../../reporting-services/security/secure-shared-data-source-items.md) 」と「 [レポートとリソースの保護](../../reporting-services/security/secure-reports-and-resources.md)」を参照してください。  
  
 SharePoint ライブラリのアイテムのプロパティを表示および編集する権限は、サイトの管理者によって決定されます。 データ ソース接続プロパティを制御するアクセス許可については、「 [レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)」を参照してください。  
  
## <a name="how-to-work-with-data-source-properties-on-a-report-server"></a>レポート サーバーでデータ ソース プロパティを操作する方法  
 データ ソース プロパティの作成や変更を行うには、さまざまなツールを使用できます。 次の表に、それらの方法およびツールと、詳しい手順へのリンクを示します。  
  
|タスク|ツール|リンク|  
|----------|----------|----------|  
|接続文字列の例を表示する。||[データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|データ ソースに接続するための資格情報を取得する方法を選択する。||[資格情報とレポート データ ソースの接続情報を指定します。](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)|  
|データ ソース接続プロパティをレポート定義 (.rdl) ファイルに追加する。|レポート デザイナー|[埋め込みまたは共有データ ソース &#40; を作成します。SSRS &#41;](http://msdn.microsoft.com/library/b111a8d0-a60d-4c8b-b00a-51644b19c34b)|  
|共有データ ソース (.rds) ファイルをレポート プロジェクトに追加する/そのファイルへのリンクを設定する。|レポート デザイナー|[作成、変更、および共有データ ソース &#40; を削除SSRS &#41;](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)|  
|ユーザーが実行時に選択できるデータ ソースの定義済み一覧を作成する。 ユーザーがレポートを要求すると、データ ソースの一覧が表示されます。 ユーザーは、レポートを実行する前に、使用するデータ ソースを選択する必要があります。 レポートにデータ ソース選択一覧を追加するには式を使用します。<br /><br /> これは、動的データ ソース接続と呼ばれます。|レポート デザイナー|[データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|レポート サーバー上の共有データ ソース アイテムを作成する。|レポート マネージャー|[作成、削除、または共有データ ソース &#40; を変更レポート マネージャー &#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)|  
|サブスクリプションやレポート スナップショットを作成するために必要な資格情報を格納する。|レポート マネージャー|[Reporting Services データ ソースの資格情報を保存します。](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)|  
|パブリッシュされたレポートのデータ ソース接続プロパティを編集する。|レポート マネージャー|[レポート &#40; のデータ ソースのプロパティを構成します。レポート マネージャー &#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)|  
|レポート サーバー上の共有データ ソース アイテムを作成する。|SharePoint サイト|[共有データ ソースを作成および管理する &#40;Reporting Services の SharePoint 統合モード&#41;](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)|  
|既存の .odc 接続情報をレポートで使用する。|SharePoint サイト|[Office データ接続 &#40; を使用します。odc &#41;でレポートと #40 です。Reporting Services の SharePoint モード &#41; と統合](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)|  
  
> [!NOTE]  
>  レポート データ ソースへのデータ ソース接続の管理と、レポート サーバー データベースへのレポート サーバー接続の管理は異なります。 内部データ ストアへのレポート サーバーの接続の詳細については、「[レポート サーバー データベース接続の構成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポートまたはモデル、共有データ ソース &#40; をバインドします。SSRS &#41;](../../reporting-services/report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [共有データ ソースの作成、削除、または変更 &#40;レポート マネージャー&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Reporting Services データ ソースの資格情報を保存します。](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)   
 [データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Reporting Services &#40; でサポートされるデータ ソースSSRS &#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)   
 [レポート サーバー コンテンツの管理 & #40 です。SSRS ネイティブ モード &#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  

