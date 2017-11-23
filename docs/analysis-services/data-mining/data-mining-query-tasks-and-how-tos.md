---
title: "データ マイニング クエリ タスクと操作方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mining models [Analysis Services], how-to topics
ms.assetid: 1bc2a775-6e62-4c66-a53c-201f2ea66295
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ffbdae6e1ffbd491d1191df8543e8b3f831921d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="data-mining-query-tasks-and-how-tos"></a>データ マイニングのクエリ タスクと操作方法
  データ マイニング モデルを利用する場合は、クエリを作成できることが不可欠です。 ここでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で提供されるツールを使用して、データ マイニング モデルに対するクエリの作成例のリンクを示します。 データ マイニング クエリとは何かに関する情報、または作成できるさまざまな種類のクエリに関する情報が必要な場合は、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
## <a name="creating-queries-with-prediction-query-builder"></a>予測クエリ ビルダーでのクエリの作成  
 予測クエリ ビルダーは、データ マイニング モデルに対するクエリをグラフィカルに作成する方法として [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の両方で提供されます。 次の各トピックでは、モデルの選択、データ ソースの指定、予測のカスタマイズ、および出力の保存の方法について説明します。  
  
-   [予測クエリ ビルダーを使用した予測クエリの作成](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [データ マイニング デザイナーでの単一クエリの作成](../../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)  
  
-   [予測クエリ ビルダーを使用した予測クエリの作成](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [予測クエリの結果の表示および保存](../../analysis-services/data-mining/view-and-save-the-results-of-a-prediction-query.md)  
  
-   [手動での予測クエリの編集](../../analysis-services/data-mining/manually-edit-a-prediction-query.md)  
  
-   [モデルへの予測関数の適用](../../analysis-services/data-mining/apply-prediction-functions-to-a-model.md)  
  
-   [予測クエリの入力データの選択およびマップ](../../analysis-services/data-mining/choose-and-map-input-data-for-a-prediction-query.md)  
  
## <a name="using-other-data-mining-query-tools"></a>他のデータ マイニング クエリ ツールの使用  
 予測クエリ ビルダーの使用に加えて、DMX または XMLA を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にクエリを直接入力することもできます。 プログラムを使用して予測クエリを作成し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに送信することもできます。 次の各トピックでは、予測クエリ ビルダーの外部で予測クエリを作成および操作する方法の詳細を説明します。  
  
 [テンプレートからの単一予測クエリの作成](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のツールを使用して、予測クエリを作成および実行する方法について説明します。  
  
 [テンプレートからの単一予測クエリの作成](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に付属しているテンプレートを使用して、予測クエリにパラメーターを追加する方法について説明します。  
  
 [データ マイニング クエリのタイムアウト値の変更](../../analysis-services/data-mining/change-the-time-out-value-for-data-mining-queries.md)  
 データ マイニング クエリ関連の動作を制御するサーバーのプロパティを設定する方法について説明します。  
  
 [マイニング モデルのコンテンツ クエリの作成](../../analysis-services/data-mining/create-a-content-query-on-a-mining-model.md)  
 データ マイニング スキーマ行セットを使用して、マイニング モデルに格納されている詳細情報を返すクエリを作成する方法について説明します。  
  
 [XMLA を使用したデータ マイニング クエリの作成](../../analysis-services/data-mining/create-a-data-mining-query-by-using-xmla.md)  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の XMLA テンプレートを使用して、マイニング モデル コンテンツに対するクエリを作成する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [クエリと式言語のリファレンス (Analysis Services)](http://msdn.microsoft.com/library/9597533d-35f4-4742-9d8c-7af392163527)   
 [データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md)  
  
  
