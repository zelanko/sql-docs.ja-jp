---
title: フィルター ページで、グラフのダイアログ ボックス (レポート ビルダーおよび SSRS) |Microsoft ドキュメント
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
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5b695b45a43f388a7dabf64bad327404ef4f6510
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164731"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a>[フィルター] ページ (グラフのダイアログ ボックス) (レポート ビルダーおよび SSRS)
  をクリックして**フィルター**でします。  
  
-   **[カテゴリ グループのプロパティ]** ダイアログ ボックス。カテゴリ別にグループ化された系列内のデータ ポイントをフィルターできます。  
  
-   **[グラフのプロパティ]** ダイアログ ボックス。グラフのフィルター処理オプションを定義できます。  
  
-   **[系列グループのプロパティ]** ダイアログ ボックス。選択したグループの系列の数を制限できます。  
  
## <a name="options"></a>および  
 **[追加]**  
 クリックして、一覧に新しいフィルター句を追加します。  
  
 **Delete**  
 選択したフィルター句を一覧から削除します。  
  
 **上矢印**  
 クリックして、選択したフィルターを一覧内で上に移動します。  
  
 **下矢印**  
 クリックして、選択したフィルターを一覧内で下に移動します。  
  
 **[式]**  
 フィルターを適用する式を入力または選択します。 式を編集するには、式 (**[fx]**) ボタンをクリックします。  
  
 **データ型**  
 **[値]** のデータ型を選択します。 可能であれば、 **[式]** のデータ型と一致するデータ型を選択します。  
  
 **[式]** および **[値]** の値は、同じデータ型に評価される必要があります。 たとえば、 **[式]** が System.Int32 データ型のフィールドに設定され、 **[値]** が 7 に設定されている場合、ドロップダウン リストから **Integer**を選択します。  
  
 必要なデータ型のオプションがドロップダウン リストにない場合は、値を正しいデータ型に変換する式を作成します。 詳細については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。  
  
 **[演算子]**  
 式と値の比較に使用する演算子を選択します。  
  
 **Value**  
 **[式]** で指定した式の評価対象となる式または値を入力します。  
  
## <a name="see-also"></a>参照  
 [データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [フィルター、グループ、およびデータを並べ替える&#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  