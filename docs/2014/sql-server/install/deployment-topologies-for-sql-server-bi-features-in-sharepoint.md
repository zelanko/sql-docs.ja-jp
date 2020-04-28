---
title: SharePoint の SQL Server BI 機能の配置トポロジ |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388725"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>SharePoint の SQL Server BI 機能の配置トポロジ
  このトピックでは、SharePoint 2010 環境および SharePoint 2013 環境に SQL Server ビジネス インテリジェンス機能の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] をインストールする場合の一般的なトポロジについて説明します。 たとえば、1 つのサーバーと 3 つの層があるとします。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010|  
  
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
  
##  <a name="sharepoint-2013-example-deployment-topologies"></a><a name="bkmk_example_deployments_2013"></a>SharePoint 2013 配置トポロジの例  
 SQL Server のセットアップ オプション **[PowerPivot for SharePoint]** には SharePoint との依存関係がなく、 統合をサポートする SharePoint オブジェクト モデルやインターフェイスは使用されません。 そのため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、Windows Server 2008 R2 以降のバージョンを実行する任意のコンピューターにインストールできます。 Analysis Services を SharePoint ファーム内のアプリケーション サーバーにすることもできますが、強制ではありません。 手順の 1 つは、Excel Services が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を実行しているサーバーを指すように構成することです。 負荷分散およびフォールト トレランスに関しては、SharePoint モードで実行している複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーをインストールし、登録することをお勧めします。  
  
 Sharepoint モードでは sharepoint server 2013 が必要であり、sharepoint サービスアプリケーションアーキテクチャを利用します。 ** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **  
  
 次のセクションでは、一般的な配置トポロジについて説明します。  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-three-server-deployment"></a><a name="bkmk_bi_Sharepoint2013_3tier"></a>PowerPivot for SharePoint 2013 と Reporting Services 3 台のサーバー配置  
 次のような 3 台のサーバー配置では、SQL Server データベース エンジン、SharePoint モードで実行している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、および SharePoint を、それぞれ別のサーバーで実行します。 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 インストーラー パッケージ (**spPowerPivot.msi**) を SharePoint サーバーで実行する必要があります。  
  
 ![SSAS および SSRS SharePoint モード 3 のサーバー配置](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "SSAS および SSRS SharePoint モード 3 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**3**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービスアプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**番**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
|**4/4**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**5/5**|**spPowerPivot.msi** を実行し、データ プロバイダー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツール、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー、およびデータ更新スケジュールをインストールします。|  
|**4/6**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]SharePoint モードのサーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**7**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
 ![SharePoint の設定](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")では Microsoft SQL Server Connect (https://connect.microsoft.com/SQLServer/Feedback))[を使用してフィードバックと連絡先情報を送信し](https://connect.microsoft.com/SQLServer/Feedback)ます。  
  
###  <a name="powerpivot-for-sharepoint-2013-single-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_1server"></a>PowerPivot for SharePoint 2013 のシングルサーバー配置  
 シングル サーバー配置は、テスト目的には役立ちますが、運用環境の配置にはお勧めしません。  
  
 次の図は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のシングル サーバー配置に含まれるコンポーネントを示しています。  
  
 ![PowerPivot for SharePoint のシングル サーバー配置](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot for SharePoint のシングル サーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**3**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービスアプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**番**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
|**4/4**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
  
###  <a name="powerpivot-for-sharepoint-2013-two-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_2server"></a>PowerPivot for SharePoint 2013 2 サーバーの展開  
 次のような 2 台のサーバー配置では、SQL Server データベース エンジンと SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を、SharePoint とは別のサーバーで実行します。 SharePoint 2013 では、 [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] インストーラー パッケージ (**spPowerPivot.msi**) は SharePoint サーバーにインストールされます。  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] によって、SharePoint Server 2013 が拡張され、サーバー側のデータ更新処理、データ プロバイダー、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーが追加され、高度なデータ モデルを使用した [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックや Excel ブックの管理がサポートされるようになりました。  
  
 インストーラー パッケージは、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 機能パックに付属しています。 Feature pack [!INCLUDE[msCoName](../../includes/msconame-md.md)]は、ダウンロードセンターの microsoft [® SQL Server® 2014 PowerPivot® For microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (HYPERLINK "<https://go.microsoft.com/fwlink/?LinkID=296473>" \t "_blank" <https://go.microsoft.com/fwlink/?LinkID=296473>) からダウンロードできます。  
  
 ![SSAS PowerPivot モード 2 のサーバー配置](../../analysis-services/media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot モード 2 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**3**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービスアプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**番**|**Sppowerpivot .msi**を実行して、データプロバイダー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]構成ツール、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリー、およびデータ更新スケジュールをインストールします。|  
|**4/4**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**5/5**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
###  <a name="powerpivot-for-sharepoint-2013-three-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_3server"></a>PowerPivot for SharePoint 2013 3 サーバーの展開  
 次のような 3 台のサーバー配置では、SQL Server データベース エンジン、SharePoint モードで実行している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、および SharePoint を、それぞれ別のサーバーで実行します。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 インストーラー パッケージ (spPowerPivot.msi) を SharePoint サーバーにインストールする必要があります。  
  
 ![AS PowerPivot モード 3 のサーバー配置](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "AS PowerPivot モード 3 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**3**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービスアプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**番**|spPowerPivot.msi を実行し、データ プロバイダー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツール、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー、およびデータ更新スケジュールをインストールします。|  
|**4/4**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**5/5**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-single-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a>PowerPivot for SharePoint 2013 と Reporting Services 単一サーバー配置  
 シングル サーバー配置は、テスト目的には役立ちますが、運用環境の配置にはお勧めしません。  
  
 ![SSAS および SSRS SharePoint モード1サーバー配置](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS および SSRS SharePoint モード1サーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**3**|PowerPivot サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**番**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
|**4/4**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**5/5**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
|**4/6**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]SharePoint モードのサーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-two-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a>PowerPivot for SharePoint 2013 と Reporting Services 2 台のサーバー配置  
 次のような 2 台のサーバー配置では、SQL Server データベース エンジンと SharePoint モードで実行している Analysis Services サーバーを、SharePoint とは別のサーバーで実行します。 PowerPivot for SharePoint 2013 インストーラーパッケージ **(Sppowerpivot .msi)** を SharePoint サーバーで実行する必要があります。  
  
 ![SSAS および SSRS SharePoint モード 2 のサーバー配置](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS および SSRS SharePoint モード 2 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**3**|PowerPivot サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**番**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
|**4/4**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**5/5**|**spPowerPivot.msi** を実行し、データ プロバイダー、PowerPivot 構成ツール、PowerPivot ギャラリーをインストールして、データ更新をスケジュールします。|  
|**4/6**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]SharePoint モードのサーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**7**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
##  <a name="sharepoint-2010-example-deployment-topologies"></a><a name="bkmk_example_deployments_2010"></a>SharePoint 2010 配置トポロジの例  
 次の図では、各階層で動作するサービスとプロバイダーを示します。 図に複数の組み込みサービスが含まれることに注意してください。これらのサービスは、一部の SQL Server BI シナリオで必要なものです。 Excel Services、Secure Store Services、および Claims to Windows Token Service は、SharePoint での PowerPivot for SharePoint または Reporting Services の配置に必要であるか、または推奨されます。 さらに、MSOLAP OLE DB プロバイダーと ADO.NET Services が、一部の PowerPivot データ アクセスのシナリオに必要です。 また、SharePoint の外部でホストされる表形式のモデル データベースに基づいて [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートを作成する場合は、必要に応じて、Analysis Services をデータ層にインストールできます。  
  
 ![論理アーキテクチャ図](../../../2014/sql-server/install/media/sql11bisetup.gif "論理アーキテクチャ図")  
  
##  <a name="single-server-deployments"></a><a name="bkmk_sharepoint2010_1server"></a>単一サーバー配置  
 データ層を含むすべてのサーバー コンポーネントを、1 台のコンピューターにインストールできます。 この配置構成は、ソフトウェアを評価する場合や、SharePoint モードの Reporting Services を含むカスタム アプリケーションを開発する場合に便利です。 この配置は、構成が最も簡単です。 すべてのコンポーネントを同じコンピューターにインストールするため、使用するライセンスの数も最も少なくなります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]、および [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのライセンス コピーとしてインストールされます。  
  
 すべての機能を 1 台のサーバーにインストールするには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を順番に同じ物理サーバーにインストールします。 スタンドアロンサーバー構成の手順については、「[配置チェックリスト: Reporting Services、Power View、および PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)」を参照してください。  
  
##  <a name="two-tier-deployment"></a><a name="bkmk_sharepoint2010_2server"></a>2層配置  
 2 層配置では、通常、SharePoint Server 2010 を 1 台のコンピューターに配置し、SQL Server データベース エンジンをもう 1 台のコンピューターに配置します。 2 コンピューター ファームで最も一般的な構成は、データ層を専用のサーバーに移動するものです。 2 層ファームでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を SharePoint サーバーにインストールします。 フロントエンドのすべての Web サービスと、アプリケーション層の共有サービスが、同じ物理サーバーで動作します。 2 層配置のインストール手順はスタンドアロン配置とよく似ており、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を順番に同じ物理サーバーにインストールします。  
  
##  <a name="three-tier-deployment"></a><a name="bkmk_sharepoint2010_3server"></a>3層配置  
 3 層配置では、通常、Web フロントエンド サービスを、処理アプリケーションまたはメモリ多用アプリケーションから分離します。 このトポロジでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をアプリケーション サーバーだけにインストールします。 Web フロントエンドで実行される Web サービスは、サーバー構成の間のインストール後タスクとして、ファーム内のアプリケーションに配置されるソリューションを使用してインストールします。 次の図は 3 層配置を示したものです。  
  
 ![3-サーバートポロジ](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3-サーバートポロジ")  
  
##  <a name="three-tier-scale-out-deployment"></a><a name="bkmk_sharepoint2010_scaleserver"></a>3層スケールアウト配置  
 このトポロジでは、同じ共有サービスを複数のサーバーで実行するスケールアウト配置を示します。このトポロジを使用すると、大量の要求を処理し、PowerPivot データまたは Reporting Services レポートに対する処理能力を高めることができます。 次の図には 3 つのアプリケーション サーバー クラスターがあり、それぞれが共有サービスの異なる組み合わせを実行しています。 SharePoint 環境では、サービスの探索と可用性はファームに組み込まれます。 同じ共有サービス アプリケーションを実行する複数の物理サーバー間の負荷分散は、共有サービス アーキテクチャの一部です。  
  
 マルチサーバー ファームを配置するときは、SharePoint の記事「 [3 層ファーム用の複数サーバー (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834)」での指示に従ってください。  
  
 ![5 サーバー トポロジ](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "5 サーバー トポロジ")  
  
## <a name="see-also"></a>参照  
 [Sharepoint モードのインストール Reporting Services sharepoint 2010 および SharePoint 2013&#41;&#40;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [PowerPivot for SharePoint 2013 のインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)   
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
