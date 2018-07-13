---
title: SharePoint (PowerPivot と Reporting Services) での SQL Server BI 機能のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 85ded5847bbb2bc1c32336e999b3579925a4e930
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325542"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>SharePoint を使用した SQL Server の BI 機能のインストール (PowerPivot と Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint での Business Intelligence (BI) 機能を有効にする Microsoft SharePoint ファームと統合できます。 機能が含まれます[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、および[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]します。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 使用は[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]SharePoint ファームでのデータ アクセス。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] は、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成され、SharePoint ライブラリからアクセスされるブック用のデータ エンジンです。 保存すると、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ブックを SharePoint には、使えるのデータ ソースとして[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]レポートします。  
  
 SharePoint 2010 で必要になるインストールと構成の手順は、SharePoint 2013 で必要な手順と一部異なります。 このセクションの一部のトピックは、SharePoint の両方のバージョンに適用されます。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 ![注](../../../2014/reporting-services/media/rs-fyinote.png "注")現在のリリース ノートについては、次を参照してください。 [SQL server 2014 リリース ノート](http://go.microsoft.com/fwlink/?LinkID=296445)します。  
  
##  <a name="bkmk_top"></a> このトピックの内容  
  
-   [SQL Server BI シナリオと SharePoint 2013](#bkmk_bi_scenarios)  
  
-   [インストールの概要](#bkmk_install_sharepoint2013_overview)  
  
## <a name="in-this-section"></a>このセクションの内容  
 このトピックの情報に加えて、次の関連項目は、このセクションの内容に含まれます。  
  
 [SharePoint の SQL Server BI 機能の配置トポロジ](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)  
  
 [SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイド](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
 [SharePoint を使用した BI 機能のインストール用チェック リスト](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)  
  
 [Reporting Services の SharePoint モード インストール&#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  
  
 [PowerPivot for SharePoint 2013 のインストール](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
##  <a name="bkmk_bi_scenarios"></a> SQL Server BI シナリオと SharePoint 2013  
 このセクションでは、インストールおよび構成するために選択できる、さまざまなレベルの BI 機能について説明します。  
  
 SharePoint 2013 の Excel Services には、ブラウザーで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを操作できるようにするためのデータ モデル機能が含まれます。 基本的なデータ モデルの機能にはデプロイする必要はありません、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 アドインをファームにします。 必要な操作は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーを SharePoint モードでインストールし、Excel Services の **[データ モデルの設定]** でサーバーを登録するだけです。  
  
 展開する、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013年アドイン機能を追加し、SharePoint ファームでの機能を使用します。 追加の機能[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリー、データ更新のスケジュール設定、および PowerPivot 管理ダッシュ ボード。 詳細については、表を参照してください。  
  
||Level|[機能]|インストールまたは構成|  
|-|-----------|--------------|--------------------------|  
|1|SharePoint のみ|Excel Services のネイティブ機能|SharePoint Server 2013 に含まれる Excel Services やその他のサービス。|  
|**2**|SharePoint モードの Analysis Services が統合された SharePoint|ブラウザー内での対話型の PowerPivot ブック|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を SharePoint モードでインストールします。<br /><br /> Excel Services で Analysis Services サーバーを登録します。|  
|**3**|SharePoint モードの Reporting Services が統合された SharePoint|Power View|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を SharePoint モードでインストールします。<br /><br /> インストール[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アドイン **(rsSharePoint.msi)** for SharePoint。 詳細については、次を参照してください[インストールまたは SharePoint 用 Reporting Services アドインのアンインストール&#40;SharePoint 2010 および SharePoint 2013。&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|PowerPivot のすべての機能|ファームの外部からのデータ ソースとしてのブックへのアクセス。<br /><br /> 定期データ更新。<br /><br /> PowerPivot ギャラリー。<br /><br /> 管理ダッシュボード。<br /><br /> BISM リンク ファイルのコンテンツの種類。|PowerPivot for SharePoint 2013 アドインを配置 **(spPowerPivot.msi)** します。 詳細については、以下を参照してください。<br /><br /> [For SharePoint アドインの PowerPivot のアンインストールをインストールまたは&#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> **spPowerPivot.msi**のダウンロード方法の詳細については、 [SQL Server 2014 PowerPivot for SharePoint のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=296473)を参照してください。|  
  
 有効化の詳細については[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]については、「[の SQL Server BI ライトアップ ストーリーの SharePoint 2013](http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx)します。  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> インストールの概要  
 両方を使用する場合[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]と[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、SQL Server インストール ウィザードを 2 回実行します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]は個別に選択、**セットアップ ロール**SQL Server セットアップ ウィザードのページ。  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] SharePoint 2010 と SharePoint 2013; の両方をサポートしていますただし、別のアーキテクチャとインストール プロセスは、SharePoint のバージョンによって使用されます。  
  
 シングル サーバーに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の BI 機能を配置するインストール手順の概要を以下に示します。  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 **SharePoint 2013**、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]インストールは、SharePoint 製品がインストールされていないサーバーで実行することができます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] SharePoint 2013 で使用されるアーキテクチャを実行**外**SharePoint ファームといずれかの SharePoint のインストールが含まれているサーバーにインストールすることができますもできますが存在しませんサーバーをインストール、SharePoint のインストール。  
  
1.  SharePoint Server 2013 をインストールし、Excel Services を有効にします。  
  
2.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を SharePoint モードでインストールし、SharePoint ファームおよびサービス アカウントに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のサーバー管理者権限を付与します。  
  
     SharePoint の両方のバージョン、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]のセットアップ ロールを選択してインストール プロセスが開始**SQL Server PowerPivot for SharePoint** SQL Server のインストール ウィザードまたは SQL Server のコマンド プロンプトを使用インストールします。  
  
     ![セットアップ ロール](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "セットアップ ロール")  
  
3.  For SharePoint 2013 を拡張することができます、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]機能とエクスペリエンス。 ダウンロードし、実行**spPowerPivot.msi**のサーバー側のデータ更新処理、コラボレーション、および管理サポートを追加する[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ブック。 詳細については、「 [Microsoft SQL Server 2014 PowerPivot for Microsoft® SharePoint](http://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。  
  
     実行、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013年のインストール パッケージ**spPowerPivot.msi**プロバイダーをインストールする各サーバーで SharePoint ファームのデータの正しいバージョンを確認します。  
  
4.  構成する[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]for SharePoint 2013 を使用して、 **PowerPivot for SharePoint 2013 構成**ツール。  
  
     2 つの SQL Server インストール ウィザードによってインストール[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]構成ツール。 構成ツールの 1 つは SharePoint 2013 をサポートし、もう 1 つは SharePoint 2010 をサポートします。  
  
     ![2 つの PowerPivot 構成ツール](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "2 つの PowerPivot 構成ツール")  
  
5.  SharePoint Server 2013 で、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを使用するように Excel Services を構成します。 詳細については、基本的な Analysis Services SharePoint 統合の構成」セクションを参照してください[PowerPivot for SharePoint 2013 インストール](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)それから[Excel Services の管理のデータ モデルの設定 (SharePoint Server2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx)します。  
  
6.  詳細については、次を参照してください。 [PowerPivot for SharePoint 2013 インストール](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)します。  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 SharePoint 2010 の場合、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインストールは、既に SharePoint 2010 がインストールされているサーバー、またはインストールする予定のサーバーで実行する必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] SharePoint 2010 のアーキテクチャを実行**内で**ファーム サーバーに SharePoint を必要とする[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]for SharePoint がインストールされています。  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を SharePoint モードでインストールし、SharePoint ファームおよびサービス アカウントに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のサーバー管理者権限を付与します。  
  
     SharePoint 2010 の配置は spPowerPivot.msi をサポートしません。この .msi は SharePoint 2010 には **不要** です。  
  
     SharePoint の両方のバージョン、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]のセットアップ ロールを選択してインストール プロセスが開始**SQL Server PowerPivot for SharePoint** SQL Server のインストール ウィザードまたは SQL Server のコマンド プロンプトを使用インストールします。  
  
2.  2 つの SQL Server インストール ウィザードによってインストール[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]構成ツール。 構成ツールの 1 つは SharePoint 2013 をサポートし、もう 1 つは SharePoint 2010 をサポートします。  
  
     構成する[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]for SharePoint 2010 を使用して、 **PowerPivot 構成ツール**します。  
  
3.  詳しくは、「 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)」をご覧ください。  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  SharePoint 2010 および 2013  
  
1.  インストール[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]sharepoint モードは、以前のリリースから変更されていません。  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 2010 および SharePoint 2013 のインストール手順は非常に似ています。 SharePoint のバージョンに関する重要な注意事項を次に示します。  
  
    -   次のサポートされる組み合わせを確認してください。  
  
        -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のバージョン。  
  
        -   SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン。  
  
        -   SharePoint 製品のバージョン。  
  
         [SharePoint と Reporting Services サーバーとアドインのサポートされる組み合わせ&#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   SharePoint 2010 の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には SharePoint 2010 Service Pack 2 (SP2) が必要です。  
  
    1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を SharePoint モードでインストールします。 [Reporting Services の SharePoint モード インストール&#40;SharePoint 2010 および SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)と[インストールの Reporting Services の SharePoint 2010 用の SharePoint モード](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)します。  
  
    2.  SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン (rsSharePoint.msi) をインストールします。 参照してください[インストールまたはアンインストール、Reporting Services アドイン、SharePoint の&#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)します。 現在のバージョンについて、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] for SharePoint アドインを参照してください[SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)します。  
  
    3.  構成、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービスと 1 つ以上[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーション。 詳細については、「Reporting Services サービス アプリケーションの作成」セクションを参照してください[Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)します。  
  
##  <a name="bkm_database_attach"></a> 概要のデータベース アタッチ アップグレードと SharePoint 2013  
 SharePoint 2013 では、インプレース アップグレードはサポートされていません。 ただし、 **データベース アタッチ アップグレードはサポートされています**。  
  
 SharePoint 2010 と統合された PowerPivot の既存のインストールを使用している場合は、SharePoint サーバーのインプレース アップグレードを行うことはできません。  ただし、SharePoint のデータベース アタッチ アップグレードの一環として以下の手順を実行できます。  
  
1.  新しい SharePoint Server 2013 ファームをインストールします。  
  
2.  SharePoint のデータベース アタッチ アップグレードを完了し、PowerPivot に関連するコンテンツ データベースを SharePoint 2013 ファームに移行します。  
  
3.  SharePoint モードで SQL Server Analysis Services のインスタンスをインストールし、SharePoint ファームおよびサービス アカウントのサーバー管理者権限を付与[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。  
  
4.  SharePoint ファーム内の各サーバーに PowerPivot for SharePoint 2013 のインストール パッケージ **spPowerPivot.msi** をインストールします。  
  
5.  [SharePoint 2013 サーバーの全体管理] で、手順 3. で作成した、SharePoint モードで実行している Analysis Services サーバーを使用するように Excel Services を構成します。  
  
     更新スケジュールを移行するには、PowerPivot サービス アプリケーションを構成します。  
  
> [!NOTE]  
>  PowerPivot および SharePoint データベース アタッチ アップグレードの詳細については、以下を参照してください。  
  
-   [SharePoint 2013 への PowerPivot の移行](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [SharePoint 2013 へのアップグレード プロセスの概要](http://go.microsoft.com/fwlink/p/?LinkId=256688)。  
  
-   [SharePoint 2013 へのアップグレードの前に環境をクリーンアップする](http://go.microsoft.com/fwlink/p/?LinkId=256689)  
  
-   [SharePoint 2010 から SharePoint 2013 にデータベースをアップグレードする](http://go.microsoft.com/fwlink/p/?LinkId=256690)。  
  
## <a name="see-also"></a>参照  
 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [SharePoint と Reporting Services サーバーとアドインのサポートされる組み合わせ&#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [インストールまたはアンインストール、Reporting Services アドイン、SharePoint の&#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
