---
title: Microsoft ビジネス インテリジェンス (BI) ツールでの分析とレポート
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 7c76ec1a74032b5f35bc42ab4a901d95574e0900
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "75688213"
---
# <a name="analysis-and-reporting-with-microsoft-business-intelligence-bi-tools"></a>Microsoft ビジネス インテリジェンス (BI) ツールでの分析とレポート

  次の表は、データ分析とレポートに対応するワークロードを、これらのワークロードに最も適した Microsoft BI ツールに関連付けます。  
  
 その目的は、ニーズを最適な方法で満たすツールを選択できるようにすることです。 製品に関する詳細については、表内の製品リンクをクリックしてください。  
  
 ツールの概要を確認し、どのツールが適しているかを判断するには、「[Microsoft Business Intelligence (BI) ツールの概要](https://www.digitalvidya.com/blog/introduction-to-microsoft-power-bi/)」を参照してください。  
  
|ワークロード|ユーザー|||BI ツール|||  
|---------------|----------|-|-|--------------|-|-|  
|||**Excel**|**SharePoint**|**について**|**Power BI**|**SQL Server**|  
|**セルフサービス BI**|アナリスト/エンド ユーザー||||||  
|パブリック データと企業データの検出とアクセスの簡素化||[Power Query](https://go.microsoft.com/fwlink/p/?LinkId=391845)||[Azure Data Catalog](https://azure.microsoft.com/services/data-catalog/)<br /><br />||  
|強力なデータ モデルの作成||[Power Pivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed?ui=en-US&rs=en-US&ad=US)|||[Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-get-the-desktop/)||  
|セルフサービスの予測分析の実行||||||[Excel 用データ マイニング アドイン](../analysis-services/data-mining-client-for-excel-sql-server-data-mining-add-ins.md)|  
|データの視覚化と探索||[Power View](https://go.microsoft.com/fwlink/p/?LinkId=391847)<br /><br /> [3D マップ](https://support.office.com/article/visualize-your-data-in-3d-maps-ce6b1d5c-4602-4dae-b487-91ec0268e75d)|||||  
|自然言語クエリを使用した問い合わせの実施|||||[Q & A](https://docs.microsoft.com/power-bi/consumer/end-user-q-and-a)||  
|モバイル デバイスを使用したレポートのアクセス||||[HTML 5 (< 10 MB ファイルの表示をサポート)](https://go.microsoft.com/fwlink/p/?LinkId=391853)|[HTML 5 (< 250 MB ファイルの表示をサポート)](https://go.microsoft.com/fwlink/p/?LinkId=391854)<br /><br /> [iOS デバイス上の Power BI モバイル アプリ](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-iphone-app-get-started)<br /><br /> [Android デバイス上の Power BI モバイル アプリ](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-android-app-get-started) <br /><br />[Windows 10 用 Power BI モバイル アプリ](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-windows-10-phone-app-get-started)||  
|コラボレーションと共有|||[SharePoint サイト](https://go.microsoft.com/fwlink/p/?LinkId=391849)|[SharePoint チーム サイト](https://go.microsoft.com/fwlink/p/?LinkId=391850)|[Power BI サイト](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports)||  
|**企業 BI**|IT プロフェッショナル||||||  
|多次元/表形式ビジネス モデルの作成||||||[Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services-overview)|  
|アドホック データ視覚エフェクトの作成|||[SharePoint 用の Power View](https://go.microsoft.com/fwlink/p/?LinkId=391858)||||  
|ダッシュボードの作成|||[SharePoint ダッシュボード](https://go.microsoft.com/fwlink/p/?LinkId=391859)<br /><br /> [PerformancePoint Services](https://technet.microsoft.com/library/ee424392.aspx)||||  
|運用レポートの作成||||||<sup>1</sup> [Reporting Services](create-deploy-and-manage-mobile-and-paginated-reports.md)|  
|カスタム レポートと埋め込みレポートの作成||||||<sup>1</sup> [Reporting Services](create-deploy-and-manage-mobile-and-paginated-reports.md)|  
|**高度な分析**|データ サイエンティスト||||||  
|セルフサービスの予測分析の実行||||||[Excel 用データ マイニング アドイン](https://msdn.microsoft.com/library/dn282385\(v=sql.120\).aspx)|  
|データ マイニング アルゴリズムの使用||||||[Analysis Services 内でのデータ マイニング](https://technet.microsoft.com/library/bb510516\(v=sql.120\).aspx)|  
  
 <sup>1</sup> Reporting Services には、操作レポートやカスタムレポート (サブスクリプションやデータ警告など) の配信をサポートするさまざまな機能があります。