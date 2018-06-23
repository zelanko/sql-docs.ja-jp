---
title: グラフの余白の追加または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 809c8f142fa7b796286d41c4a7389b760c76334f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175286"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a>グラフの余白の追加または削除 (レポート ビルダーおよび SSRS)
  縦棒グラフおよび散布図では、横余白が X 軸の両端に自動的に追加されます。 横棒グラフでは、横余白が Y 軸の両端に自動的に追加されます。 その他すべての種類のグラフでは、横余白は追加されません。 余白のサイズは変更できません。  
  
 このトピックは、円グラフ、ドーナツ グラフ、じょうごグラフ、またはピラミッド グラフには当てはまりません。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a>横余白を有効または無効にするには  
  
1.  軸を右クリックし、 **[軸のプロパティ]** を選択します。 **[縦軸のプロパティ]** ダイアログ ボックスまたは **[横軸のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[軸のオプション]** ページで、 **[横余白]** プロパティを設定します。  
  
    -   **[自動]** グラフの種類に基づいて横余白を追加するかどうかが判断されます。  
  
    -   **[無効]** 横棒グラフ、縦棒グラフ、および散布図では、横余白はなしになります。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [[軸のプロパティ] ダイアログ ボックス、[軸のオプション] &#40;レポート ビルダーおよび SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)   
 [軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)   
 [日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  