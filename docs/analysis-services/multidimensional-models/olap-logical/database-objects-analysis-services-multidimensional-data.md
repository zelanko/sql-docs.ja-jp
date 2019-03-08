---
title: データベース オブジェクト (Analysis Services - 多次元データ) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c7b9bab0da5b00e77696217974dee5eb5d1d522
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2019
ms.locfileid: "57578742"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>データベース オブジェクト (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスには、データベース オブジェクトとオンライン分析処理 (OLAP) およびデータ マイニングで使用するためのアセンブリが含まれています。  
  
-   データベースには、OLAP と、データ ソース、データ ソース ビュー、キューブ、メジャー、メジャー グループ、ディメンション、属性、階層、マイニング構造、マイニング モデル、ロールなどのデータ マイニング オブジェクトが含まれています。  
  
-   アセンブリには、ユーザー定義関数が含まれており、多次元式 (MDX) 言語およびデータ マイニング拡張機能 (DMX) 言語が提供されている固有の関数の機能を拡張します。  
  
 <xref:Microsoft.AnalysisServices.Database> オブジェクトは、ビジネス インテリジェンス プロジェクトに必要なすべてのデータ オブジェクト (OLAP キューブ、ディメンション、データ マイニング構造など) とそのサポート オブジェクト (<xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.Account>、<xref:Microsoft.AnalysisServices.Role> など) のコンテナーです。  
  
 <xref:Microsoft.AnalysisServices.Database> オブジェクトは、次のオブジェクトや属性へのアクセスを提供します。  
  
-   アクセスできるすべてのキューブ (コレクション)  
  
-   アクセスできるすべてのディメンション (コレクション)  
  
-   アクセスできるすべてのマイニング構造 (コレクション)  
  
-   すべてのデータ ソースとデータ ソース ビュー (2 つのコレクション)  
  
-   すべてのロールとデータベース権限 (2 つのコレクション)  
  
-   データベースの照合順序の値  
  
-   データベースの推定サイズ  
  
-   データベースの言語の値  
  
-   データベースの表示の設定  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で OLAP とデータ マイニング機能の両方によって共有されるオブジェクトについて説明します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[多次元モデルのデータ ソース](../../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータ ソースについて説明します。|  
|[多次元モデルのデータ ソース ビュー](../../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で、1 つ以上のデータ ソースに基づく論理データ モデルについて説明します。|  
|[多次元モデルのキューブ](../../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)|キューブと、メジャー、メジャー グループ、ディメンションの使用法とリレーションシップ、計算、主要業績評価指標 (KPI)、アクション、翻訳、パーティション、パースペクティブなどのキューブ オブジェクトについて説明します。|  
|[ディメンション &#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|ディメンションと、属性、属性リレーションシップ、階層、レベル、メンバーなどのディメンション オブジェクトについて説明します。|  
|[マイニング構造 (Analysis Services - データ マイニング)](../../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)|マイニング構造と、マイニング モデルなどのマイニング オブジェクトについて説明します。|  
|[セキュリティ ロール (Analysis Services - 多次元データ)](../../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)|ロールについて説明します。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でオブジェクトへのアクセスを制御するために使用するセキュリティ メカニズムです。|  
|[多次元モデルのアセンブリの管理](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)|アセンブリについて説明します。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で、MDX 言語と DMX 言語を拡張するために使用するユーザー定義関数のコレクションです。|  
  
## <a name="see-also"></a>参照  
 [サポートされるデータ ソース &#40;SSAS - 多次元&#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)   
 [多次元モデル ソリューション](../../../analysis-services/multidimensional-models/multidimensional-model-solutions-ssas.md)   
 [データ マイニング ソリューション](../../../analysis-services/data-mining/data-mining-solutions.md)  
  
  
