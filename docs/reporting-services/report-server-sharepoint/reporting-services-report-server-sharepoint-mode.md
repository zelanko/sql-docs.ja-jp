---
title: "Reporting Services レポート サーバー (SharePoint モード) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a8cd1bd00ec92535fff73c5eaa4ff9bbe9274ef2
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---

# <a name="reporting-services-report-server-sharepoint-mode"></a>Reporting Services レポート サーバー (SharePoint モード)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  用に構成された Reporting Services レポート サーバー **SharePoint モード**SharePoint 製品の配置内で実行できます。 SharePoint モードのレポート サーバーは、レポートおよびその他の [!INCLUDE[ssRSnfoversion_md](../../includes/ssrsnoversion-md.md)] コンテンツの種類に対して、SharePoint のコラボレーション機能や管理機能を使用できます。 SharePoint モードでは、SharePoint Web フロント エンド上の SharePoint 製品用 Reporting Services アドインの適切なバージョンをインストールする必要があります。  
  
> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

 インストールと構成の詳細については、以下を参照してください。  
  
-   [SharePoint 2010 用 Reporting Services SharePoint モードのインストール](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c)です。  
  
-   [その他のレポート サーバーをファームに追加](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)です。  
  
## <a name="feature-summary"></a>機能の概要

 SharePoint 統合モードで動作するようにレポート サーバーを構成すると、次のことが可能になります。これらの追加機能はこのモードでレポート サーバーを配置した場合にのみ利用できます。  
  
-   SharePoint ドキュメント管理とコラボレーションの機能 (警告など) を使用できます。 SharePoint サイトは、すべてのレポート アイテムを 1 か所で利用および管理するための統合ポータルとして使用できます。  
  
-   SharePoint の権限と認証プロバイダーを使用して、レポート、モデル、その他のアイテムへのアクセスを制御できます。  
  
-   SharePoint の配置トポロジを使用して、ファイアウォール外のインターネット接続を経由してレポートを配信できます。 レポート サーバーでは、インターネット アクセス用に構成されている大規模な SharePoint 配置でレポートとデータを処理するサービスが提供されます。  
  
-   SharePoint サイトのカスタム アプリケーション ページで、レポート、モデル、データ ソース、スケジュール、レポート履歴を管理できます。 SharePoint サイトでは、プロパティの設定、スケジュールとサブスクリプションの定義、レポート履歴の作成と管理などを、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で他のツールを使って作成し管理するときと同じ方法で行うことができます。  
  
-   レポート、レポート モデル、リソース、および共有データ ソース ファイルを、Office SharePoint Server のレポート センターなどの SharePoint ライブラリにパブリッシュまたはアップロードできます。  
  
     レポート デザイナー、モデル デザイナー、およびレポート ビルダーを使用して、SharePoint ライブラリに直接パブリッシュするレポートおよびデータ ソースを作成します。 また、SharePoint サイトで [アップロード] アクションを使用して、レポート定義やレポート モデルを SharePoint ライブラリに追加することもできます。  
  
     レポート サーバーでは、使用しているサーバー モードに関係なく同じ方法でレポート定義が処理されるため、レポートのデータとレイアウトがサーバー モードの影響を受けることはありません。 ネイティブ モードのレポート サーバーで実行できるレポートであれば、SharePoint 統合モード用に構成されたレポート サーバーで実行できます。  
  
-   新しい SharePoint 配信拡張機能を使用して、SharePoint ライブラリに対しレポートのサブスクライブと配信を行うことができます。 電子メールや共有フォルダーを使ってレポートを配信することもできます。 レポートの配信にはレポート サーバーの配信拡張機能が使用されます。 実行時にクエリを行うサブスクライバー データを使用して、大規模なレポート配信用のデータ ドリブン サブスクリプションを作成できます。  
  
-   レポート ビューアー web パーツを SharePoint web アプリケーション内でレポートを表示する SharePoint ページに追加できます。 Web パーツには、ページ ナビゲーション、検索、印刷、および機能をエクスポートします。  
  
-   新しい SOAP エンドポイントに対してプログラムを実行し、SharePoint サイトと統合されるカスタム アプリケーションを作成できます。 更新された Windows Management Instrumentation (WMI) プロバイダーを使用して、SharePoint 統合モードで動作するレポート サーバー インスタンスをプログラムから構成することもできます。  
  
-   接続モードの Microsoft Access サービスのレポート機能。  
  
-   SharePoint リストの AAM 領域、インターネットに直接つながっている配置、および SharePoint ユーザー トークン。  
  
## <a name="connected-mode-and-local-mode"></a>接続モードとローカル モード

 SQL Server 2008 R2 リリースでは、SharePoint 2010 用 Microsoft SQL Server 2008 R2 以降の Reporting Services アドインがインストールされている SharePoint 2010 サーバーからレポートを表示するための新しい *ローカル モード* が導入されました。  
  
-   *ローカル モード*: ローカル モードでは、レポートを Reporting Services レポート サーバーと統合することがなく、SharePoint ドキュメント ライブラリからローカルに表示します。 SharePoint 製品用の Reporting Services アドインが必要ですが Reporting Services レポート サーバーはありません。 アドインは、いくつかの異なる方法でインストールできます (SharePoint 2010 製品準備ツールなど)。 ローカル モードの詳細については、次を参照してください。[ローカル モード レポート ビューアーで接続モードのレポートと](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md)と[SharePoint 製品用 Reporting Services アドインの検索先](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)です。  
  
-   *接続モード*: Reporting Services レポート サーバーを SharePoint サーバーの全体管理を使用して、SharePoint ファームに統合することで接続モードはサポートされています。 レポート サーバーとの統合により、完全なエンド ツー エンドのレポート処理が実現され、SharePoint 2010 のコラボレーション機能やレポート サーバーのサーバー ベースの機能 (サブスクリプション、スナップショット、サーバー ベースの処理など) が提供されます。  
  
## <a name="unsupported-sharepoint-features"></a>サポートされていない sharePoint 機能

 すべての SharePoint 機能が統合操作に使用できるわけではありません。 Reporting Services 直接統合していない SharePoint 機能の一覧を次に示します。  
  
-   Secure Store Service。  
  
-   ドキュメント ライブラリの Reporting Services ファイルに対して SharePoint Outlook カレンダー統合や SharePoint スケジュール機能を使用することはできません。  
  
-   SharePoint ビジネス データ カタログ。  
  
-   SharePoint のパーソナル化はまた、Reporting Services のページでサポートされていません。 SharePoint Web アプリケーションが匿名アクセスに対して有効になっている場合、レポート サーバー統合はサポートされません。  
  
-   SharePoint ドキュメント ライブラリのバージョン管理は、SQL Server Reporting Services では **サポートされません** 。 "ドキュメントの改版履歴" が有効なドキュメント ライブラリにレポート アイテムを保存した場合、Reporting Services の機能が正しく働かず、ULS ログにエラーが出力されます。 ULS ログに出力されるエラーの例を次に示します。  
  
    -   "レポートに関連付けられているデータ ソースが無効になっています。"  
  
     ドキュメント ライブラリのバージョン履歴は、"ライブラリ設定" の "バージョン設定" ページで構成されます。  
  
## <a name="supported-combinations-of-the-sharepoint-add-in-and-report-server"></a>SharePoint アドインとレポート サーバーのサポートされる組み合わせ

 レポート サーバー、SharePoint 用 Reporting Services アドイン、および SharePoint 製品のすべての組み合わせで、すべての機能がサポートされているわけではありません。 詳細については、次を参照してください[SharePoint および Reporting Services サーバーおよびアドインのサポートされる組み合わせ。](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
> [!NOTE]  
>  Reporting Services アドインの正しいバージョンを SharePoint 製品の対応するバージョンと共に使用する必要があります。  
  
## <a name="components-that-provide-integration"></a>統合を実現するコンポーネント

 インストールを統合する単一の展開内のサーバーを結合する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SharePoint 製品のインスタンスでの Reporting Services  
  
 統合は、によって提供される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と SharePoint 製品用 Reporting Services アドイン。 Reporting Services アドインを自由に配布のコンポーネントをダウンロードして、SharePoint の適切なバージョンを実行しているサーバーにインストールすることです。  
  
> [!TIP]  
>  レポート サーバー、SharePoint 用 Reporting Services アドイン、および SharePoint 製品のすべての組み合わせで、すべての機能がサポートされているわけではありません。 詳細については、「 [SharePoint および Reporting Services サーバーおよびアドインのサポートされる組み合わせ](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)です。  
  
-   Sharepoint で Reporting Services アドインを提供 ReportServer プロキシ エンドポイント、レポート ビューアー web パーツ、およびアプリケーション ページを表示、格納、および SharePoint サイトまたはファームでレポート サーバーのコンテンツを管理できるようにします。  
  
-   Reporting Services では、更新済みプログラム ファイル、SOAP エンドポイント、およびカスタム セキュリティおよび配信拡張機能を提供します。 レポート サーバーは、SharePoint 統合モードで実行し、レポートのアクセスと配信を SharePoint サイトのみで専用に行うように構成する必要があります。  
  
 SharePoint で Reporting Services アドインをインストールし、2 つのサーバーを統合用に構成した後にアップロードまたは、SharePoint ライブラリにレポート サーバー コンテンツ タイプを発行とし、表示して、SharePoint サイトからこれらのドキュメントを管理します。 アップロードとレポート サーバー コンテンツのパブリッシュは重要な最初の手順です。web パーツおよびページは、レポート定義 (.rdl) を選択して、レポート モデル (.smdl) および SharePoint サイト上のデータ ソース (.rsds) を共有するときに表示されます。  
  
##  <a name="language-considerations"></a>言語に関する注意点

 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 」および「 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 製品は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 SharePoint 製品の配置内で動作するようにレポート サーバーを構成すると、複数の言語が表示されることがあります。 ユーザー インターフェイス、ドキュメント、メッセージは次の言語で表示されます。  
  
-   すべてのアプリケーション ページ、ツール、エラー、警告、および Reporting Services から送信されるメッセージのいずれかで Reporting Services インスタンスによって使用される言語で表示されます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]言語です。  
  
-   SharePoint サイトでは、レポート ビューアー web パーツ、およびレポート ビルダーで開くアプリケーション ページは、Reporting Services アドインのサポートされている言語のいずれかで表示されます。 サポートされている言語の一覧を表示するには[SQL Server ダウンロード](http://msdn.microsoft.com/sql/downloads/)し、SQL Server 2016 Reporting Services アドインのダウンロード ページを見つけます。  
  
-   SharePoint サイト、SharePoint のサーバーの全体管理、オンライン ヘルプ、メッセージは、Office Server 製品でサポートされる言語で使用できます。  
  
 レポート サーバーの言語から、SharePoint 製品またはテクノロジの言語が異なる場合は、Reporting Services は最も近い一致を示す、同じ言語ファミリから言語を使用しようとします。 近い言語が使用できない場合、レポート サーバーでは英語が使用されます。  
  
## <a name="related-tasks"></a>関連タスク

 次の表には、Reporting Services SharePoint モードのレポート サーバーに関連するタスクをまとめたものです。  
  
|**タスク**|**リンク**|  
|--------------|--------------|  
|インストールと SharePoint モードで Reporting Services を構成する詳細な手順です。|[SharePoint 2010 用 Reporting Services SharePoint モードのインストール](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c)と[ファームに追加のレポート サーバーを追加](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)です。|  
|スケール アウト、Reporting Services SharePoint 配置でレポート サーバーの追加。|[その他のレポート サーバーをファームに追加](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)と[SharePoint での SQL Server BI 機能の配置トポロジ](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26)です。|  
|追加 SharePoint web フロント エンドが表示およびレポート アイテム用にインストールされて、Reporting Services コンポーネントを追加します。|[フロント エンド追加の Reporting Services web ファームを追加します。](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|SharePoint でレポート サーバーの電子メールを構成します。|[Reporting Services サービス アプリケーションの電子メールを構成します。](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|
|TechNet Wiki に掲載されている、今リリース向けの最新情報。|[SQL Server 2012 Reporting Services の役立つヒント、テクニック、およびトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=221297)です。|  

## <a name="next-steps"></a>次の手順

[インストールまたはつの sdd で Reporting Services を SharePoint のアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
[レポート ビューアー web パーツを SharePoint サイトで](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
[SSRS 2012 の SharePoint 統合の構成に関するクイズ](http://go.microsoft.com/fwlink/?LinkId=306443)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

