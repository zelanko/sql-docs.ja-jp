---
title: グラフの凡例項目を非表示にする (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 26e3fe8feb400bb9280a37f8f33bebf510377fe0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261878"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a>グラフの凡例項目を非表示にする (レポート ビルダーおよび SSRS)
  既定では、図形グラフ以外のグラフに追加した系列は、凡例の項目として使用されます。 円グラフ、ドーナツ グラフ、じょうごグラフ、およびピラミッド グラフでは、グラフに系列を追加すると、凡例に個々のデータ ポイントが追加されます。  
  
 凡例の任意の項目を非表示にすることができます。 凡例の項目を非表示にした場合も、グラフには表示されます。 これは、グラフに追加した系列の詳細な情報を表示したくないときに便利です。 たとえば、移動平均のような計算系列をグラフに追加した場合、凡例のこのエントリを非表示にし、元の系列の詳細な情報のみを表示できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a>凡例の項目を非表示にするには  
  
1.  非表示にする系列を右クリックし、 **[系列のプロパティ]** をクリックします。  
  
2.  **[凡例]** をクリックします。 **[凡例内の次の系列を非表示にする]** オプションを選択します。  
  
    > [!NOTE]  
    >  あるグループの系列を非表示にし、他のグループの系列を表示することはできません。 **[系列グループ]** 領域にフィールドを追加している場合、このグループに属するすべての系列は非表示になります。  
  
## <a name="see-also"></a>参照  
 [グラフの凡例の書式設定&#40;レポート ビルダーおよび SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [グラフのデータ ポイントの書式設定&#40;レポート ビルダーおよび SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](chart-legend-change-item-text-report-builder.md)   
 [グラフへの移動平均の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [[全般] ([凡例のプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
