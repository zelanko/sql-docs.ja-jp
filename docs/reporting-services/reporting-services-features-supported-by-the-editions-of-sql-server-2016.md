---
title: "SQL Server 2016 の各エディションがサポートする Reporting Services の機能 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 39f03d2d-6e48-4b34-a9d3-07f86313b937
caps.latest.revision: 3
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 3
---
# SQL Server 2016 の各エディションがサポートする Reporting Services の機能
このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のさまざまなエディションでサポートされる機能の詳細について説明します。  
  
 180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
 最新のリリース ノートについては、「 [SQL Server 2016 Release Notes](../sql-server/sql-server-2016-release-notes.md)」を参照してください。 新機能に関する最新情報については、「[Reporting Services (SSRS) の新機能](What's%20New%20in%20Reporting%20Services%20\(SSRS\).md)」をご覧ください。
    
 **SQL Server 2016 をお試しください。**    
    
 > [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure 仮想マシンのアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2016 がインストール済みの仮想マシンをすぐにご利用いただけます](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    

Evaluation Edition および Developer Edition でサポートされている機能については、SQL Server Enterprise Edition をご覧ください。

各 SQL Server テクノロジの表に移動するには、それぞれのリンクをクリックしてください。  

-   [Reporting Services](#SSRS)  
  
-   [Business Intelligence クライアント](#BIC)  

##  <a name="SSRS"></a> Reporting Services  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|モバイル レポートと KPI|はい||||||はい|  
|サポートされているカタログ DB の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Standard 以上|Standard 以上|Web|Express|||Standard 以上|  
|サポートされているデータ ソースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Web|Express|||すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|  
|レポート サーバー|はい|可|可|可|||はい|  
|レポート デザイナー|はい|可|可|可|||はい|  
|レポート デザイナー Web ポータル|はい|可|可|可|||はい|  
|ロール ベース セキュリティ|はい|可|可|可|||はい|  
|Excel、PowerPoint、Word、PDF、およびイメージへのエクスポート|はい|可|可|可|||はい|  
|強化されたゲージとグラフ|はい|可|可|可|||はい|  
|[!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードへのレポート アイテムのピン留め|はい|可|可|可|||はい|  
|カスタム認証|はい|可|可|可|||はい|  
|データ フィードとしてのレポート|はい|可|可|可|||はい|  
|モデルのサポート|はい|可|可||||可|  
|ロールベースのセキュリティのカスタム ロールの作成|可|可|||||はい|  
|モデル アイテムのセキュリティ|はい|可|||||はい|  
|無限クリック スルー|はい|可|||||はい|  
|共有コンポーネント ライブラリ|はい|可|||||はい|  
|電子メールおよびファイル共有のサブスクリプションとスケジュール設定|はい|可|||||はい|  
|レポート履歴、実行スナップショット、およびキャッシュ|はい|可|||||はい|  
|SharePoint 統合|はい|可|||||可|  
|リモートおよび非 SQL データ ソースのサポート<sup>1</sup>|可|可|||||はい|  
|データ ソース、配信およびレンダリング、RDCE の拡張性|はい|可|||||はい|  
|カスタム ブランド化|はい||||||はい|  
|データ ドリブン レポート サブスクリプション|はい||||||可|  
|スケール アウト配置 (Web ファーム)|可||||||はい|  
|警告<sup>2</sup>|はい||||||はい|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|はい||||||可|  
  
 <sup>1</sup> SQL Server 2016 Reporting Services (SSRS) でサポートされるデータ ソースの詳細については、「[Reporting Services &#40;SSRS&#41; でサポートされるデータ ソース](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」をご覧ください。  
  
 <sup>2</sup> SharePoint モードの Reporting Services が必要です。 詳細については、「[ Reporting Services の SharePoint モードのインストール](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)」を参照してください。  
  
## レポート サーバー データベースのサーバー エディション  
 レポート サーバー データベースを作成するときは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のすべてのエディションでデータベースをホストできるわけではないことに注意してください。 次の表に、 [!INCLUDE[ssDE](../includes/ssde-md.md)] の特定のエディションで使用できる [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のエディションを示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services のエディション|データベースをホストするために使用するデータベース エンジン インスタンスのエディション|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Enterprise Edition または Standard Edition (ローカルまたはリモート)|  
|Standard|Enterprise Edition または Standard Edition (ローカルまたはリモート)|  
|Web|Web Edition (ローカルのみ)|  
|Express with Advanced Services|Express with Advanced Services (ローカルのみ)|  
|Evaluation|Evaluation|  
  
##  <a name="BIC"></a> Business Intelligence クライアント  
 次のソフトウェア クライアント アプリケーションを Microsoft ダウンロード センターから入手できます。これらのアプリケーションは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで使用するビジネス インテリジェンス ドキュメントの作成に役立ちます。 作成したドキュメントをサーバー環境でホストする場合は、そのドキュメントの種類をサポートする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエディションを使用してください。 これらのクライアント アプリケーションで作成したドキュメントをホストするのに必要なサーバー機能を備えた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを次の表に示します。  
  
|ツール名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] (.rdl、.rds)|可|可|||||可|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] (.rsmobile)|可||||||可|  
|モバイル デバイス (iOS、Windows 10、Android) 用 Power BI アプリ (.rsmobile)|可||||||可|  
  
> [!NOTE]  
> 1.  上記の表は、これらのクライアント ツールを有効にするために必要な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを示しています。ただし、これらのツールは、どのエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にホストされているデータにもアクセスできます。  
> 2.  [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] モバイル レポートの作成の単一ポイントです。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サーバーに接続してデータ ソースにアクセスし、レポートを作成します。 次に、それらを [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サーバーにパブリッシュすることで、組織内の他のユーザーがサーバーまたはモバイル デバイスでアクセスできるようにします。 ローカル データ ソースの場合は、[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] スタンド アロンを使用することもできます。  
> 3.  オンプレミスの [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]、クラウドの [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]、またはその両方のいずれをレポート配信ソリューションとして使用しても、モバイル デバイスでダッシュボードおよびモバイル レポートにアクセスするために必要なのは、1 つのモバイル アプリのみです。 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] アプリは Windows、iOS、または Android アプリ ストアからダウンロードできます。  

## 参照  
 [SQL Server 2016 の各エディションでサポートされる機能](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
 [SQL Server 2016 の製品仕様](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md) 