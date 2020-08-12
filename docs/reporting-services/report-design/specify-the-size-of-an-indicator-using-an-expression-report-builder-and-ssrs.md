---
title: 式を使用したインジケーターのサイズの指定 (レポート ビルダー) | Microsoft Docs
description: レポート ビルダーで、色、方向、形状に加えてサイズを使用して、インジケーターの視覚的効果を最大限にする方法について説明します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b699e22bfe392ae04cbfb504f09e3faba48b08b9
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681591"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a>式を使用したインジケーターのサイズの指定 (レポート ビルダーおよび SSRS)
  インジケーターは、色、方向、形状のほか、サイズを変更して、視覚的効果を高めることができます。  
  
 インジケーターには、IndicatorStates という名前のインジケーターの状態のコレクションがあります。 一般に、IndicatorStates コレクションには複数の状態があります。 各状態は、コレクションのメンバーであり、アイコンで表示されます。 各状態をまとめて IndicatorStates コレクションが構成されます。  
  
 アイコンのサイズを動的に構成するには、レポート ビルダーのプロパティ ペインにある IndicatorStates コレクションのメンバーのプロパティを設定します。 **プロパティ** ペインが表示されていない場合は、 **[表示]** タブをクリックし、 **[プロパティ]** をクリックします。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、 **[プロパティ]** ウィンドウを使用して、メンバーのプロパティを設定します。 **[プロパティ]** ウィンドウが開いていない場合は、F4 キーを押します。  
  
 **プロパティ** ペインでは、インジケーターの IndicatorStates コレクションのプロパティにアクセスできます。 アイコンを異なるサイズになるように構成するには、式を使用して IndicatorStates コレクション メンバーの ScaleFactor プロパティを設定します。 詳細については、「[式 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)」を参照してください。  
  
 この手順で使用する式は、「 [インジケーター &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)をクリックします。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a>式を使用してインジケーターのアイコン サイズを指定するには  
  
1.  変更するインジケーターをクリックします。  
  
2.  プロパティ ペインで、IndicatorStates プロパティを探します。  
  
     プロパティ ペインがカテゴリごとに整理されている場合は、 **[状態]** カテゴリ内に IndicatorStates があります。  
  
3.  IndicatorStates の横にある参照ボタン ( **[...]** ) をクリックします。 **[インジケーターの状態コレクション エディター]** ダイアログ ボックスが開きます。  
  
     コレクションのメンバーをすべて選択します。  
  
4.  **[プロパティの複数選択]** の一覧で、ScaleFactor の横にある下矢印をクリックし、 **[式]** をクリックします。  
  
5.  **[式]** ダイアログ ボックスで、式を作成します。  
  
     次のサンプル式では、 **SalesYTD** フィールドの値に基づいて、アイコンのサイズが異なります。  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     詳細については、「[式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)」を参照してください。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [インジケーター &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
