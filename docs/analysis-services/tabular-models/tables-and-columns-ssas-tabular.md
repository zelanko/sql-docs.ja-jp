---
title: "テーブルと列 (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c428d717-05de-436c-b9dc-e8c1925a60ca
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 91d370b9e71d843aa9a8ef8848b7cd63b38f0880
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="tables-and-columns-ssas-tabular"></a>テーブルと列 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]新しい列データの追加、テーブル間のリレーションシップを作成する、データを拡張する計算の定義しフィルター処理およびデータの並べ替えによって、テーブルの操作を開始するにはテーブルのインポート ウィザードを使用して、モデルにテーブルとデータを追加したが後、見やすくするためのテーブルです。  
  
 このトピックのセクション:  
  
-   [利点](#bkmk_benefits)  
  
-   [テーブルと列の操作](#bkmk_working)  
  
-   [関連タスク](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a> 利点  
 テーブル モデルのテーブルのフレームワークを使用して、列および他のメタデータを定義できます。 テーブルは次の要素で構成されます。  
  
 **テーブル定義**  
 テーブル定義には列のセットが含まれます。 列は、計算列と同様に、手動でデータ ソースからインポートしたり、追加することもできます。  
  
 **テーブルのメタデータ**  
 リレーションシップ、メジャー、ロール、パースペクティブ、および貼り付けられたデータはすべて、テーブルのコンテキスト内のオブジェクトを定義するメタデータです。  
  
 **Data**  
 データは、テーブルのインポート ウィザードを使用するか計算列で新しいデータを作成してテーブルを最初にインポートしたときに、テーブル列に入力されます。 ソースでデータが変更されるか、モデルがメモリから削除された場合は、テーブルにデータを再入力する処理操作を実行する必要があります。  
  
##  <a name="bkmk_working"></a> テーブルと列の操作  
 モデル デザイナーで直接新しいモデル テーブルを作成することはありません。 別のデータ ソースからデータをインポートまたはコピーしたときに、新しいタブが自動的に作成されます。 モデル デザイナーの各タブには、次のような項目を含むデータのテーブルが 1 つ含まれています。  
  
-   リレーショナル データベースや、Analysis Services キューブなどのその他の非リレーショナル ソースからの 1 つのテーブルまたはビュー。  
  
-   フィード ファイルまたはテキスト ファイルからインポートされた表形式のデータセット。  
  
-   テーブルにコピーまたは貼り付けられたリレーショナル データと表形式 (HTML) データの組み合わせ。  
  
 データをインポートすると、各テーブルやビュー、シート、データのファイルがテーブルとしてモデル デザイナーに追加されます。 通常はソースごとに別々のタブにデータを追加しますが、**[貼り付け]** および **[貼り付け追加]** を使用すると 1 つのテーブルにデータを結合することができます。 詳細については、「[ &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)」を参照してください。  
  
 必要なデータをすべて追加した後で、テーブル、参照、または参照関連値の間の追加のリレーションシップを他のテーブルで作成したり、新しい計算列を追加して派生値を作成したりできます。  
  
 非常に大きなデータ セットを操作する場合は、特定のデータを表示しないように除外できます。 また、異なる順序でデータを並べ替えることもできます。 モデル デザイナーを使用すると、列全体または特定のデータを表示または非表示にするためにフィルター処理、並べ替え、および非表示機能を使用できます。  
  
##  <a name="bkmk_related_tasks"></a> 関連タスク  
  
|トピック|Description|  
|-----------|-----------------|  
|[列のテーブルへの追加 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)|テーブル定義にソース列を追加する方法について説明します。|  
|[列の削除 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/delete-a-column-ssas-tabular.md)|モデル デザイナー、または [テーブルのプロパティ] ダイアログ ボックスを使用して、モデル テーブルの列を削除する方法について説明します。|  
|[テーブル、列、または行のフィルターのマッピングの変更 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/change-table-column-or-row-filter-mappings-ssas-tabular.md)|[テーブルのプロパティの編集] ダイアログ ボックスのテーブルのプレビューまたは SQL クエリ エディターを使用して、テーブル、列、または行のフィルターのマッピングを変更する方法について説明します。|  
|[タイム インテリジェンスで使用する [日付テーブルとしてマーク] の指定 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|[日付テーブルとしてマーク] ダイアログ ボックスを使用して、日付テーブルと一意識別子列を指定する方法について説明します。 DAX 式でタイム インテリジェンス関数を使用する場合は、日付テーブルと一意識別子の指定が必要です。|  
|[テーブルの追加 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/add-a-table-ssas-tabular.md)|既存のデータ ソース接続を使用して、データ ソースからテーブルを追加する方法について説明します。|  
|[テーブルの削除 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)|モデル ワークスペース データベース内の不要なテーブルを削除する方法について説明します。|  
|[テーブルまたは列名の変更 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/rename-a-table-or-column-ssas-tabular.md)|モデル内で識別できるようにテーブルまたは列の名前を変更する方法について説明します。|  
|[列のデータ型の設定 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)|列のデータ型を変更する方法について説明します。 データ型は、列のデータの格納および表示方法を定義します。|  
|[列の非表示または固定 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/hide-or-freeze-columns-ssas-tabular.md)|表示しない列を非表示にする方法、およびモデルのある領域内の特定の列を固定 (ロック) して、その領域を表示したまま別の領域にスクロールする方法について説明します。|  
|[計算列 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/ssas-calculated-columns.md)|このセクションのトピックでは、計算列を使用して集計データをモデルに追加する方法について説明します。|  
|[データのフィルター処理と並べ替え &#40;SSAS テーブル&#41;](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)|このセクションのトピックでは、モデル デザイナーのコントロールを使用してデータのフィルター処理または並べ替えを実行する方法について説明します。|  
  
  
