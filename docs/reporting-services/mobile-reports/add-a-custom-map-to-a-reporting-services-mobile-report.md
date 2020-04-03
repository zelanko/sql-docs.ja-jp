---
title: Reporting Services モバイル レポートへのカスタム マップの追加 | Microsoft Docs
description: Reporting Services モバイル レポートにカスタム マップを追加できます。 この記事では、カスタム マップにデータを読み込んで接続する方法について説明します。
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a1c15d5b5155d68f94a1672ca55654485c6b1835
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79448348"
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Reporting Services モバイル レポートへのカスタム マップの追加
カスタム マップには、2 つのファイルが必要です。  
* 図形ジオメトリ用の .SHP ファイル  
* メタデータ用の .DBF ファイル  
  
詳しくは、「 [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)」 (Reporting Services モバイル レポートのカスタム マップ) をご覧ください。  
  
この 2 つのファイルは同じフォルダーに格納します。 また、この 2 つのファイル名は一致する必要があります (例: canada.shp と canada.dbf)。 メタデータ (DBF ファイル) の最初の列は、マップにデータを設定するときに使用する、対応する図形の名前 (キー) のキー値と照合するために使用されます。
  
## <a name="load-a-custom-map"></a>カスタム マップを読み込む  
  
1. **[レイアウト]** タブで、マップの種類を選択します: **[グラデーション ヒート マップ]** 、 **[範囲停止のヒート マップ]** 、または **[バブル マップ]** 。これをデザイン画面にドラッグして、必要なサイズにします。  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. **[レイアウト]** ビュー、 **[Visual Properties]** (ビジュアル プロパティ) パネル、 **[マップ]** の順に移動し、 **[Custom Map From File]** (ファイルのカスタム マップ) を選択します。   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. **[開く]** ダイアログ ボックスで、SHP ファイルと DBF ファイルの場所に移動し、両方とも選択します。   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>データをカスタム マップに接続する  
最初にカスタム マップをレポートに追加すると、 [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] によって、シミュレート済みの地理データが入力されます。  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
カスタム マップへの実際のデータの表示は、組み込みマップへのデータ表示と同じです。 データを表示するには、「 [Maps in SQL Server mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) 」 (SQL Server モバイル レポートのマップ)の手順に従います。  
  
### <a name="see-also"></a>関連項目  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Maps in SQL Server mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  
