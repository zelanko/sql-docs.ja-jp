---
title: レポートのパラメーター ペインをカスタマイズする (レポート ビルダー) | Microsoft Docs
description: レポート ビルダーでパラメーターを使用してページ分割されたレポートを作成するときに、[パラメーター] ウィンドウをカスタマイズする方法について説明します。
ms.date: 06/15/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 4ce9e8d5-911a-4422-928f-a8d005b79fc6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 29bd397d64280644394077a29a3420dbf43b5e6f
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796563"
---
# <a name="customize-the-parameters-pane-in-a-report-report-builder"></a>Customize the Parameters Pane in a Report (Report Builder)
  レポート ビルダーでパラメーターを使用して改ページ調整されたレポートを作成するときに、パラメーター ペインをカスタマイズできます。 レポート デザイン ビューで、パラメーター ペインの特定の列や行にパラメーターをドラッグできます。 列を追加または削除して、ペインのレイアウトを変更することもできます。

 ペイン内で新しい列や行にパラメーターをドラッグすると、 **レポート データ** ペインのパラメーターの順序が変わります。 **レポート データ** ペインでパラメーターの順序を変更すると、ペインでのパラメーターの位置が変わります。 パラメーターの順序が重要である理由については、「[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。

## <a name="to-customize-the-parameters-pane"></a>パラメーター ペインをカスタマイズするには

1.  **[ビュー]** タブで **[パラメーター]** チェック ボックスをオンにして、パラメーター ペインを表示します。

     ![[ビュー] タブからパラメーター ペインにアクセスする](../../reporting-services/report-design/media/ssrs-customparameter-accessparameterpanedesignmode.png "[ビュー] タブからパラメーター ペインにアクセスする")

     デザイン画面の上部にペインが表示されます。

2.  ペインにパラメーターを追加するには、次のいずれかの操作を行います。

    -   パラメーター ペインで空のセルを右クリックし、 **[パラメーターの追加]** をクリックします。

         ![パラメーター ペインから新しいパラメーターを追加する](../../reporting-services/report-design/media/ssrs-customizeparameter-addnewparameter.png "パラメーター ペインから新しいパラメーターを追加する")

    -   **レポート データ** ペインの **[パラメーター]** を右クリックし、 **[パラメーターの追加]** をクリックします。

3.  パラメーターをパラメーター ペインの新しい場所に移動するには、ペインの異なるセルにパラメーターをドラッグします。

     ペインでパラメーターの位置を変更すると、 **レポート データ** ペインの **[パラメーター]** ボックスの一覧でパラメーターの順序が自動的に変わります。 パラメーターの順序の影響については、「[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。

4.  パラメーターのプロパティにアクセスするには、次のいずれかの操作を行います。

    -   パラメーター ペインでパラメーターを右クリックし、 **[パラメーターのプロパティ]** をクリックします。

         ![パラメーター ペインからパラメーターのプロパティにアクセスする](../../reporting-services/report-design/media/ssrs-customizeparameter-accessparameterproperties-composite.png "パラメーター ペインからパラメーターのプロパティにアクセスする")

    -   **レポート データ** ペインでパラメーターを右クリックし、 **[パラメーターのプロパティ]** をクリックします。

5.  ペインに新しい列や行を追加するには、または既存の行や列を削除するには、パラメーター ペインのどこかを右クリックし、表示されるメニューでコマンドをクリックします。

     ![パラメーター ペインに列と行を追加する](../../reporting-services/report-design/media/ssrs-customparameter-addcolumnsrows.png "パラメーター ペインに列と行を追加する")

    > [!IMPORTANT]
    >  パラメーターを含む列または行を削除すると、レポートからパラメーターが削除されます。

6.  ペインとレポートからパラメーターを削除するには、次のいずれかの操作を行います。

    -   パラメーター ペインでパラメーターを右クリックし、  **[削除]** をクリックします。

         ![パラメーター ペインからパラメーターを削除する](../../reporting-services/report-design/media/ssrs-customparameter-deleteparameter.png "パラメーター ペインからパラメーターを削除する")

    -   **レポート データ** ペインでパラメーターを右クリックし、 **[削除]** をクリックします。

## <a name="hiddeninternal-parameters-during-runtime"></a>実行時の非表示または内部パラメーター
非表示または内部パラメーターがある場合、それは次のロジックに従い、実行時に空の領域としてレンダリングされます。

   - 任意の行または列に、非表示または内部パラメーター、または空セルしかない場合、その行または列全体が実行時にレンダリングされません
   - それ以外の場合、非表示または内部パラメーターまたは空のセルは、空の領域としてレンダリングされます

`ReportParameter1` が非表示で、残りのパラメーターが表示の場合は、次のようになります。

![非表示のパラメーター 例 1](../../reporting-services/report-design/media/ssrs-hidden-parameter-rb-1.png "レイアウト グリッドに非表示パラメーターが 1 つある場合")

最初の列または最初の行に表示されるパラメーターがあるため、これは実行時に空の領域になります。

![非表示のパラメーター 例 1 - 実行時](../../reporting-services/report-design/media/ssrs-hidden-parameter-server-1.png "レイアウト グリッドに非表示パラメーターが 1 つある場合、実行時には空の領域になる")

同じ例で、`ReportParameter3` も非表示に設定した場合は、次のようになります。

![非表示のパラメーター 例 2](../../reporting-services/report-design/media/ssrs-hidden-parameter-rb-2.png "同じ列に非表示パラメーターが 2 つある場合")

列全体が空と見なされているため、実行時に最初の列はレンダリングされません。

![非表示のパラメーター 例 2 - 実行時](../../reporting-services/report-design/media/ssrs-hidden-parameter-server-2.png "同じ列に非表示パラメーターが 2 つある場合の実行時")

## <a name="default-layout"></a>既定のレイアウト
SQL Server Reporting Services 2016 より前に作成されたレポートでは、パラメーターの既定のレイアウト グリッドとして、2 列、N 行が実行時に使用されます。 既定のレイアウトを変更するには、Microsoft レポート ビルダーでそのレポートを開き、レポートを保存します。 レポートを保存すると、カスタマイズしたパラメーターのレイアウト情報が .rdl ファイルに保存されます。


## <a name="see-also"></a>関連項目
 [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)


