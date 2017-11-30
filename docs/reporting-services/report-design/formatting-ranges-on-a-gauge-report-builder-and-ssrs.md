---
title: "ゲージの範囲の書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 851b829cf66a2d89ba2753381dc1598e5bc439b6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>ゲージの範囲の書式設定 (レポート ビルダーおよび SSRS)
 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、ゲージ範囲は、ゲージ上の値の重要なサブセクションを示す、ゲージ スケール上のゾーンまたは領域です。 ゲージ範囲を使用すると、ポインター値が特定の値範囲に入る時期を視覚的に示すことができます。 範囲は、開始値と終了値で定義されます。  
  
 また、範囲を使用して、ゲージのさまざまなセクションを定義することもできます。 たとえば、0 ～ 10 の値を持つゲージで、0 ～ 3 の値を持つ赤色の範囲を定義し、4 ～ 7 の値を持つ黄色の範囲を定義し、8 ～ 10 の値を持つ緑色の範囲を定義することができます。 指定した開始値が指定した終了値よりも大きい場合は、開始値が終了値になり、終了値が開始値になるように値が交換されます。  
  
 範囲は、スケールにポインターを配置するのと同じように配置することができます。 **[位置]** プロパティと **[スケールからの距離]** プロパティで範囲の位置を決定します。 詳しくは、「 [ゲージ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)」をご覧ください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>参照  
 [ゲージのスケールの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [ゲージのポインターの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [ゲージへの最小値または最大値の設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [チュートリアル: レポートへの KPI の追加 &#40;レポート ビルダー&#41;](../../reporting-services/tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [ゲージ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
