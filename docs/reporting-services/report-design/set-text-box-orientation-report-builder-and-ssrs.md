---
title: テキストボックスの方向の設定 (レポート ビルダー) | Microsoft Docs
description: レポート ビルダーで、改ページされたレポートのテキスト ボックスをさまざまな方向に回転させる方法について説明します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 058da26bfe4fc5bf8ae5d777a35d0356b463ca11
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681381"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、さまざまな方向にテキスト ボックスを回転することができます。   
* 水平方向   
* 垂直方向 (90 度回転。テキストの読み取りは上から下、東アジア言語の文字を除く)

* 270 度回転 (テキストの読み取りは下から上)   
  
回転するのはテキストではなくテキスト ボックスであるため、対象のテキスト ボックス内のすべてのテキストに回転が適用されます。 テキストの一部のみに異なる方向を指定することはできません。 回転したテキストに合わせて、列の幅と行の高さを手動で調整してください。  
  
 テキストの向きを指定する WritingMode プロパティは、 **[テキスト ボックスのプロパティ]** ダイアログ ボックスにはありません。 このプロパティはプロパティ ペインで設定できます。   
  
## <a name="to-rotate-text"></a>テキストを回転するには  
  
1.  レポートを作成するか、または既存のレポートを開いてから、デザイン画面に [テキスト ボックスを追加](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) します。  
  
3.  回転するテキスト ボックスを選択します。  
  
2.  プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。  
  
4.  プロパティ ペインで、WritingMode プロパティを見つけて、テキスト ボックスに適用するテキストの向きを選択します。  
  
    > [!NOTE]  
    >  プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、 **[ローカライズ]** カテゴリ内にあります。  
  
5.  リスト ボックスで **[横]** 、 **[縦]** 、 **[270 度回転]** のいずれかを選択します。  
  
## <a name="see-also"></a>参照  
 [テキスト ボックス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [チュートリアル:テキストの書式設定 &#40;レポート ビルダー&#41;](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
