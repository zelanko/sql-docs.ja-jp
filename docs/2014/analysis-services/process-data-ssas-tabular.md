---
title: データの処理 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2066cb6d871f43dda719cab3539253db97bfca7
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84540064"
---
# <a name="process-data-ssas-tabular"></a>データの処理 (SSAS テーブル)
  キャッシュ モードでデータをテーブル モデルにインポートするときは、そのデータのインポート時点でのスナップショットを取得することになります。 場合によっては、そのデータは変更されることはないため、モデルで更新される必要はありません。 ただし、インポートするデータが定期的に変更され、かつデータ ソースから取得した最新データをモデルで反映できるようにするため、そのデータを処理 (更新) し計算済みデータを再計算しなければならなくなる可能性が高くなります。 モデルのデータを更新するため、すべてのテーブルと個別のテーブルでパーティションまたはデータ ソース接続ごとに処理を実行します。  
  
 モデル プロジェクト作成時には、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で処理アクションを手動で開始する必要があります。 モデルを配置した後は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して処理操作を実行するか、スクリプトを使用してスケジュールできます。 ここで説明するタスクはすべて、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]でのモデル作成時に実行できる処理アクションに関係します。 配置済みモデルの処理アクションの詳細については、「[データベース、テーブル、またはパーティションの処理](tabular-models/process-database-table-or-partition-analysis-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|トピック|説明|  
|-----------|-----------------|  
|[データの手動処理 (SSAS テーブル)](manually-process-data-ssas-tabular.md)|モデル ワークスペース データを手動で処理する方法について説明します。|  
|[データの処理のトラブルシューティング &#40;SSAS テーブル&#41;](troubleshoot-process-data-ssas-tabular.md)|処理操作のトラブルシューティング方法について説明します。|  
  
  
