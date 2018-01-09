---
title: "SQL Server の以前のバージョンにデータ マイニング ソリューションの配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f082d488439f1331c009352bc7d691b7703f0e32
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a>SQL Server の以前のバージョンへのデータ マイニング ソリューションの配置
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]このセクションには、データ マイニング モデルまたはデータ マイニング構造のインスタンスで作成された展開しようとしたときに発生する可能性がある既知の互換性の問題がについて説明します[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]SQL Server 2005 の Analysis Services を使用するデータベースに展開するときに、またはインスタンスに SQL Server 2005 で作成されたモデル[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
 SQL Server 2000 Analysis Services のインスタンスへの配置はサポートされていません。  
  
 [タイム シリーズ モデルの配置](#bkmk_TimeSeries)  
  
 [提示されたパーティションを使用するモデルの配置](#bkmk_Holdout)  
  
 [フィルターを使用するモデルの配置](#bkmk_Filter)  
  
 [データベース バックアップからの復元](#bkmk_Backup)  
  
 [データベースの同期の使用](#bkmk_Synch)  
  
##  <a name="bkmk_TimeSeries"></a> タイム シリーズ モデルの配置  
 Microsoft タイム シリーズのアルゴリズムは、SQL Server 2008 で補完的なアルゴリズムの ARIMA が追加され、機能が拡張されています。 タイム シリーズ アルゴリズムの変更に関する詳細については、「 [Microsoft タイム シリーズ アルゴリズム](../../analysis-services/data-mining/microsoft-time-series-algorithm.md)」を参照してください。  
  
 したがって、新しい ARIMA アルゴリズムを使用するタイム シリーズ マイニング モデルを SQL Server 2005 Analysis Services のインスタンスに配置すると、動作が異なる場合があります。  
  
 ARTXP モデルと ARIMA モデルを組み合わせた予測を制御するパラメーター PREDICTION_SMOOTHING を明示的に設定している場合に、このモデルを SQL Server 2005 のインスタンスに配置すると、パラメーターが無効であるというエラーが Analysis Services で発生します。 このエラーを防ぐには、PREDICTION_SMOOTHING パラメーターを削除し、モデルを純粋な ARTXP モデルに変換する必要があります。  
  
 反対に、SQL Server 2005 Analysis Services を使用して作成されたタイム シリーズ モデルを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスに配置する場合、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でマイニング モデルを開くと、最初に定義ファイルが新しい形式に変換され、既定では、2 つの新しいパラメーターがすべてのタイム シリーズ モデルに追加されます。 パラメーター FORECAST_METHOD が既定値 MIXED で追加され、パラメーター PREDICTION_SMOOTHING が既定値 0.5 で追加されます。 ただし、モデルを再処理するまで、モデルは引き続き ARTXP のみを予測に使用します。 モデルの再処理が終わるとすぐ、予測に ARIMA と ARTXP の両方が使用されます。  
  
 したがって、モデルが変更されないようにするには、モデルを参照するだけにして、決して処理を行わないようにします。 あるいは、FORECAST_METHOD パラメーターまたは PREDICTION_SMOOTHING パラメーターを明示的に設定することもできます。  
  
 混合モデルを設定する方法については、「 [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)」を参照してください。  
  
 モデルのデータ ソースに使用されるプロバイダーが SQL Client Data Provider 10 の場合、データ ソース定義も変更して、SQL Server Native Client の前のバージョンを指定する必要があります。 そうしないと、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で、プロバイダーが登録されていないことを示すエラーが発生します。  
  
##  <a name="bkmk_Holdout"></a> 提示されたパーティションを使用するモデルの配置  
 データ マイニング モデルをテストするために使用される、提示されたパーティションを含むマイニング構造を作成する場合は、マイニング構造を SQL Server 2005 のインスタンスに配置できますが、パーティション情報は失われます。  
  
 SQL Server 2005 Analysis Services でマイニング構造を開くと、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でエラーが発生し、提示されたパーティションを削除するためにそのマイニング構造が再生成されます。  
  
 プロパティ ウィンドウに、提示されたパーティションのサイズが使用可能なで不要になった構造が再構築された後にただし、値\</ddl100_100:holdoutmaxpercent > 30\</ddl100_100:HoldoutMaxPercent >)、ASSL スクリプト ファイルである可能性があります。  
  
##  <a name="bkmk_Filter"></a> フィルターを使用するモデルの配置  
 マイニング モデルにフィルターを適用する場合、モデルは、SQL Server 2005 のインスタンスに配置することができますが、フィルターは適用されません。  
  
 マイニング モデルを開くと、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でエラーが発生し、フィルターを削除するためにモデルが再生成されます。  
  
##  <a name="bkmk_Backup"></a> データベース バックアップからの復元  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で作成されたデータベース バックアップを SQL Server 2005 のインスタンスに復元することはできません。 復元を実行すると、SQL Server Management Studio でエラーが発生します。  
  
 SQL Server 2005 Analysis Services データベースのバックアップを作成して [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンス上に復元する場合、前のセクションで示したようにすべてのタイム シリーズ モデルが変更されます。  
  
##  <a name="bkmk_Synch"></a> データベースの同期の使用  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] から SQL Server 2005 へのデータベースの同期はサポートされていません。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] データベースの同期を試みると、サーバーはエラーを返し、データベースの同期は失敗します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services の旧バージョンとの互換性](../../analysis-services/analysis-services-backward-compatibility.md)  
  
  
