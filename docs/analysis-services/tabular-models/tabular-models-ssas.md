---
title: "表形式モデル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/29/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: edeea89c1d767364f4f087d0f4b2e6d566895c52
ms.sourcegitcommit: c77a8ac1ab372927c09bf241d486e96881b61ac9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="tabular-models"></a>テーブル モデル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]表形式モデルは、Analysis Services データベースをメモリ内または DirectQuery モードでは、バックエンド リレーショナル データ ソースからデータを直接へのアクセスを実行します。  
  
 既定のモードはインメモリ モードです。 最新の圧縮アルゴリズムおよびマルチ スレッド クエリ プロセッサを使用して、分析エンジン アクセスを提供高速表形式モデル オブジェクトとデータを Power BI と Excel などのクライアント アプリケーションを報告することによってです。  
  
 DirectQuery は、モデルが大きすぎてメモリに収まらない場合やデータの揮発性によって妥当な処理方法が阻害される場合に使用できる、代替クエリ モードです。 このリリースの DirectQuery では、追加のデータ ソースのサポート、DirectQuery モデルの計算テーブルおよび列の処理機能、バックエンド データベースに達する DAX 式を介した行レベルのセキュリティ、および以前のバージョンよりも高速なスループットを実現するクエリ最適化により、インメモリ モデルとの同等性が高まっています。
  
 表形式モデルは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、モデル、テーブル、リレーションシップ、および DAX 式を作成するためのデザイン画面を提供する表形式モデル プロジェクト テンプレートを使用して作成します。 複数のソースからデータをインポートした後、リレーションシップ、計算テーブルおよび列、メジャー、KPI、階層、および翻訳を追加して、モデルを拡充することができます。  
  
 Azure Analysis Services に配置できるモデルまたは表形式サーバー モード用 SQL Server Analysis Services のインスタンスに構成します。 配置済みテーブル モデルは、多次元モデルと同じように SQL Server Management Studio で管理できます。 また、最適処理のためにパーティション分割したり、ロール ベースのセキュリティを使用して行レベルに保護したりすることもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テーブル モデル ソリューション](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md)-このセクションのトピックでは、作成および表形式モデル ソリューションの配置について説明します。
  
 [表形式モデル データベース](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)-このセクションのトピックでは、配置済みテーブル モデル ソリューションの管理について説明します。
  
 [表形式モデルのデータ アクセス](../../analysis-services/tabular-models/tabular-model-data-access.md)-このセクションのトピックでは、テーブル モデル ソリューションの配置への接続について説明します。
  
## <a name="see-also"></a>参照  
 [Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)   
 [テーブル ソリューションと多次元ソリューションの比較](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [ツールと Analysis Services で使用されるアプリケーション](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
