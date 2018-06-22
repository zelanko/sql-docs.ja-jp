---
title: データセットのプロパティ ダイアログ ボックスのフィールド (レポート ビルダー) |Microsoft ドキュメント
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
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 8e9fa18bb0edfc2edac3e58e22467ba49a01cf50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074769"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a>[フィールド] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  **[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** を選択すると、レポート データセットのフィールド コレクションを変更できます。 フィールドの一覧は自動的に作成されますが、 **[フィールド]** を使用してクエリ フィールドや計算フィールドを追加、編集、および削除することができます。  
  
 計算フィールドは埋め込みデータセットでのみサポートされています。 詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。  
  
## <a name="options"></a>および  
 **[追加]**  
 データセットに新しいクエリ フィールドまたは計算フィールドを追加します。  
  
 **Delete**  
 選択したフィールドをデータセットから削除します。  
  
 **フィールド名**  
 フィールドの名前を入力します。 フィールドはデータセット内で一意である必要があります。 データセット内の既存の各フィールドの名前はあらかじめ設定されています。  
  
 **[フィールド ソース]**  
 フィールドの値を入力します。  
  
 計算フィールドの場合、フィールド ソースは、データセット クエリで取得した既存のフィールドの名前か、ユーザーが作成した式である必要があります。 たとえば、Sales クエリ フィールドの値の 10 倍を表すフィールドを作成する場合は、 `=10 * Fields!Sales.Value`という式を使用します。  
  
 クエリ フィールドの場合、フィールド ソースは、データセット クエリで取得した既存のフィールドの名前である必要があります。  
  
 **式 ([fx])**  
 新しい計算フィールドを表す式を追加または変更します。 このボタンは、 **[追加]** をクリックして **[計算フィールド]** を選択した場合にのみ表示されます。  
  
## <a name="see-also"></a>参照  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [共有データセットまたは埋め込みデータセットの作成 &#40;レポート ビルダーおよび SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [データセットのプロパティ ダイアログ ボックス、オプション&#40;レポート ビルダー&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md)   
 [データセットのプロパティ ダイアログ ボックスのフィルター&#40;レポート ビルダー&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md)   
 [データセットのプロパティ ダイアログ ボックスで、パラメーター&#40;レポート ビルダー&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md)   
 [データセットのプロパティ ダイアログ ボックスでは、クエリ&#40;レポート ビルダー&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  