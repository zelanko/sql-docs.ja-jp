---
title: 集計のデザイン ウィザードの F1 ヘルプ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Aggregation Design Wizard
ms.assetid: 39e23cf1-6405-4fb6-bc14-ba103314362d
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5cc9101bf9f5d733ea00d50c90de1981c611d6aa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176718"
---
# <a name="aggregation-design-wizard-f1-help"></a>集計のデザイン ウィザードの F1 ヘルプ
  集計を利用するとパフォーマンスが向上しますが、これは [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が各クエリの基となるデータ ソースからデータを取得して再計算を行うのではなく、キューブのストレージから直接、事前に計算された合計を取得するためです。  
  
 こうした集計のデザインは、集計のデザイン ウィザードを使用して行います。 このウィザードでは、次の手順に従います。  
  
-   パーティション、メジャー グループ、またはキューブのストレージとキャッシュのオプションに対して、標準またはカスタムの設定を選択します。  
  
-   パーティション、メジャー グループ、またはキューブによって参照されるオブジェクトの推定カウントまたは実際のカウントを指定します。  
  
-   集計オプションと制限を指定して、デザインされた集計によって配信されるストレージとクエリのパフォーマンスを最適化します。  
  
-   パーティション、メジャー グループ、またはキューブの保存と処理 (省略可) を行い、定義された集計を生成します。  
  
 集計のデザイン ウィザードを使用した後で、使用法に基づく最適化ウィザードを使用して、キューブをクエリするビジネス ユーザーとクライアント アプリケーションの使用パターンに基づいて集計をデザインできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [変更するパーティションを選択して&#40;集計のデザイン ウィザード&#41;](select-partitions-to-modify-aggregation-design-wizard.md)  
  
-   [集計使用法の確認&#40;集計のデザイン ウィザード&#41;](review-aggregation-usage-aggregation-design-wizard.md)  
  
-   [オブジェクト カウントの指定&#40;集計のデザイン ウィザード&#41;](specify-object-counts-aggregation-design-wizard.md)  
  
-   [集計オプションの設定&#40;集計のデザイン ウィザード&#41;](set-aggregation-options-aggregation-design-wizard.md)  
  
-   [ウィザードの完了&#40;集計のデザイン ウィザード&#41;](completing-the-wizard-aggregation-design-wizard.md)  
  
## <a name="see-also"></a>参照  
 [集計と集計デザイン](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md)   
 [使用法に基づく最適化ウィザードの F1 ヘルプ](usage-based-optimization-wizard-f1-help.md)   
 [Analysis Services のウィザード&#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  