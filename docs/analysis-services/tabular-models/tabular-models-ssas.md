---
title: "表形式モデル |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/21/2018
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
ms.openlocfilehash: 2df607b47e4bb2a5a770e27d1bceb5a6d7e6ebbc
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-models"></a>テーブル モデル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
表形式モデルは、インメモリ モードまたは DirectQuery モードで実行される Analysis Services データベースで、バックエンド リレーショナル データ ソースから直接取得したデータにアクセスします。 最新の圧縮アルゴリズムおよびマルチ スレッド クエリ プロセッサを使用するは、分析エンジンは、Power BI と Excel などのクライアント アプリケーションを報告することによって、表形式モデル オブジェクトとデータを高速アクセスを提供します。  
  
 DirectQuery は、代替クエリ モードでは、モデルのインメモリ モデルでは、ログオフが、大きすぎて、メモリ内、またはデータの揮発性によって妥当な処理方法に収まりません。 DirectQuery ではさまざまなデータ ソース、DirectQuery モデルでは、バックエンド データベースにアクセスし、クエリを実行する DAX 式を使用して行レベルのセキュリティの計算されるテーブルと列を処理する機能のサポートにより、インメモリ モデルと同等の機能高速なスループットを最適化します。
  
 表形式モデルは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、モデル、テーブル、リレーションシップ、および DAX 式を作成するためのデザイン画面を提供する表形式モデル プロジェクト テンプレートを使用して作成します。 複数のソースからデータをインポートした後、リレーションシップ、計算テーブルおよび列、メジャー、KPI、階層、および翻訳を追加して、モデルを拡充することができます。  
  
 Azure Analysis Services に配置できるモデルまたは表形式サーバー モード用 SQL Server Analysis Services のインスタンスに構成します。 配置済みテーブル モデルは、SQL Server Management Studio で管理できます。 モデルが増すにつれて、それらは、処理を最適化するためにパーティション分割し、ロール ベース セキュリティを使用して行レベル セキュリティで保護できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テーブル モデル ソリューション](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md)-このセクションの記事では、作成および表形式モデル ソリューションの配置について説明します。
  
 [表形式モデル データベース](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)-このセクションの記事では、配置済みテーブル モデル ソリューションの管理について説明します。
  
 [表形式モデルのデータ アクセス](../../analysis-services/tabular-models/tabular-model-data-access.md)-このセクションの記事では、テーブル モデル ソリューションの配置への接続について説明します。
  
## <a name="see-also"></a>参照  
 [Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)   
 [表形式および多次元ソリューションの比較](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [ツールと Analysis Services で使用されるアプリケーション](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
