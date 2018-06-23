---
title: 系列へのツールヒントの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ae6fc4bd445be2aab739aa23b42d1aa5a6198879
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165515"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a>系列へのツールヒントの表示 (レポート ビルダーおよび SSRS)
  グラフの系列上の各データ ポイントにツールヒントを追加すると、表示されたレポートのデータ ポイントにユーザーがマウス カーソルを合わせたときにデータ ポイントに関連する情報 (グループ名、データ ポイントの値、系列の合計に対するデータ ポイントの比率など) が表示されます。  
  
 計算系列にはツールヒントを追加できません。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-tooltip-on-each-data-point"></a>各データ ポイントにツールヒントを指定するには  
  
1.  系列を右クリックするか、 **[値]** 領域のフィールドを右クリックし、 **[系列のプロパティ]** をクリックします。  
  
2.  **[系列データ]** をクリックし、 **ToolTip** プロパティに文字列または式を入力します。 グラフ固有のキーワードを使用して、グラフ上の別の要素を表すことができます。 詳細については、次を参照してください。 [、グラフの書式設定データ ポイント&#40;レポート ビルダーおよび SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)です。  
  
## <a name="see-also"></a>参照  
 [グラフのデータ ポイントの書式設定&#40;レポート ビルダーおよび SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](chart-legend-change-item-text-report-builder.md)   
 [グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [レポートへのドリルスルー アクションの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  