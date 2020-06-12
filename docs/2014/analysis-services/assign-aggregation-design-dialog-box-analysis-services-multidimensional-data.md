---
title: '[集計デザインの割り当て] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfc4f7a0847373360a79ddda366ad7aa3f02c5de
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527958"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a>[集計デザインの割り当て] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [集計デザインの割り当て] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、1 つまたは複数のコピー先パーティションに集計デザインを割り当てることができます。 **[集計デザインの割り当て]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** でパーティションまたは集計デザインを右クリックし、 **[集計デザインの割り当て]** をクリックします。  
  
## <a name="options"></a>オプション  
  
|期間|定義|  
|----------|----------------|  
|**[集計のデザイン]**|1 つまたは複数のコピー先パーティションに割り当てる集計デザインを選択します。|  
|**[コピー先パーティション]**|集計デザインを割り当てるパーティションを選択します。 次のグリッドを使用して、コピー先パーティションを指定します。<br /><br /> \<check box>: 列ヘッダーのチェックボックスをオンまたはオフにして、一覧表示されているすべてのパーティションを対象パーティションとして追加または除外します。 パーティション横にあるチェック ボックスをオンまたはオフにすることで、そのパーティションをコピー先パーティションとして選択または選択解除できます。<br /><br /> **パーティション**: パーティションの名前が表示されます。<br /><br /> [**ソース**: パーティションのソーステーブルまたはクエリを表示します。<br /><br /> **集計のデザイン**: パーティションの既存の集計デザインの名前が表示されます。|  
|**[集計デザインを含むパーティションを非表示にする]**|オンにすると、集計デザインが割り当てられていないパーティションだけが表示されます。|  
  
## <a name="see-also"></a>参照  
 [集計と集計デザイン](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
