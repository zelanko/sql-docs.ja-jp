---
title: オブジェクト カウント (集計のデザイン ウィザード) を指定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 305d9d79-d1ab-4704-a7b5-3283842b3996
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a31d248330d80e49a7669982e6ad3011fb7375e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085518"
---
# <a name="specify-object-counts-aggregation-design-wizard"></a>[オブジェクト カウントの指定] (集計のデザイン ウィザード)
  **[オブジェクト カウントの指定]** ページを使用すると、キューブ内のオブジェクト数を自動的に計算したり、推定カウントを手動で入力したりできます。 集計のデザイン ウィザードでは、オブジェクト カウントを使用してストレージ要件を推定します。  
  
## <a name="options"></a>および  
 **キューブ オブジェクト**  
 キューブ内のディメンションおよび属性を表示します。 持たない属性のみが`AggregationUsage`プロパティに設定`None`で、**集計使用法の確認**はカウントを指定するを必要とする唯一の属性であるために、ウィザードのページが表示されます。  
  
 **[推定カウント]**  
 メジャー グループ内の推定行数およびデータベース ディメンション内の属性の推定メンバー数を表示します。 推定カウントとして使用する値を入力することも、推定カウントの値を計算することもできます。 カウントの値を計算するには、入力`0`をクリックしてフィールド**カウント**です。 既にカウントが表示されているフィールドは更新されません。  
  
 **パーティションの数**  
 (省略可) メジャー グループ内の推定行数およびパーティション内の属性の推定メンバー数を入力します。  
  
 **Count**  
 空のすべてのフィールドに対する **[推定カウント]** 列の値を計算し、再作成します。 既にカウントが表示されているフィールドは更新されません。  
  
## <a name="see-also"></a>参照  
 [集計のデザイン ウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード&#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  