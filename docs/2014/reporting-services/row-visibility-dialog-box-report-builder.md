---
title: 行の表示 ダイアログ ボックス) (レポート ビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
caps.latest.revision: 13
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3dd8f40b00db99496d43199183ca34e95ca7dfc5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328825"
---
# <a name="row-visibility-dialog-box-report-builder"></a>[行表示] ダイアログ ボックス (レポート ビルダー)
  **[行表示]** ダイアログ ボックスを使用すると、選択した行をレポートの初回実行時に表示または非表示にすることも、別のレポート アイテムを使用して行の表示を切り替えることもできます。  
  
## <a name="options"></a>および  
 **レポートを最初に実行時**  
 レポートに行を表示する際の初期設定を示すオプションを選択します。  
  
 **[表示]**  
 行を表示します。  
  
 **非表示にします。**  
 行を非表示にします。  
  
 **表示または非表示の式を基に**  
 式を使用して初期表示を変化させます。  
  
 評価される式を入力、`Boolean`の値`True`アイテムを非表示にして`False`アイテムを表示します。 式を編集するには、 **[式]** (*[fx]*) ボタンをクリックします。  
  
 **このレポート アイテムが表示を切り替えることができます。**  
 ユーザーが HTML レポート ビューアーでこの行の表示/非表示を切り替えられるようにする切り替えイメージを表示します。  
  
 切り替えイメージを表示するレポートのテキスト ボックスの名前 (「Textbox1」など) を入力または選択します。 選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープに存在する必要があります。 たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。 グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。  
  
## <a name="see-also"></a>参照  
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [アイテムへの展開または折りたたみアクションの追加 &#40;レポート ビルダーおよび SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [イメージ&#40;レポート ビルダーおよび SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
