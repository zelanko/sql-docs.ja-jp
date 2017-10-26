---
title: "ツールと Analysis Services で使用されるアプリケーション |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 5b9e63d4c7cdc57814b04b2e96e52bda17a25f5a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="tools-and-applications-used-in-analysis-services"></a>Analysis Services で使用するツールとアプリケーション
  ツールとアプリケーションが Analysis Services モデルの構築にする必要がありますを検索し、配置済みデータベースを管理します。  
  
## <a name="analysis-services-model-designers"></a>Analysis Services モデルのデザイナー  
 モデルは、プロジェクト テンプレートで SQL Server Data Tools (SSDT)、Visual Studio シェルを使用して作成されます。 プロジェクト テンプレートは、Analysis Services ソリューションを構成するデータ モデル オブジェクトを作成するため、モデル デザイナーを提供します。 SSDT とは、毎月更新され、無料の web ダウンロードです。

 **[SQL Server Data Tools (SSDT) のダウンロードします。](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)** 
  
 モデルの互換性レベルの設定により、利用できる機能と、モデルを実行する Analysis Services のリリースが決まります。  モデル デザイナーによって一部でを決定するかどうかは、特定の互換性レベルを指定できます。  
  
 BIM ファイル表形式の JSON 形式で、双方向のクロス フィルターを最新の機能を使用して表形式モデルを作成または互換性レベル 1200 以上にアップグレードする必要があります。  
  
 低い互換性レベルを必要とする場合など、Analysis Services の以前のバージョンでモデルを配置することができるときでも使用、モデル デザイナー SSDT でします。 ツールの新しいバージョンでは、あらゆる互換性レベル モデルの種類 (表形式または多次元) の作成をサポートします。   

## <a name="administrative-tools"></a>管理ツール  
  
 SQL Server Management Studio (SSMS) は、Analysis Services を含む、すべての SQL Server 機能の主要な管理ツールです。 SSMS は毎月更新され、無料の web ダウンロードです。 
  
**[SQL Server Management Studio をダウンロードします。](../ssms/download-sql-server-management-studio-ssms.md)** 
  
 SSMS には、SQL Server Profiler トレースの監視活動と SQL Server 2016 と Azure Analysis Services サーバーで問題を診断するために軽量な代替手段を提供する拡張イベント (Xevent) が含まれています。 詳細については、「 [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) 」を参照してください。  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 xEvents のサポートに伴い、正式には非推奨となりましたが、SQL Server Profiler は引き続き、接続、MDX クエリの実行、その他のサーバー操作を監視するための使い慣れたツールとして利用できます。 SQL Server Profiler は既定でインストールされます。 アプリでの SQL Server アプリケーションで Windows で検索することができます。  
  
### <a name="powershell"></a>PowerShell  
 PowerShell コマンドを使用すると、多くの管理タスクを実行できます。 参照してください[PowerShell リファレンス](../analysis-services/powershell/analysis-services-powershell-reference.md)詳細についてはします。  
  
### <a name="community-and-third-party-tools"></a>コミュニティとサード パーティのツール  
 コミュニティ コードの例については、「 [Analysis Services Codeplex ページ](http://sqlsrvanalysissrvcs.codeplex.com/) 」を参照してください。 Analysis Services をサポートするサード パーティのツールの推奨事項を確認するには、「[フォーラム](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) 」が役立ちます。  
  
## <a name="see-also"></a>参照  
 [多次元データベースの互換性レベル](../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [表形式モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

