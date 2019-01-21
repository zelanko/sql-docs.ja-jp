---
title: SQL Server の各エディションがサポートする Reporting Services の機能
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.date: 11/01/2018
ms.openlocfilehash: 37dec44c539db86f8f0d239fffe0ca28699f2799
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645331"
---
# <a name="reporting-services-features-supported-by-the-editions-of-sql-server"></a>SQL Server の各エディションがサポートする Reporting Services の機能

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

このトピックでは、SQL Server のさまざまなエディションでサポートされる Reporting Services 機能の詳細について説明します。 180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
 最新の SQL Server リリース ノートについては、「[SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)」を参照してください。 新機能に関する最新情報については、「 [Reporting Services (SSRS) の新機能](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)」をご覧ください。

 **SQL Server 2017 をお試しください**    

> [![SQL Server 2017 をダウンロードする](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?LinkID=829477) **[Evaluation Center から SQL Server 2017 をダウンロードする](https://go.microsoft.com/fwlink/?LinkID=829477)**    
>
> ![Azure Virtual Machine のアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2017 がインストール済みの Virtual Machine をすぐにご利用いただけます](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    

Evaluation Edition および Developer Edition でサポートされている機能については、SQL Server Enterprise Edition の列を参照してください。

##  <a name="SSRS"></a> Reporting Services  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Developer|  
|------------------|---------|------------------------------------|------------------------|-------------|---------------|  
|モバイル レポートと KPI|はい||||はい|  
|サポートされているカタログ DB の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Standard 以上|Standard 以上|Web|Express|Standard 以上|  
|サポートされているデータ ソースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Web|Express|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|  
|レポート サーバー|はい|[はい]|[はい]|[はい]|はい|  
|レポート デザイナー|はい|[はい]|[はい]|[はい]|はい|  
|レポート デザイナー Web ポータル|はい|[はい]|[はい]|[はい]|はい|  
|ロール ベース セキュリティ|はい|[はい]|[はい]|[はい]|はい|  
|Excel、PowerPoint、Word、PDF、およびイメージへのエクスポート|はい|[はい]|[はい]|[はい]|はい|  
|強化されたゲージとグラフ|はい|[はい]|[はい]|[はい]|可|  
|[!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードへのレポート アイテムのピン留め|可|[はい]|[はい]|[はい]|はい|  
|カスタム認証|はい|[はい]|[はい]||はい|  
|データ フィードとしてのレポート|はい|[はい]|[はい]|[はい]|はい|  
|モデルのサポート|はい|[はい]|[はい]||はい|  
|ロールベースのセキュリティのカスタム ロールの作成|はい|[はい]|||はい|  
|モデル アイテムのセキュリティ|はい|[はい]|||はい|  
|無限クリック スルー|はい|[はい]|||はい|  
|共有コンポーネント ライブラリ|はい|[はい]|||はい|  
|電子メールおよびファイル共有のサブスクリプションとスケジュール設定|はい|[はい]|||はい|  
|レポート履歴、実行スナップショット、およびキャッシュ|はい|[はい]|||はい|  
|SharePoint 統合|はい|[はい]|||はい|  
|リモートおよび非 SQL データ ソースのサポート<sup>1</sup>|はい|[はい]|||はい|  
|データ ソース、配信およびレンダリング、RDCE の拡張性|はい|[はい]|||はい|  
|カスタム ブランド化|はい||||はい|  
|データ ドリブン レポート サブスクリプション|はい||||はい|  
|スケール アウト配置 (Web ファーム)|はい||||可|  
|警告<sup>2</sup> (SSRS 2016) |可||||可|  
| Power View<sup>2</sup> (SSRS 2016) |可||||可| 
|コメント<sup>3</sup> |可|[はい]|[はい]|[はい]|可|  

 <sup>1</sup> SQL Server Reporting Services (SSRS) でサポートされるデータ ソースの詳細については、「[Reporting Services でサポートされるデータ ソース (SSRS)](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」を参照してください。  
  
 <sup>2</sup> SharePoint モードの Reporting Services 2016 が必要です。 詳細については、「 [Reporting Services の SharePoint モードのインストール](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)」を参照してください。 Reporting Services 2017 以降、SharePoint と Reporting Services の統合は使用できなくなりました。 

<sup>3</sup> Power BI Report Server と Reporting Services 2017 以降のみ。

> [!NOTE]
> SQL Server Express with Tools および SQL Server Express では、SQL Server Reporting Services はサポートされていません。
  
## <a name="report-server-database-server-edition-requirements"></a>レポート サーバー データベースのサーバー エディション
 レポート サーバー データベースを作成するときは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のすべてのエディションでデータベースをホストできるわけではないことに注意してください。 次の表に、 [!INCLUDE[ssDE](../includes/ssde-md.md)] の特定のエディションで使用できる [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のエディションを示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services のエディション|データベースをホストするために使用するデータベース エンジン インスタンスのエディション|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Enterprise Edition または Standard Edition (ローカルまたはリモート)|  
|Standard|Enterprise Edition または Standard Edition (ローカルまたはリモート)|  
|Web|Web Edition (ローカルのみ)|  
|Express with Advanced Services|Express with Advanced Services (ローカルのみ)|  
|Evaluation|Evaluation|  
  
##  <a name="BIC"></a> Business Intelligence クライアント  
 次のソフトウェア クライアント アプリケーションを Microsoft ダウンロード センターから入手できます。これらのアプリケーションは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで使用するビジネス インテリジェンス ドキュメントの作成に役立ちます。 作成したドキュメントをサーバー環境でホストする場合は、そのドキュメントの種類をサポートする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエディションを使用してください。 これらのクライアント アプリケーションで作成したドキュメントをホストするのに必要なサーバー機能を備えた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを次の表に示します。  
  
|ツール名|Enterprise|Standard|Web|Express with Advanced Services|Developer|  
|---------------|----------------|--------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)] (.rdl、.rds)|はい|[はい]|[はい]|[はい]|はい|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] (.rsmobile)|はい||||はい|  
|モバイル デバイス (iOS、Windows 10、Android) 用 Power BI アプリ (.rsmobile)|はい||||はい|  
  
> [!NOTE]  
> 1. 上記の表は、これらのクライアント ツールを有効にするために必要な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを示しています。ただし、これらのツールは、どのエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にホストされているデータにもアクセスできます。  
> 2. [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] モバイル レポートの作成の単一ポイントです。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サーバーに接続してデータ ソースにアクセスし、レポートを作成します。 次に、それらを [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サーバーにパブリッシュすることで、組織内の他のユーザーがサーバーまたはモバイル デバイスでアクセスできるようにします。 ローカル データ ソースの場合は、 [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] スタンド アロンを使用することもできます。  
> 3. オンプレミスの  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 、クラウドの [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 、またはその両方のいずれをレポート配信ソリューションとして使用しても、モバイル デバイスでダッシュボードおよびモバイル レポートにアクセスするために必要なのは、1 つのモバイル アプリのみです。 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] アプリは Windows、iOS、または Android アプリ ストアからダウンロードできます。  

## <a name="next-steps"></a>次の手順

[SQL Server 2017 の各エディションでサポートされている機能](~/sql-server/editions-and-components-of-sql-server-2017.md)  
[SQL Server のインストール計画](../sql-server/install/planning-a-sql-server-installation.md) 

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
