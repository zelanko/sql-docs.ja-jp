---
title: テーブル モデリング (SSAS テーブル) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df693d141f3a91c1c0b9b023a89d39c5f2c171ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085750"
---
# <a name="tabular-modeling-ssas-tabular"></a>テーブル モデリング (SSAS テーブル)
  表形式のモデルは、Analysis Services のメモリ内データベースです。 xVelocity メモリ内分析エンジン (VertiPaq) は、最新の圧縮アルゴリズムとマルチスレッド クエリ プロセッサを使用して、Microsoft Excel や Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのレポート クライアント アプリケーションによる、表形式のモデルのオブジェクトとデータへの高速アクセスを実現します。  
  
 表形式のモデルは、キャッシュ モードおよび DirectQuery モードの 2 つのモードによるデータ アクセスをサポートします。 キャッシュ モードでは、リレーショナル データベース、データ フィード、フラット テキスト ファイルなどの複数のソースからのデータを統合できます。 DirectQuery モードでは、メモリ内モデルをバイパスでき、クライアント アプリケーションはデータを (SQL Server リレーショナル) ソースで直接クエリできます。  
  
 表形式のモデルは、新しい表形式モデル プロジェクトのテンプレートを使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成されます。 複数のソースからデータをインポートしてから、リレーションシップ、計算列、メジャー、KPI、および階層を追加すると、階層モデルを拡充できます。 モデルは、クライアント レポート アプリケーションの接続先の Analysis Services のインスタンスに配置できます。 配置済みのモデルは、SQL Server Management Studio で多次元モデルのように管理できます。 また、最適処理のためにパーティション分割したり、ロール ベースのセキュリティを使用して行レベルに保護したりすることもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テーブル モデル ソリューション&#40;SSAS 表形式&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
 [表形式モデル データベース&#40;SSAS 表形式&#41;](tabular-model-databases-ssas-tabular.md)  
  
 [テーブル モデル データ アクセス](tabular-model-data-access.md)  
  
  