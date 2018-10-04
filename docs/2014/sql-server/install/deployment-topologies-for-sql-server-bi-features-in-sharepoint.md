---
title: SharePoint での SQL Server BI 機能の配置トポロジ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e1a24a1453fef96347d07df3cbe9d95263b45de2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079512"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>SharePoint の SQL Server BI 機能の配置トポロジ
  このトピックでは、SharePoint 2010 環境および SharePoint 2013 環境に SQL Server ビジネス インテリジェンス機能の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] をインストールする場合の一般的なトポロジについて説明します。 たとえば、1 つのサーバーと 3 つの層があるとします。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **このトピックの内容:**  
  
-   [SharePoint 2013 の配置トポロジの例](#bkmk_example_deployments_2013)  
  
    -   [PowerPivot for SharePoint 2013 と Reporting Services の 3 つのサーバー配置](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [PowerPivot for SharePoint 2013 のシングル サーバー配置](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [PowerPivot for SharePoint 2013 の 2 つのサーバー配置](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [PowerPivot for SharePoint 2013 の 3 つのサーバー配置](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot for SharePoint 2013 と Reporting Services のシングル サーバー配置](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [PowerPivot for SharePoint 2013 と Reporting Services の 2 つのサーバー配置](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [SharePoint 2010 の配置トポロジの例](#bkmk_example_deployments_2010)  
  
    -   [シングル サーバー配置](#bkmk_sharepoint2010_1server)  
  
    -   [2 層の展開](#bkmk_sharepoint2010_2server)  
  
    -   [3 層配置](#bkmk_sharepoint2010_3server)  
  
    -   [3 層のスケール アウト配置](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="bkmk_example_deployments_2013"></a> SharePoint 2013 の配置トポロジの例  
 SQL Server のセットアップ オプション **[PowerPivot for SharePoint]** には SharePoint との依存関係がなく、 統合をサポートする SharePoint オブジェクト モデルやインターフェイスは使用されません。 そのため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Windows Server 2008 R2 またはそれ以降のバージョンを実行するコンピューターにインストールできます。 Analysis Services を SharePoint ファーム内のアプリケーション サーバーにすることもできますが、強制ではありません。 手順の 1 つは、Excel Services が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を実行しているサーバーを指すように構成することです。 負荷分散およびフォールト トレランスに関しては、SharePoint モードで実行している複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーをインストールし、登録することをお勧めします。  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード**SharePoint server 2013 が必要ですし、SharePoint サービス アプリケーションのアーキテクチャを採用しています。  
  
 次のセクションでは、一般的な配置トポロジについて説明します。  
  
###  <a name="bkmk_bi_Sharepoint2013_3tier"></a> PowerPivot for SharePoint 2013 と Reporting Services の 3 つのサーバー配置  
 次の 3 台のサーバー配置で、SQL Server データベース エンジンで[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]SharePoint モードおよび SharePoint を別のサーバーで実行するたびに実行しているサーバー。 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013年インストーラー パッケージ (**spPowerPivot.msi**) SharePoint サーバーで実行する必要があります。  
  
 ![SSAS および SSRS SharePoint モード 3 サーバーの展開](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "SSAS および SSRS SharePoint モード 3 サーバーの展開")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション。|  
|**(4)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**(5)**|実行、 **spPowerPivot.msi** 、データ プロバイダーをインストールする、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]構成ツール、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリー、およびデータ更新をスケジュールします。|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SharePoint モードのサーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(7)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
 ![SharePoint の設定](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")[フィードバックや連絡先の情報を Microsoft SQL Server の接続を介して送信](https://connect.microsoft.com/SQLServer/Feedback)(https://connect.microsoft.com/SQLServer/Feedback)します。  
  
###  <a name="bkmk_powerpivot_sharepoint2013_1server"></a> PowerPivot for SharePoint 2013 のシングル サーバー配置  
 シングル サーバー配置は、テスト目的には役立ちますが、運用環境の配置にはお勧めしません。  
  
 次の図は、単一のサーバーの一部であるコンポーネントを示しています。[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]展開します。  
  
 ![PowerPivot for SharePoint のシングル サーバー配置](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot for SharePoint のシングル サーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
|**(4)**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_2server"></a> PowerPivot for SharePoint 2013 の 2 つのサーバー配置  
 次の 2 台のサーバー配置は、SQL Server データベース エンジンと[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の SharePoint モードの SharePoint とは異なるサーバー上で実行します。 SharePoint 2013 の場合、[!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)]インストーラー パッケージ (**spPowerPivot.msi**) SharePoint サーバーにインストールされます。  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] SharePoint Server 2013 にサーバー側のデータ更新処理、追加、データ プロバイダーの拡張[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリー、および管理サポート[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ブックや Excel ブックでは、データ モデルを高度な。  
  
 インストーラー パッケージは、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 機能パックに付属しています。 Feature pack をダウンロードすることができます、[!INCLUDE[msCoName](../../includes/msconame-md.md)]ダウンロード センターの「 [Microsoft® SharePoint® 用 Microsoft® SQL Server® 2014 PowerPivot®](http://go.microsoft.com/fwlink/?LinkID=296473) (HYPERLINK"http://go.microsoft.com/fwlink/?LinkID=296473"\t"_blank"http://go.microsoft.com/fwlink/?LinkID=296473)します。  
  
 ![SSAS PowerPivot モード 2 のサーバー配置](../../../2014/analysis-services/media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot モード 2 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|実行、 **spPowerPivot.msi** 、データ プロバイダーをインストールする、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]構成ツール、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ギャラリー、およびデータ更新をスケジュールします。|  
|**(4)**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(5)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_3server"></a> PowerPivot for SharePoint 2013 の 3 つのサーバー配置  
 次の 3 台のサーバー配置で、SQL Server データベース エンジンで[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]SharePoint モードおよび SharePoint を別のサーバーで実行するたびに実行しているサーバー。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 インストーラー パッケージ (spPowerPivot.msi) を SharePoint サーバーにインストールする必要があります。  
  
 ![PowerPivot モード 3 サーバーの展開として](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "として PowerPivot モード 3 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|spPowerPivot.msi を実行し、データ プロバイダー、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツール、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー、およびデータ更新スケジュールをインストールします。|  
|**(4)**|SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(5)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a> PowerPivot for SharePoint 2013 と Reporting Services のシングル サーバー配置  
 シングル サーバー配置は、テスト目的には役立ちますが、運用環境の配置にはお勧めしません。  
  
 ![SSAS および SSRS SharePoint モードの 1 サーバーの展開](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS および SSRS SharePoint モードの 1 サーバーの展開")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|PowerPivot サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション。|  
|**(4)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**(5)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SharePoint モードのサーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a> PowerPivot for SharePoint 2013 と Reporting Services の 2 つのサーバー配置  
 次のような 2 台のサーバー配置では、SQL Server データベース エンジンと SharePoint モードで実行している Analysis Services サーバーを、SharePoint とは別のサーバーで実行します。 PowerPivot for SharePoint 2013 インストーラー パッケージ **(spPowerPivot.msi)** SharePoint サーバーで実行する必要があります。  
  
 ![SSAS および SSRS SharePoint モードの 2 サーバー展開](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS および SSRS SharePoint モード 2 のサーバー配置")  
  
|||  
|-|-|  
|**(1)**|Excel Services アプリケーション。 このサービス アプリケーションは、SharePoint インストールの一部として作成されます。|  
|**(2)**|PowerPivot サービス アプリケーション。 既定の名前は、 **"既定の PowerPivot サービス アプリケーション"** です。|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション。|  
|**(4)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール メディアまたは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から、SharePoint 用 Reporting Services アドインをインストールします。|  
|**(5)**|**spPowerPivot.msi** を実行し、データ プロバイダー、PowerPivot 構成ツール、PowerPivot ギャラリーをインストールして、データ更新をスケジュールします。|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SharePoint モードのサーバー。 **[データ モデルの設定]** で、このサーバーを使用するように Excel Services アプリケーションを構成します。|  
|**(7)**|SharePoint コンテンツ データベース、構成データベース、およびサービス アプリケーション データベース。|  
  
##  <a name="bkmk_example_deployments_2010"></a> SharePoint 2010 の配置トポロジの例  
 次の図では、各階層で動作するサービスとプロバイダーを示します。 図に複数の組み込みサービスが含まれることに注意してください。これらのサービスは、一部の SQL Server BI シナリオで必要なものです。 Excel Services、Secure Store Services、および Claims to Windows Token Service は、SharePoint での PowerPivot for SharePoint または Reporting Services の配置に必要であるか、または推奨されます。 さらに、MSOLAP OLE DB プロバイダーと ADO.NET Services が、一部の PowerPivot データ アクセスのシナリオに必要です。 必要に応じて、インストールできます Analysis Services、データ層でビルドする場合[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]レポートは、SharePoint の外部でホストされている表形式モデル データベースに基づいています。  
  
 ![論理アーキテクチャ図](../../../2014/sql-server/install/media/sql11bisetup.gif "論理アーキテクチャ図")  
  
##  <a name="bkmk_sharepoint2010_1server"></a> シングル サーバー配置  
 データ層を含むすべてのサーバー コンポーネントを、1 台のコンピューターにインストールできます。 この配置構成は、ソフトウェアを評価する場合や、SharePoint モードの Reporting Services を含むカスタム アプリケーションを開発する場合に便利です。 この配置は、構成が最も簡単です。 すべてのコンポーネントを同じコンピューターにインストールするため、使用するライセンスの数も最も少なくなります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]、および [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのライセンス コピーとしてインストールされます。  
  
 すべての機能を 1 台のサーバーにインストールするには、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を順番に同じ物理サーバーにインストールします。 スタンドアロン サーバーの構成については、次を参照してください。[展開のチェックリスト: Reporting Services、Power View および PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)します。  
  
##  <a name="bkmk_sharepoint2010_2server"></a> 2 層の展開  
 2 層配置では、通常、SharePoint Server 2010 を 1 台のコンピューターに配置し、SQL Server データベース エンジンをもう 1 台のコンピューターに配置します。 2 コンピューター ファームで最も一般的な構成は、データ層を専用のサーバーに移動するものです。 2 層ファームで両方をインストールする[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]SharePoint サーバーにします。 フロントエンドのすべての Web サービスと、アプリケーション層の共有サービスが、同じ物理サーバーで動作します。 2 層配置のインストール手順はスタンドアロン配置とよく似ており、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を順番に同じ物理サーバーにインストールします。  
  
##  <a name="bkmk_sharepoint2010_3server"></a> 3 層配置  
 3 層配置では、通常、Web フロントエンド サービスを、処理アプリケーションまたはメモリ多用アプリケーションから分離します。 このトポロジでは、インストール[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]をアプリケーション サーバーだけです。 Web フロントエンドで実行される Web サービスは、サーバー構成の間のインストール後タスクとして、ファーム内のアプリケーションに配置されるソリューションを使用してインストールします。 次の図は 3 層配置を示したものです。  
  
 ![3 サーバー トポロジ](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3 サーバー トポロジ")  
  
##  <a name="bkmk_sharepoint2010_scaleserver"></a> 3 層のスケール アウト配置  
 このトポロジでは、同じ共有サービスを複数のサーバーで実行するスケールアウト配置を示します。このトポロジを使用すると、大量の要求を処理し、PowerPivot データまたは Reporting Services レポートに対する処理能力を高めることができます。 次の図には 3 つのアプリケーション サーバー クラスターがあり、それぞれが共有サービスの異なる組み合わせを実行しています。 SharePoint 環境では、サービスの探索と可用性はファームに組み込まれます。 同じ共有サービス アプリケーションを実行する複数の物理サーバー間の負荷分散は、共有サービス アーキテクチャの一部です。  
  
 マルチサーバー ファームを配置するときは、SharePoint の記事「 [3 層ファーム用の複数サーバー (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?linkID=219834)」での指示に従ってください。  
  
 ![5 サーバー トポロジ](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "5 サーバー トポロジ")  
  
## <a name="see-also"></a>参照  
 [Reporting Services の SharePoint モード インストール&#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [PowerPivot for SharePoint 2013 のインストール](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
