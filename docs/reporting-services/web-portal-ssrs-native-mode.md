---
title: "Web ポータル (SSRS ネイティブ モード) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 7349e626-6ed5-4d21-b05f-cf042ad9ad70
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: e3dff8b613f933caa84522b31bdc862aa9c799f7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="web-portal-ssrs-native-mode"></a>Web ポータル (SSRS ネイティブ モード)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Reporting Services web ポータルは、モバイル レポート、Kpi、レポートを表示して、レポート サーバー インスタンス内にある要素を移動することができる web ベースのエクスペリエンスです。 また、1 つのレポート サーバー インスタンスに管理 web ポータルを使用することができます。

![ssRSPortal](../reporting-services/media/ssrsportal.png)

## <a name="what-is-the-web-portal"></a>Web ポータルとは

Web ポータルを使用するには、次のタスクを実行します。

- レポートの表示、検索、印刷、サブスクライブ。

- サーバー上のアイテムを整理するフォルダー階層の作成、セキュリティ保護、保守。

- アイテムおよび操作に対するアクセスを決定するロールベースのセキュリティの構成。

- レポート実行プロパティ、レポート履歴、レポート パラメーターの構成。

- スケジュールおよびデータ ソース接続をさらに管理しやすくする共有スケジュールおよび共有データ ソースの作成。

- 大きい受信者一覧にレポートをロール アウトするデータ ドリブン サブスクリプションの作成。

- 既存レポートの再利用や目的変更を行うための、リンク レポートの作成。

- Report Builder や Mobile Report Publisher など、一般的なツールのダウンロード。

- [KPI の作成](../reporting-services/working-with-kpis-in-reporting-services.md)。

- フィードバックや機能要求の送信。

Web ポータルを使用すると、特定のレポートの検索、レポート サーバー フォルダーを参照します。 レポート、その全般プロパティ、レポート履歴にキャプチャされているレポートの過去のコピーを表示できます。 権限に応じて、レポートにサブスクライブし、電子メールの受信ボックスやファイル システム上の共有フォルダーに配信させることもできます。

> [!NOTE]
> サポートされているブラウザーやバージョンの詳細については、「 [Reporting Services のブラウザー サポートの計画](../reporting-services/browser-support-for-reporting-services-and-power-view.md)」を参照してください。

Web ポータルは、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 SharePoint 統合モード用に構成されたレポート サーバーでは使用できません。

いくつかの web ポータル機能は、指定したエディションで利用できますのみ[!INCLUDE[ssNoVersion](../includes/ssnoversion.md)]です。 詳細については、次を参照してください。 [Reporting Services 機能が SQL Server 2016 の各エディションでサポートされている](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)です。

新しくインストールした場合、コンテンツおよび設定を操作するのに十分な権限を持っているのはローカル管理者のみです。 他のユーザーに権限を与えるには、ローカル管理者がレポート サーバーへのアクセスを許可するロールの割り当てを作成する必要があります。 ロールの割り当てが作成された後、ユーザーがアクセスできるようになるアプリケーション ページとタスクは、そのユーザーに対するロールの割り当てによって異なります。 詳細については、次を参照してください[、レポート サーバーにユーザー アクセスの許可。](security/grant-user-access-to-a-report-server-report-manager.md)

> [!NOTE]
> サーバーが実行されているローカル コンピューターで Web ポータルを閲覧している場合、このフォルダーの表示が禁止されている旨のメッセージが表示されることがあります。 これは Universal Access Control (UAC) による規制であり、また、ユーザーが管理者としてブラウザーを実行していないことに起因します。 管理者として Edge を実行することはできません。 Internet Explorer を使用する必要があります。 リモートでサーバーを閲覧するか、管理者として Internet Explorer を起動し、Web ポータルを閲覧できます。 Web ポータルをリモートで利用する場合、自分のアカウントにフォルダーのコンテンツ管理権限を与える必要があります。  

## <a name="start-and-use-the-web-portal"></a>Web ポータルの開始と使用

Web ポータルを入力して起動する web アプリケーションとは、[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]ブラウザー ウィンドウのアドレス バーの URL。 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]の起動時に表示されるページ、リンク、オプションは、レポート サーバーに対してユーザーが持っている権限によって異なります。 タスクを実行するには、そのタスクを含むロールに割り当てられている必要があります。  すべての権限を持つロールに割り当てられたユーザーは、レポート サーバーの管理に利用できるすべてのアプリケーション メニューとページにアクセスできます。 一方、レポートの表示と実行の権限を持つロールに割り当てられたユーザーは、それらの操作をサポートするメニューとページのみを表示できます。 各ユーザーに対して、レポート サーバーごとに異なるロールを割り当てることも、単一のレポート サーバーに保存されている多様なレポートまたはフォルダーごとに異なるロールを割り当てることもできます。

ロールの詳細については、「 [ネイティブ モードのレポート サーバーに対する権限の許可](../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)」を参照してください。

### <a name="start-the-web-portal"></a>Web ポータルを開始します。

ブラウザーから web ポータルを起動するには、次の操作を行います。

1. Web ブラウザーを開きます。 サポートされている Web ブラウザーの一覧は「 [Reporting Services のブラウザー サポートの計画](../reporting-services/browser-support-for-reporting-services-and-power-view.md)」でご確認いただけます。

2. Web ブラウザーのアドレス バーに入力 web ポータルの URL。

    既定の URL は *http://[ComputerName]/reports*です。

    レポート サーバーは、特定のポートを使用するように構成できます。 たとえば、 *http://[ComputerName]:80/repまたはts* または *http://[ComputerName]:8080/repまたはts*。

## <a name="grouping-by-categories"></a>カテゴリ別のグループ化

Web ポータルでは、さまざまなカテゴリに項目をグループ化されます。 次のようなカテゴリがあります。

- KPI
- モバイル レポート
- ページネーションのあるレポート
- Power BI Desktop レポート
- Excel ブック
- [データセット]
- データ ソース
- リソース

右上の **[表示]** を選択すると、表示内容を変更できます。 [非表示項目の表示] を選択した場合、そのアイテムは薄い色で表示されます。

![ssRSWebPortal-view](../reporting-services/media/ssrswebportal-view.png)

![ssRSWebPortal-hidden](../reporting-services/media/ssrswebportal-hidden.png)

### <a name="power-bi-desktop-reports-and-excel-workbooks"></a>Power BI Desktop レポートと Excel ブック

Power BI Desktop レポートと Excel ブックのアクセス許可をアップロード、整理、管理できます。 Web ポータル内でグループ化されます。

![ssRSWebPortal-view-pbi-and-excel](../reporting-services/media/ssrswebportal-view-pbi-and-excel.png)

ファイルは他のリソース ファイルと同様に Reporting Services 内に保管されます。 いずれかのアイテムを選択すると、デスクトップにローカル ダウンロードされます。 レポート サーバーに再アップロードすることで、変更を保存できます。

## <a name="search-for-items"></a>アイテムの検索

検索語句を入力できます。ユーザーがアクセスできるアイテムが表示されます。 結果は KPI、レポート、データセット、その他のアイテムに分類されます。 その後、結果を使用したり、お気に入りに追加したりできます。

![ssRSWebPortal-Search](../reporting-services/media/ssrswebportal-search.png)

## <a name="web-portal-tasks"></a>Web ポータル タスク

[Web ポータルのブランド化](../reporting-services/branding-the-web-portal.md)

[KPI の操作](../reporting-services/working-with-kpis-in-reporting-services.md)

[共有データセットの操作](../reporting-services/work-with-shared-datasets-web-portal.md)

## <a name="see-also"></a>参照

[SQL Server Mobile Report Publisher を使用してモバイル レポートを作成する](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
[URL の構成 (SSRS 構成マネージャー)](../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)  
[Reporting Services ツール](../reporting-services/tools/reporting-services-tools.md)  
[Reporting Services のブラウザー サポートの計画](../reporting-services/browser-support-for-reporting-services-and-power-view.md)  
[Reporting Services の機能が SQL Server 2016 の各エディションでサポートされています。](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)  

他に質問しますか。 [Reporting Services のフォーラムを再試行してください。](http://go.microsoft.com/fwlink/?LinkId=620231)
