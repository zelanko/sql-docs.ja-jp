---
title: SQL Server 2016 の各エディションがサポートする Reporting Services の機能 | Microsoft Docs
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 39f03d2d-6e48-4b34-a9d3-07f86313b937
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3a57f466df8b404455234dde9635448b1a9ebb86
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50031902"
---
# <a name="reporting-services-features-supported-by-the-editions-of-sql-server-2016"></a>SQL Server 2016 の各エディションがサポートする Reporting Services の機能

このトピックでは、SQL Server 2016 のさまざまなエディションでサポートされる機能の詳細について説明します。  
  
 180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
 最新のリリース ノートについては、「 [SQL Server 2016 Release Notes](../sql-server/sql-server-2016-release-notes.md)」を参照してください。 新機能に関する最新情報については、「 [Reporting Services (SSRS) の新機能](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)」をご覧ください。
    
 **SQL Server 2016 をお試しください。**    
    
 > [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure 仮想マシンのアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2016 がインストール済みの仮想マシンをすぐにご利用いただけます](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    

Evaluation Edition および Developer Edition でサポートされている機能については、SQL Server Enterprise Edition をご覧ください。

各 SQL Server テクノロジの表に移動するには、それぞれのリンクをクリックしてください。  

-   [Reporting Services](#SSRS)  
  
-   [Business Intelligence クライアント](#BIC)  

##  <a name="SSRS"></a> Reporting Services  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|モバイル レポートと KPI|はい||||||はい|  
|サポートされているカタログ DB の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Standard 以上|Standard 以上|Web|Express|||Standard 以上|  
|サポートされているデータ ソースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Web|Express|||すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|  
|レポート サーバー|はい|[はい]|[はい]|[はい]|||はい|  
|レポート デザイナー|はい|[はい]|[はい]|[はい]|||はい|  
|レポート デザイナー Web ポータル|はい|[はい]|[はい]|[はい]|||はい|  
|ロール ベース セキュリティ|はい|[はい]|[はい]|[はい]|||はい|  
|Excel、PowerPoint、Word、PDF、およびイメージへのエクスポート|はい|[はい]|[はい]|[はい]|||はい|  
|強化されたゲージとグラフ|はい|[はい]|[はい]|[はい]|||はい|  
|[!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]ダッシュボードへのレポート アイテムのピン留め|はい|[はい]|[はい]|[はい]|||はい|  
|カスタム認証|はい|[はい]|[はい]|[はい]|||はい|  
|データ フィードとしてのレポート|はい|[はい]|[はい]|[はい]|||はい|  
|モデルのサポート|はい|[はい]|[はい]||||はい|  
|ロールベースのセキュリティのカスタム ロールの作成|はい|[はい]|||||はい|  
|モデル アイテムのセキュリティ|はい|[はい]|||||はい|  
|無限クリック スルー|はい|[はい]|||||はい|  
|共有コンポーネント ライブラリ|はい|[はい]|||||はい|  
|電子メールおよびファイル共有のサブスクリプションとスケジュール設定|はい|[はい]|||||はい|  
|レポート履歴、実行スナップショット、およびキャッシュ|はい|[はい]|||||はい|  
|SharePoint 統合|はい|[はい]|||||はい|  
|リモートおよび非 SQL データ ソースのサポート<sup>1</sup>|はい|[はい]|||||はい|  
|データ ソース、配信およびレンダリング、RDCE の拡張性|はい|[はい]|||||はい|  
|カスタム ブランド化|はい||||||はい|  
|データ ドリブン レポート サブスクリプション|はい||||||はい|  
|スケール アウト配置 (Web ファーム)|はい||||||はい|  
|警告<sup>2</sup>|はい||||||はい|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|はい||||||はい|  
  
 <sup>1</sup> SQL Server 2016 Reporting Services (SSRS) でサポートされるデータ ソースの詳細については、「[Reporting Services &#40;SSRS&#41; でサポートされるデータ ソース](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」をご覧ください。  
  
 <sup>2</sup> SharePoint モードの Reporting Services が必要です。 詳細については、「 [Reporting Services の SharePoint モードのインストール](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)」を参照してください。  
  
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
  
|ツール名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)] (.rdl、.rds)|はい|[はい]|||||はい|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] (.rsmobile)|はい||||||はい|  
|モバイル デバイス (iOS、Windows 10、Android) 用 Power BI アプリ (.rsmobile)|はい||||||はい|  
  
> [!NOTE]  
> 1.  上記の表は、これらのクライアント ツールを有効にするために必要な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを示しています。ただし、これらのツールは、どのエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にホストされているデータにもアクセスできます。  
> 2.  [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] モバイル レポートの作成の単一ポイントです。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サーバーに接続してデータ ソースにアクセスし、レポートを作成します。 次に、それらを [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サーバーにパブリッシュすることで、組織内の他のユーザーがサーバーまたはモバイル デバイスでアクセスできるようにします。 ローカル データ ソースの場合は、 [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] スタンド アロンを使用することもできます。  
> 3.  オンプレミスの  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 、クラウドの [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 、またはその両方のいずれをレポート配信ソリューションとして使用しても、モバイル デバイスでダッシュボードおよびモバイル レポートにアクセスするために必要なのは、1 つのモバイル アプリのみです。 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] アプリは Windows、iOS、または Android アプリ ストアからダウンロードできます。  

## <a name="next-steps"></a>次の手順

[SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)  
[SQL Server 2016 の製品仕様](https://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)  
[SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md) 

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
