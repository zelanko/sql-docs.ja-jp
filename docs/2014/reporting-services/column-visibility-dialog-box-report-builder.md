---
title: '[列表示] ダイアログ ボックス (レポート ビルダー) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
caps.latest.revision: 12
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b5fbdc627473f449007af6dadcc73fcc69efc46f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173887"
---
# <a name="column-visibility-dialog-box-report-builder"></a>[列表示] ダイアログ ボックス (レポート ビルダー)
  **[列表示]** ダイアログ ボックスでは、選択した列をレポートの初期実行時に表示または非表示にする操作や、別のレポート アイテムを使用して列の表示を切り替える操作を行うことができます。  
  
## <a name="options"></a>および  
 **レポートが最初に実行時**  
 レポートにレポート アイテムを表示する際の初期設定を示すオプションを選択します。  
  
 **[表示]**  
 列を表示します。  
  
 **非表示にします。**  
 列を非表示にします。  
  
 **表示または非表示が式に基づく**  
 式を使用して初期表示を変化させます。  
  
 評価される式を入力、`Boolean`の値`True`アイテムを非表示にして`False`アイテムを表示します。 式を編集するには、式 (*[fx]*) ボタンをクリックします。  
  
 **このレポート アイテムでの表示の切り替えすることができます。**  
 HTML レポート ビューアーでこの列の表示/非表示をユーザーが切り替えられるようにするための切り替えイメージを表示します。  
  
 切り替えイメージを表示するレポートのテキスト ボックスの名前 (「Textbox1」など) を入力または選択します。 選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープに存在する必要があります。 たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。 グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。  
  
## <a name="see-also"></a>参照  
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [アイテムへの展開または折りたたみアクションの追加 &#40;レポート ビルダーおよび SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [イメージ&#40;レポート ビルダーおよび SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  