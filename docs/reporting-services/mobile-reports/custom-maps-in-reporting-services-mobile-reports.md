---
title: Reporting Services モバイル レポートのカスタム マップ | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: mobile-reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea22c2ea60a681accc747e9426fbecb4aad7b515
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="custom-maps-in-reporting-services-mobile-reports"></a>Reporting Services モバイル レポートのカスタム マップ
SQL Server Mobile Report Publisher の地理的マップは、*ESRI シェープファイル*と呼ばれる形式で定義されます。  
  
この形式は、もともとは一企業によって設計されたものですが、広く普及した準オープン形式として GIS アプリケーションの大部分で使用されるようになりました。 この形式に従い、Mobile Report Publisher でマップを定義するときは、次の 2 つのファイルを提供する必要があります。  
  
- 図形ジオメトリ用の .SHP ファイル  
- メタデータ用の .DBF ファイル  
  
ベース ファイル名は一致する必要があります (例: *canada.shp* と *canada.dbf*)。 メタデータには、マップにデータを設定するときに使用する対応する図形の名前 (キー) を値として含む *NAME* フィールドを含める必要があります。  
  
> **注**: SHP と DBF の2 つのマップ ファイルのサイズの合計が 512 KB 以下である必要があります。 マップ ファイルが大きすぎる場合は、[http://mapshaper.org/](http://mapshaper.org/) などのツールを使用してサイズを小さくします。  
  
[モバイル レポートにカスタムのマップを追加](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md)する方法を確認してください。  
  
## <a name="technical-information"></a>技術情報  
  
- 公式の仕様: [http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Wikipedia のシェープファイルの記事: [http://en.wikipedia.org/wiki/Shapefile](http://en.wikipedia.org/wiki/Shapefile)  
  
## <a name="creating--editing-map-geometry"></a>マップ ジオメトリの作成および編集  
  
シェープファイルの作成と編集プロセスは複雑であり、このドキュメントの範囲外です。 役に立つリソースとアプリケーションを次に示します。  
  
- ArcGIS: [http://www.arcgis.com/](http://www.arcgis.com/)  
- Adobe Illustrator 用 MAPublisher プラグイン: [http://www.avenza.com/mapublisher](http://www.avenza.com/mapublisher)  
- QuantumGIS (無料): [http://www.qgis.org/](http://www.qgis.org/)  
- Manco ShapeFile Editor: [http://www.mancosoftware.com/ShapeFileEditor](http://www.mancosoftware.com/ShapeFileEditor)  
  
## <a name="existing-shapefiles"></a>既存のシェープファイル  
  
次のような Web サイトから多くの既存のシェープファイルをダウンロードできます。  
  
- Diva-GIS: [http://www.diva-gis.org/Data](http://www.diva-gis.org/Data)  
- OpenStreetMap: [http://openstreetmapdata.com/data](http://openstreetmapdata.com/data)  
  
### <a name="see-also"></a>参照  
- [Maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
