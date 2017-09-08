---
title: "データ (SSAS テーブル) の処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6fc5d0e934ae7fe4d7f9a00594c2f1ffd21bda1c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="process-data-ssas-tabular"></a>データの処理 (SSAS テーブル)
  キャッシュ モードでデータをテーブル モデルにインポートするときは、そのデータのインポート時点でのスナップショットを取得することになります。 場合によっては、そのデータは変更されることはないため、モデルで更新される必要はありません。 ただし、インポートするデータが定期的に変更され、かつデータ ソースから取得した最新データをモデルで反映できるようにするため、そのデータを処理 (更新) し計算済みデータを再計算しなければならなくなる可能性が高くなります。 モデルのデータを更新するため、すべてのテーブルと個別のテーブルでパーティションまたはデータ ソース接続ごとに処理を実行します。  
  
 モデル プロジェクト作成時には、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で処理アクションを手動で開始する必要があります。 モデルを配置した後は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して処理操作を実行するか、スクリプトを使用してスケジュールできます。 ここで説明するタスクはすべて、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でのモデル作成時に実行できる処理アクションに関係します。 配置済みモデルの処理アクションの詳細については、「[データベース、テーブル、またはパーティションの処理 &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)」をご覧ください。  
  
## <a name="related-tasks"></a>関連タスク  
  
|トピック|Description|  
|-----------|-----------------|  
|[データの手動処理 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/manually-process-data-ssas-tabular.md)|モデル ワークスペース データを手動で処理する方法について説明します。|  
|[データの処理のトラブルシューティング &#40;SSAS テーブル&#41;](../../analysis-services/troubleshoot-process-data-ssas-tabular.md)|処理操作のトラブルシューティング方法について説明します。|  
  
  
