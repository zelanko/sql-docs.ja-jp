---
title: "データ マイニング クエリのタイムアウト値の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cb73246a4187ff8b8360c4e2eb37f6eaacd44dd3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>データ マイニング クエリのタイムアウト値の変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]リフト チャートの作成または予測クエリを実行するときにかかる場合があります、予測に必要なすべてのデータの生成に時間。 クエリがタイムアウトするのを防ぐため、クエリの完了を [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーで待機する時間を制御する値を変更できます。  
  
 既定値は 15 ですが、モデルが複雑な場合やデータ ソースが大規模な場合、これでは十分でない場合があります。 必要に応じて値を大幅に増やし、処理に十分な時間を確保します。 たとえば、 **[クエリ タイムアウト]** を 600 に設定すると、クエリを 10 分間実行し続けることができます。  
  
 予測クエリの詳細については、「 [データ マイニングのクエリ タスクと操作方法](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)」を参照してください。  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>データ マイニング クエリのタイムアウト値の構成  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **[オプション]** ペインで **[ビジネス インテリジェンス デザイナー]**を展開します。  
  
3.  **[クエリ タイムアウト]** ボックスをクリックし、秒数の値を入力します。  
  
## <a name="see-also"></a>参照  
 [データ マイニングのクエリ タスクと操作方法](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
