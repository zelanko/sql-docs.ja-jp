---
title: SQL Server BI 機能の展開トポロジ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 2ba357fc3910779573ffa36f3070b55c08ced8ee
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388725"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>SharePoint の SQL Server BI 機能の配置トポロジ
  このトピックでは、SharePoint 2010 環境および SharePoint 2013 環境に SQL Server ビジネス インテリジェンス機能の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] をインストールする場合の一般的なトポロジについて説明します。 たとえば、1 つのサーバーと 3 つの層があるとします。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **このトピックの内容:**  
  
-   [SharePoint 2013 の配置トポロジの例](#bkmk_example_deployments_2013)  
  
    -   [PowerPivot for SharePoint 2013 と Reporting Services の 3 台のサーバー配置](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [PowerPivot for SharePoint 2013 のシングル サーバー配置](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [PowerPivot for SharePoint 2013 の 2 台のサーバー配置](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [PowerPivot for SharePoint 2013 の 3 台のサーバー配置](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot for SharePoint 2013 と Reporting Services の 1 台のサーバー配置](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [PowerPivot for SharePoint 2013 と Reporting Services の 2 台のサーバー配置](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [SharePoint 2010 の配置トポロジの例](#bkmk_example_deployments_2010)  
  
    -   [1 台のサーバー配置](#bkmk_sharepoint2010_1server)  
  
    -   [2 層配置](#bkmk_sharepoint2010_2server)  
  
    -   [3 層配置](#bkmk_sharepoint2010_3server)  
  
    -   [3 層スケールアウト配置](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="sharepoint-2013-example-deployment-topologies"></a><a name="bkmk_example_deployments_2013"></a>SharePoint 2013 の展開トポロジの例  
 SQL Server のセットアップ オプション **[PowerPivot for SharePoint]** には SharePoint との依存関係がなく、 統合をサポートする SharePoint オブジェクト モデルやインターフェイスは使用されません。 そのため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、Windows Server 2008 R2 以降のバージョンを実行する任意のコンピューターにインストールできます。 Analysis Services を SharePoint ファーム内のアプリケーション サーバーにすることもできますが、強制ではありません。 手順の 1 つは、Excel Services が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を実行しているサーバーを指すように構成することです。 負荷分散およびフォールト トレランスに関しては、SharePoint モードで実行している複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーをインストールし、登録することをお勧めします。  
  
 SharePoint モードには SharePoint サーバー 2013 が必要であり、SharePoint サービス アプリケーション アーキテクチャを利用します。 ** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **  
  
 次のセクションでは、一般的な配置トポロジについて説明します。  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-three-server-deployment"></a><a name="bkmk_bi_Sharepoint2013_3tier"></a>SharePoint 2013 およびレポート サービスの 3 台のサーバー展開の PowerPivot  
 次のような 3 台のサーバー配置では、SQL Server データベース エンジン、SharePoint モードで実行している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、および SharePoint を、それぞれ別のサーバーで実行します。 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 インストーラー パッケージ (**spPowerPivot.msi**) を SharePoint サーバーで実行する必要があります。  
  
 ![SSAS および SSRS SharePoint モード 3 のサーバー配置](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "SSAS および SSRS SharePoint モード 3 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
|**(4)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**(5)**|**spPowerPivot.msi** を実行し、データ プロバイダー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツール、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー、およびデータ更新スケジュールをインストールします。|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]サーバーを使用します。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(7)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
 ![SharePoint 設定](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")[マイクロソフト SQL Server 接続](https://connect.microsoft.com/SQLServer/Feedback)(https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="powerpivot-for-sharepoint-2013-single-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_1server"></a>SharePoint 2013 シングル サーバー展開の PowerPivot  
 シングル サーバー配置は、テスト目的には役立ちますが、運用環境の配置にはお勧めしません。  
  
 次の図は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のシングル サーバー配置に含まれるコンポーネントを示しています。  
  
 ![PowerPivot for SharePoint のシングル サーバー配置](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot for SharePoint のシングル サーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
|**(4)**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
  
###  <a name="powerpivot-for-sharepoint-2013-two-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_2server"></a>2 台のサーバー展開の PowerPivot  
 次のような 2 台のサーバー配置では、SQL Server データベース エンジンと SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を、SharePoint とは別のサーバーで実行します。 SharePoint 2013 では、 [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] インストーラー パッケージ (**spPowerPivot.msi**) は SharePoint サーバーにインストールされます。  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] によって、SharePoint Server 2013 が拡張され、サーバー側のデータ更新処理、データ プロバイダー、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーが追加され、高度なデータ モデルを使用した [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックや Excel ブックの管理がサポートされるようになりました。  
  
 インストーラー パッケージは、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 機能パックに付属しています。 機能パックは、マイクロソフトのダウンロード[!INCLUDE[msCoName](../../includes/msconame-md.md)]センターからダウンロードできます[® SQL Server ® 2014 PowerPivot®マイクロソフト® SharePoint® (](https://go.microsoft.com/fwlink/?LinkID=296473) HYPERLINK " " """"_blank"<https://go.microsoft.com/fwlink/?LinkID=296473> <https://go.microsoft.com/fwlink/?LinkID=296473>) をダウンロードできます。  
  
 ![SSAS PowerPivot モード 2 のサーバー配置](../../analysis-services/media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot モード 2 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|データ プロバイダー、構成ツール、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリー、およびスケジュール データ更新を[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]インストールするのには**spPowerPivot.msi**を実行します。|  
|**(4)**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(5)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
###  <a name="powerpivot-for-sharepoint-2013-three-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_3server"></a>SharePoint 2013 3 台のサーバー展開の PowerPivot  
 次のような 3 台のサーバー配置では、SQL Server データベース エンジン、SharePoint モードで実行している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、および SharePoint を、それぞれ別のサーバーで実行します。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 インストーラー パッケージ (spPowerPivot.msi) を SharePoint サーバーにインストールする必要があります。  
  
 ![AS PowerPivot モード 3 のサーバー配置](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "AS PowerPivot モード 3 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|spPowerPivot.msi を実行し、データ プロバイダー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツール、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー、およびデータ更新スケジュールをインストールします。|  
|**(4)**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(5)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-single-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a>SharePoint 2013 およびレポート サービスの単一サーバー展開の PowerPivot  
 シングル サーバー配置は、テスト目的には役立ちますが、運用環境の配置にはお勧めしません。  
  
 ![SSAS および SSRS SharePoint モード 1 サーバーの展開](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS および SSRS SharePoint モード 1 サーバーの展開")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|PowerPivot サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
|**(4)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**(5)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]サーバーを使用します。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-two-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a>SharePoint 2013 およびレポート サービス 2 つのサーバー展開の PowerPivot  
 次のような 2 台のサーバー配置では、SQL Server データベース エンジンと SharePoint モードで実行している Analysis Services サーバーを、SharePoint とは別のサーバーで実行します。 SharePoint 2013 インストーラー パッケージ **(spPowerPivot.msi) の PowerPivot を**SharePoint サーバーで実行する必要があります。  
  
 ![SSAS および SSRS SharePoint モード 2 のサーバー配置](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS および SSRS SharePoint モード 2 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|PowerPivot サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
|**(4)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**(5)**|**spPowerPivot.msi** を実行し、データ プロバイダー、PowerPivot 構成ツール、PowerPivot ギャラリーをインストールして、データ更新をスケジュールします。|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]サーバーを使用します。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(7)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
##  <a name="sharepoint-2010-example-deployment-topologies"></a><a name="bkmk_example_deployments_2010"></a>SharePoint 2010 の展開トポロジの例  
 次の図では、各階層で動作するサービスとプロバイダーを示します。 図に複数の組み込みサービスが含まれることに注意してください。これらのサービスは、一部の SQL Server BI シナリオで必要なものです。 Excel Services、Secure Store Services、および Claims to Windows Token Service は、SharePoint での PowerPivot for SharePoint または Reporting Services の配置に必要であるか、または推奨されます。 さらに、MSOLAP OLE DB プロバイダーと ADO.NET Services が、一部の PowerPivot データ アクセスのシナリオに必要です。 また、SharePoint の外部でホストされる表形式のモデル データベースに基づいて [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートを作成する場合は、必要に応じて、Analysis Services をデータ層にインストールできます。  
  
 ![論理アーキテクチャ図](../../../2014/sql-server/install/media/sql11bisetup.gif "論理アーキテクチャ図")  
  
##  <a name="single-server-deployments"></a><a name="bkmk_sharepoint2010_1server"></a>シングル サーバーの展開  
 データ層を含むすべてのサーバー コンポーネントを、1 台のコンピューターにインストールできます。 この配置構成は、ソフトウェアを評価する場合や、SharePoint モードの Reporting Services を含むカスタム アプリケーションを開発する場合に便利です。 この配置は、構成が最も簡単です。 すべてのコンポーネントを同じコンピューターにインストールするため、使用するライセンスの数も最も少なくなります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]、および [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのライセンス コピーとしてインストールされます。  
  
 すべての機能を 1 台のサーバーにインストールするには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を順番に同じ物理サーバーにインストールします。 スタンドアロン サーバー構成の手順については、「[展開チェックリスト: レポート サービス、Power View、PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)」を参照してください。  
  
##  <a name="two-tier-deployment"></a><a name="bkmk_sharepoint2010_2server"></a>2 層展開  
 2 層配置では、通常、SharePoint Server 2010 を 1 台のコンピューターに配置し、SQL Server データベース エンジンをもう 1 台のコンピューターに配置します。 2 コンピューター ファームで最も一般的な構成は、データ層を専用のサーバーに移動するものです。 2 層ファームでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を SharePoint サーバーにインストールします。 フロントエンドのすべての Web サービスと、アプリケーション層の共有サービスが、同じ物理サーバーで動作します。 2 層配置のインストール手順はスタンドアロン配置とよく似ており、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を順番に同じ物理サーバーにインストールします。  
  
##  <a name="three-tier-deployment"></a><a name="bkmk_sharepoint2010_3server"></a>3 層展開  
 3 層配置では、通常、Web フロントエンド サービスを、処理アプリケーションまたはメモリ多用アプリケーションから分離します。 このトポロジでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をアプリケーション サーバーだけにインストールします。 Web フロントエンドで実行される Web サービスは、サーバー構成の間のインストール後タスクとして、ファーム内のアプリケーションに配置されるソリューションを使用してインストールします。 次の図は 3 層配置を示したものです。  
  
 ![3 サーバー のトプロジー](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3 サーバー のトプロジー")  
  
##  <a name="three-tier-scale-out-deployment"></a><a name="bkmk_sharepoint2010_scaleserver"></a>3層スケールアウト展開  
 このトポロジでは、同じ共有サービスを複数のサーバーで実行するスケールアウト配置を示します。このトポロジを使用すると、大量の要求を処理し、PowerPivot データまたは Reporting Services レポートに対する処理能力を高めることができます。 次の図には 3 つのアプリケーション サーバー クラスターがあり、それぞれが共有サービスの異なる組み合わせを実行しています。 SharePoint 環境では、サービスの探索と可用性はファームに組み込まれます。 同じ共有サービス アプリケーションを実行する複数の物理サーバー間の負荷分散は、共有サービス アーキテクチャの一部です。  
  
 マルチサーバー ファームを配置するときは、SharePoint の記事「 [3 層ファーム用の複数サーバー (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834)」での指示に従ってください。  
  
 ![5 サーバー トポロジ](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "5 サーバー トポロジ")  
  
## <a name="see-also"></a>参照  
 [レポート サービス SharePoint 2010 および SharePoint 2013&#41;&#40;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [2013 年のインストール用の PowerPivot](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)   
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
