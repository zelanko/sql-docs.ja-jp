---
title: ツールと Analysis Services で使用されるアプリケーション |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d3ecb5de4c70c09bc367b9008f5d62c6a23faef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162283"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>Analysis Services で使用するツールとアプリケーション
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  ツールおよびアプリケーションが Analysis Services モデルを構築する必要があり、配置済みのデータベースを管理します。  
  
## <a name="analysis-services-model-designers"></a>Analysis Services モデルのデザイナー  
 プロジェクト テンプレートで SQL Server Data Tools (SSDT)、Visual Studio シェルを使用して、モデルが作成されます。 プロジェクト テンプレートは、Analysis Services ソリューションを構成するデータ モデル オブジェクトを作成するため、モデル デザイナーを提供します。 SSDT は、毎月更新される無料の web ダウンロードです。

 **[SQL Server Data Tools (SSDT) のダウンロードします。](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)** 
  
 モデルの互換性レベルの設定により、利用できる機能と、モデルを実行する Analysis Services のリリースが決まります。  モデル デザイナーによって一部を確認するかどうか、特定の互換性レベルを指定できます。  
  
 BIM ファイルに表形式の JSON 形式と双方向のクロス フィルター、最新の機能を使用して表形式モデルを作成または互換性レベル 1200 以上アップグレードする必要があります。  
  
 低い互換性レベルが必要な場合など、Analysis Services の以前のバージョンでのモデルを配置する必要があることができますも、モデル デザイナー SSDT を使用しています。 ツールの新しいバージョンをサポートして、互換性レベル モデルの種類 (表形式または多次元) を作成します。   

## <a name="administrative-tools"></a>管理ツール  
  
 SQL Server Management Studio (SSMS) は、Analysis Services を含む、すべての SQL Server 機能の主要な管理ツールです。 SSMS では、毎月更新される無料の web ダウンロードです。 
  
**[SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)** 
  
 SSMS には、SQL Server Profiler のトレース アクティビティを監視し、SQL Server 2016 と Azure Analysis Services サーバー上の問題を診断するために軽量な代替手段を提供する拡張イベント (xEvents) が含まれています。 詳細については、「 [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) 」を参照してください。  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 xEvents のサポートに伴い、正式には非推奨となりましたが、SQL Server Profiler は引き続き、接続、MDX クエリの実行、その他のサーバー操作を監視するための使い慣れたツールとして利用できます。 SQL Server Profiler は既定でインストールされます。 Windows でアプリ上の SQL Server アプリケーションのことを見つけることができます。  
  
### <a name="powershell"></a>PowerShell  
 PowerShell コマンドを使用すると、多くの管理タスクを実行できます。 参照してください[PowerShell リファレンス](../analysis-services/powershell/analysis-services-powershell-reference.md)詳細についてはします。  
  
### <a name="community-and-third-party-tools"></a>コミュニティとサード パーティのツール  
 コミュニティ コードの例については、「 [Analysis Services Codeplex ページ](http://sqlsrvanalysissrvcs.codeplex.com/) 」を参照してください。 Analysis Services をサポートするサード パーティのツールの推奨事項を確認するには、「[フォーラム](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) 」が役立ちます。  
  
## <a name="see-also"></a>参照  
 [多次元データベースの互換性レベル](../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [表形式モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
