---
title: オブジェクト数の指定 (使用法に基づく最適化ウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e0503192c3c948110f8301c8eb375e1c8203e42f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068242"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a>[オブジェクト カウントの指定] (使用法に基づく最適化ウィザード)
  **[オブジェクト カウントの指定]** ページを使用すると、キューブ内のオブジェクト数を自動的に計算したり、推定カウントを手動で入力したりできます。 使用法に基づく最適化ウィザードでは、オブジェクト カウントを使用してストレージ要件を推定します。  
  
## <a name="options"></a>オプション  
 **[キューブ オブジェクト]**  
 キューブ内のディメンションおよび属性を表示します。 ウィザードの [**集計使用法**の確認`AggregationUsage` ] ページでプロパティが [なし] に設定されていない属性のみが表示されます。カウントを指定する必要がある属性はこれらの属性だけであるためです。  
  
 **[推定カウント]**  
 メジャー グループ内の推定行数およびデータベース ディメンション内の属性の推定メンバー数を表示します。 推定カウントとして使用する値を入力することも、推定カウントの値を計算することもできます。 カウントの値を計算するには、フィールドに「 0 」を入力して **[カウント]** をクリックします。 既にカウントが表示されているフィールドは更新されません。  
  
 **パーティション数**  
 (省略可) メジャー グループ内の推定行数およびディメンション内の属性の推定メンバー数を竜力します。  
  
 **Count**  
 空のすべてのフィールドに対する **[推定カウント]** 列の値を計算し、再作成します。 既にカウントが表示されているフィールドは更新されません。  
  
## <a name="see-also"></a>参照  
 [集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード &#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
