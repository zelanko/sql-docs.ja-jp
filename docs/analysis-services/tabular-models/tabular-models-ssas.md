---
title: "テーブル モデル (SSAS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 1d770b114a708301f884de76d7c6a4cc39227195
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="tabular-modeling-ssas"></a>テーブル モデリング (SSAS)
  表形式モデルは、インメモリ モードまたは DirectQuery モードで実行される Analysis Services データベースで、バックエンド リレーショナル データ ソースから直接取得したデータにアクセスします。  
  
 既定のモードはインメモリ モードです。 インメモリ分析エンジンは、最新の圧縮アルゴリズムおよびマルチスレッド クエリ プロセッサを使用し、Microsoft Excel、Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]などのレポート クライアント アプリケーションにより、表形式のモデル オブジェクトおよびデータへの高速アクセスを実現します。  
  
 DirectQuery は、モデルが大きすぎてメモリに収まらない場合やデータの揮発性によって妥当な処理方法が阻害される場合に使用できる、代替クエリ モードです。 このリリースの DirectQuery では、追加のデータ ソースのサポート、DirectQuery モデルの計算テーブルおよび列の処理機能、バックエンド データベースに達する DAX 式を介した行レベルのセキュリティ、および以前のバージョンよりも高速なスループットを実現するクエリ最適化により、インメモリ モデルとの同等性が高まっています。
  
 表形式モデルは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、モデル、テーブル、リレーションシップ、および DAX 式を作成するためのデザイン画面を提供する表形式モデル プロジェクト テンプレートを使用して作成します。 複数のソースからデータをインポートした後、リレーションシップ、計算テーブルおよび列、メジャー、KPI、階層、および翻訳を追加して、モデルを拡充することができます。  
  
 モデルは、クライアント レポート アプリケーションの接続先の、表形式サーバー モード用に構成された Analysis Services のインスタンスに配置できます。 配置済みのモデルは、SQL Server Management Studio で多次元モデルのように管理できます。 また、最適処理のためにパーティション分割したり、ロール ベースのセキュリティを使用して行レベルに保護したりすることもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [表形式モデル ソリューション &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) - このセクションのトピックでは、表形式モデル ソリューションの作成と配置について説明します。
  
 [表形式モデル データベース &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) - このセクションのトピックでは、配置された表形式モデル ソリューションの管理について説明します。
  
 [表形式モデル データ アクセス](../../analysis-services/tabular-models/tabular-model-data-access.md) - このセクションのトピックでは、配置された表形式モデル ソリューションへの接続について説明します。
  
## <a name="see-also"></a>参照  
 [Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)   
 [テーブル ソリューションと多次元ソリューションの比較 (SSAS)](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [ツールと Analysis Services で使用されるアプリケーション](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [DirectQuery モード &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
