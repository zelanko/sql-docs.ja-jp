---
title: Microsoft のさまざまな環境でのビジネス インテリジェンス機能の比較 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1fb759ee-8172-4c4c-9f7d-49af2c731006
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 97ac603e2e043810d468d9c9ada00c11a4f78d15
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188089"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>さまざまな Microsoft 環境での Business Intelligence 機能の比較
  Microsoft[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]数など、さまざまな環境にデプロイできるビジネス インテリジェンス[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SharePoint Server、SharePoint Online、および Power BI for Office 365 とします。 このトピックでは、各環境でサポートされるコンポーネントと機能を比較します。  
  
 SharePoint Server と SharePoint Online の比較に関する詳細については、「 [Compare SharePoint plans and options](http://products.office.com/SharePoint/compare-sharepoint-plans)」を参照してください。  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>BI レポートとダッシュボードの作成と管理  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online Plan 2|Office 365 用 BI 機能|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|BI サイト|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ギャラリー|いいえ|Power BI サイト|  
|データ スチュワードシップおよびクエリの共有と管理|いいえ|いいえ|[はい]  **<sup>1</sup>**|  
|Master Data Services (MDS) と Data Quality Services (DQS) との統合|はい|いいえ|いいえ|  
|定期データ更新|可 (ただし Power Query データを含むブックはサポートしない)|いいえ|はい|  
|自然言語クエリ (Q&A)|いいえ|いいえ|[はい]  **<sup>2</sup>**|  
|予測される予測|いいえ|いいえ|[はい]  **<sup>3</sup>**|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 統合|はい|いいえ|いいえ|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 統合 (多次元および表形式)|はい|いいえ|いいえ|  
|対話型の Power View ダッシュボードを PowerPoint プレゼンテーションにエクスポートする|はい|いいえ|いいえ|  
|ブラウザー内のダッシュ ボードの作成|はい|いいえ|いいえ|  
|利用状況の監視|はい|いいえ|はい|  
|ベースのセキュリティの活用行[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]キューブ|はい|いいえ|いいえ|  
  
 **<sup>1</sup>**[データ管理におけるデータ スチュワードの役割について](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US)と[ビデオ: Power BI の情報管理とデータ スチュワードシップ](https://www.youtube.com/watch?v=8dHOj68ts7c)します。    
  
 **<sup>2</sup>**[power BI Q & a: Power BI ブックの最適化 (クラウドのモデリング)](https://support.office.com/article/Power-BI-Q-A-Optimize-a-Power-BI-workbook-cloud-modeling--96dc5941-d0f1-44e2-9d9d-c038a3a55849?ui=en-US&rs=en-US&ad=US)します。    
  
 **<sup>3</sup>**[Office 365 の Power View での機能の新しい予測 Introducing](http://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx)します。    
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>BI データ、レポート、およびダッシュボードの表示と参照  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online Plan 2|Office 365 用 BI 機能|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|ブラウザーで Microsoft Excel ブックを表示する|可 (ブックのサイズが 2 GB より小さい場合)|可 (ブックのサイズが 10 MB より小さい場合)|可 (ブックのサイズが 250 MB より小さい場合)|  
|HTML5 でのブラウザー内のデータ探索|いいえ|いいえ|はい|  
|レポートとダッシュ ボードにリモートでアクセスするモバイル BI アプリ|いいえ|いいえ|[はい]  **<sup>1</sup>**|  
|含む Excel ブック[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]データ ソースとして **<sup>2</sup>**|はい|いいえ|いいえ|  
|機能をさまざまなブラウザーやバージョンで使用するための機能|Power View の視覚化の [はい]、  **<sup>3</sup>**|はい、ブックのファイル サイズを 10 MB より小さい **<sup>3</sup>**|[はい]  **<sup>3</sup>**|  
  
 **<sup>1</sup>**[Microsoft Power BI](http://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba)します。    
  
 **<sup>2</sup>**[データ ソースとしての PowerPivot ブック  ](http://blogs.technet.com/b/excel_services__powerpivot_for_sharepoint_support_blog/archive/2013/02/15/powerpivot-workbook-as-a-data-source.aspx)  
  
 **<sup>3</sup>**[モバイル デバイスのサポートでのビジネス インテリジェンス (BI) ツール](http://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx)と[Reporting Services と Power View のブラウザー サポート (Reporting Services 2014) の計画](http://msdn.microsoft.com/library/ms156511.aspx)します。    
  
## <a name="more-information"></a>詳細情報  
  
-   「[Business intelligence capabilities in Excel, SharePoint Online, and Power BI for Office 365 (Excel、SharePoint Online、および Power BI for Office 365 でのビジネス インテリジェンス機能)](https://technet.microsoft.com/en-us/library/dn198235.aspx)」。  
  
-   シノニムを使用するための要件については、「 [Power Pivot Excel データ モデルにシノニムを追加する](https://support.office.com/Article/Add-synonyms-to-a-Power-Pivot-Excel-data-model-345f4f5b-5ec2-4998-bc46-a26bdc0810b6?ui=en-US&rs=en-US&ad=US)」を参照してください。  
  
-   [Office Online の「エンタープライズ ソーシャル ネットワーク:Yammer またはニュースフィード](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US)」。  
  
-   「[Power BI for Office 365](http://www.microsoft.com/powerbi/default.aspx)」。  
  
-   「[Power BI の料金](http://www.microsoft.com/powerBI/pricing.aspx)」。  
  
-   「[BI センター サイトと Power BI for Office 365 サイトを比較する](http://technet.microsoft.com/library/dn394343\(v=office.15\).aspx)」。  
  
-   [Microsoft BI のレポートや分析ツールの概要](http://go.microsoft.com/fwlink/p/?LinkId=617093)  
  
## <a name="community-content"></a>コミュニティ コンテンツ  
 「[内部設置型 vs クラウドでの Microsoft セルフ サービス BI](http://businessintelligist.com/2014/02/07/microsoft-self-service-bi-on-premise-vs-could/)」。  
  
  
