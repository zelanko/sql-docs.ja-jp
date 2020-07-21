---
title: '[行表示] ダイアログボックス (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5ad7e47457aa2d1f1d5e36adec7e988de7b8bbb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102347"
---
# <a name="row-visibility-dialog-box-report-builder"></a>[行表示] ダイアログ ボックス (レポート ビルダー)
  **[行表示]** ダイアログ ボックスを使用すると、選択した行をレポートの初回実行時に表示または非表示にすることも、別のレポート アイテムを使用して行の表示を切り替えることもできます。  
  
## <a name="options"></a>オプション  
 **[レポートの初期実行時]**  
 レポートに行を表示する際の初期設定を示すオプションを選択します。  
  
 **表示**  
 行を表示します。  
  
 **非表示**  
 行を非表示にします。  
  
 **[式を基に表示/非表示を切り替える]**  
 式を使用して初期表示を変化させます。  
  
 アイテムを非表示にする場合は `Boolean`、アイテムを表示する場合は `True` と評価される `False` 値の式を入力します。 式を編集するには、**式**([*fx*]) ボタンをクリックします。  
  
 **[次のレポート アイテムでの表示の切り替えを可能にする]**  
 ユーザーが HTML レポート ビューアーでこの行の表示/非表示を切り替えられるようにする切り替えイメージを表示します。  
  
 切り替えイメージを表示するレポートのテキスト ボックスの名前 (「Textbox1」など) を入力または選択します。 選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープに存在する必要があります。 たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。 グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。  
  
## <a name="see-also"></a>参照  
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [アイテムへの展開または折りたたみアクションの追加 &#40;レポートビルダーと SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [&#40;レポートビルダーと SSRS&#41;の画像](report-design/images-report-builder-and-ssrs.md)   
 [ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
