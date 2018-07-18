---
title: 円グラフの値の開始位置を円の最上部にする (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 2da5ccaf0fe846a26959970bd9bf3e939b5a2558
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256261"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>円グラフの値の開始位置を円の最上部にする (レポート ビルダーおよび SSRS)
  円グラフでは、既定でデータセットの最初の値が円の最上部から 90 度の位置から開始されます。 最初の値の開始位置を最上部にすることが望ましい場合もあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>円グラフの開始位置を円の最上部にするには  
  
1.  円グラフをクリックします。  
  
2.  **プロパティ** ペインが開いていない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。  
  
3.  **プロパティ** ペインの **[カスタム属性]** で、 **[PieStartAngle]** を **0** から **270**に変更します。  
  
4.  **[実行]** をクリックして、レポートをプレビューします。  
  
 最初の値の開始位置が円グラフの最上部になります。  
  
## <a name="see-also"></a>参照  
 [グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md)   
 [円グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
