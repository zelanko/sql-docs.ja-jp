---
title: '[データマイニングのクエリ結果の保存] ダイアログボックス (マイニングモデル予測ビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0838c90f0797a0db9c8a66cd8c5f877aaecdad0a
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84538934"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a>[データ マイニングのクエリ結果を保存] ダイアログ ボックス ([マイニング モデル予測] ビュー)
  **[データ マイニングのクエリ結果を保存]** ダイアログ ボックスを使用すると、新しいテーブルに、データ マイニング クエリの結果を保存できます。  
  
 この新しいテーブルは、データ ソースで定義されたデータベースに作成されます。  
  
## <a name="options"></a>オプション  
 **データ ソース**  
 現在のプロジェクトからデータ ソースを選択します。 適切なデータ ソースがない場合には、 **[新規作成]** をクリックして新しいデータ ソースを作成します。  
  
 **[新規作成]**  
 **データ ソース ウィザード**を開きます。  
  
 **テーブル名**  
 新しいテーブルの名前を入力します。  
  
 **[存在する場合は上書きする]**  
 同じ名前を持つ既存のテーブルを上書きする場合は、このオプションをオンにします。  
  
 次のいずれかに該当する場合は、既存のテーブルを上書きする必要があります。  
  
-   予測クエリに列を追加した場合。  
  
-   予測クエリで列の名前やデータ型を変更した場合。  
  
-   対象となるテーブルで ALTER ステートメントを実行した場合。  
  
 複数の列の名前が同じである場合 (複数の派生列の名前が既定の列名 **Expression**である場合など) は、重複する名前を持つ各列に対して別名を作成する必要があります。 テーブル内の列には一意の名前が必要であるため、列に一意の名前が存在しない場合は、デザイナーが SQL Server に結果を保存しようとするとエラーが発生します。  
  
 **[DSV に追加]**  
 (省略可能) 既存のデータ ソースにテーブルを追加する場合に、プロジェクトに含まれているデータ ソース ビューを選択します。  
  
 このオプションは、モデルのすべての関連テーブル (トレーニングデータ、予測ソースデータ、クエリ結果など) を同じデータソースで保持する場合に便利です。  
  
## <a name="see-also"></a>参照  
 [予測クエリビルダー &#40;データマイニング&#41;](prediction-query-builder-data-mining.md)   
 [データマイニングクエリインターフェイス](data-mining/data-mining-query-tools.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
