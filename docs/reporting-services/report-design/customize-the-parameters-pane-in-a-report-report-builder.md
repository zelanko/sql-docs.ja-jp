---
title: "レポートのパラメーター ペインをカスタマイズする (レポート ビルダー) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ce9e8d5-911a-4422-928f-a8d005b79fc6
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 7e31a23d41c011787960cc662c11f763bab7291b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="customize-the-parameters-pane-in-a-report-report-builder"></a>レポートのパラメーター ペインをカスタマイズする (レポート ビルダー)
  レポート ビルダーでパラメーターを使用して改ページ調整されたレポートを作成するときに、パラメーター ペインをカスタマイズできます。 レポート デザイン ビューで、パラメーター ペインの特定の列や行にパラメーターをドラッグできます。 列を追加または削除して、ペインのレイアウトを変更することもできます。  
  
 ペイン内で新しい列や行にパラメーターをドラッグすると、 **レポート データ** ペインのパラメーターの順序が変わります。 **レポート データ** ペインでパラメーターの順序を変更すると、ペインでのパラメーターの位置が変わります。 パラメーターの順序が重要である理由については、「[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="to-customize-the-parameters-pane"></a>パラメーター ペインをカスタマイズするには  
  
1.  **[ビュー]** タブで **[パラメーター]** チェック ボックスをオンにして、パラメーター ペインを表示します。  
  
     ![[ビュー] タブからパラメーター ペインにアクセスする](../../reporting-services/report-design/media/ssrs-customparameter-accessparameterpanedesignmode.png "[ビュー] タブからパラメーター ペインにアクセスする")  
  
     デザイン画面の上部にペインが表示されます。  
  
2.  ペインにパラメーターを追加するには、次のいずれかの操作を行います。  
  
    -   パラメーター ペインで空のセルを右クリックし、 **[パラメーターの追加]**をクリックします。  
  
         ![パラメーター ペインから新しいパラメーターを追加する](../../reporting-services/report-design/media/ssrs-customizeparameter-addnewparameter.png "パラメーター ペインから新しいパラメーターを追加する")  
  
    -   **レポート データ** ペインの **[パラメーター]** を右クリックし、 **[パラメーターの追加]**をクリックします。  
  
3.  パラメーターをパラメーター ペインの新しい場所に移動するには、ペインの異なるセルにパラメーターをドラッグします。  
  
     ペインでパラメーターの位置を変更すると、 **レポート データ** ペインの **[パラメーター]** ボックスの一覧でパラメーターの順序が自動的に変わります。 パラメーターの順序の影響については、「[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。  
  
4.  パラメーターのプロパティにアクセスするには、次のいずれかの操作を行います。  
  
    -   パラメーター ペインでパラメーターを右クリックし、 **[パラメーターのプロパティ]**をクリックします。  
  
         ![パラメーター ペインからパラメーターのプロパティにアクセスする](../../reporting-services/report-design/media/ssrs-customizeparameter-accessparameterproperties-composite.png "パラメーター ペインからパラメーターのプロパティにアクセスする")  
  
    -   **レポート データ** ペインでパラメーターを右クリックし、 **[パラメーターのプロパティ]**をクリックします。  
  
5.  ペインに新しい列や行を追加するには、または既存の行や列を削除するには、パラメーター ペインのどこかを右クリックし、表示されるメニューでコマンドをクリックします。  
  
     ![パラメーター ペインに列と行を追加する](../../reporting-services/report-design/media/ssrs-customparameter-addcolumnsrows.png "パラメーター ペインに列と行を追加する")  
  
    > [!IMPORTANT]  
    >  パラメーターを含む列または行を削除すると、レポートからパラメーターが削除されます。  
  
6.  ペインとレポートからパラメーターを削除するには、次のいずれかの操作を行います。  
  
    -   パラメーター ペインでパラメーターを右クリックし、  **[削除]**をクリックします。  
  
         ![パラメーター ペインからパラメーターを削除する](../../reporting-services/report-design/media/ssrs-customparameter-deleteparameter.png "パラメーター ペインからパラメーターを削除する")  
  
    -   **レポート データ** ペインでパラメーターを右クリックし、 **[削除]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)  
  
  
