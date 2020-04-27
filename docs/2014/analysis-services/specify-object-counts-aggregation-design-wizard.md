---
title: オブジェクトカウントの指定 (集計のデザインウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 305d9d79-d1ab-4704-a7b5-3283842b3996
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d616997d3764aad42691d9ef3c213d553b5f311
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068309"
---
# <a name="specify-object-counts-aggregation-design-wizard"></a>[オブジェクト カウントの指定] (集計のデザイン ウィザード)
  **[オブジェクト カウントの指定]** ページを使用すると、キューブ内のオブジェクト数を自動的に計算したり、推定カウントを手動で入力したりできます。 集計のデザイン ウィザードでは、オブジェクト カウントを使用してストレージ要件を推定します。  
  
## <a name="options"></a>オプション  
 **[キューブ オブジェクト]**  
 キューブ内のディメンションおよび属性を表示します。 カウントを指定する必要がある唯一`AggregationUsage`の属性で`None`あるため、ウィザードの [**集計使用法の確認**] ページでプロパティがに設定されていない属性のみが表示されます。  
  
 **[推定カウント]**  
 メジャー グループ内の推定行数およびデータベース ディメンション内の属性の推定メンバー数を表示します。 推定カウントとして使用する値を入力することも、推定カウントの値を計算することもできます。 カウント値を計算するには`0` 、フィールドに「」と入力し、[**カウント**] をクリックします。 既にカウントが表示されているフィールドは更新されません。  
  
 **パーティション数**  
 (省略可) メジャー グループ内の推定行数およびパーティション内の属性の推定メンバー数を入力します。  
  
 **Count**  
 空のすべてのフィールドに対する **[推定カウント]** 列の値を計算し、再作成します。 既にカウントが表示されているフィールドは更新されません。  
  
## <a name="see-also"></a>参照  
 [集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード &#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
