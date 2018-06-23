---
title: '作業 3: を作成して、照合データ品質プロジェクトを実行している |Microsoft ドキュメント'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2080aac8b429a9bc3ae21313f2163316b6cebeae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178772"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>タスク 3: 照合するデータ品質プロジェクトを作成および実行する
  ここでは、照合アクティビティ用のデータ品質プロジェクトを作成し、クレンジングされた仕入先データで照合プロセスを実行して、データ内の重複部分を削除します。  
  
1.  メイン ページで、 **DQS クライアント**をクリックして**新しいデータ品質プロジェクト**です。  
  
2.  型**Remove Supplier Duplicates**から、**プロジェクトの名前**です。  
  
3.  選択**Suppliers** Kb の一覧から、**ナレッジ ベースを使用**フィールドです。 前のレッスンでは、このナレッジ ベースの照合ポリシーを作成しました。  
  
4.  選択**照合**から、**アクティビティのリスト**右下のペインからです。  
  
     ![新しいデータ品質プロジェクトの選択に一致する](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "新しいデータ品質プロジェクトの選択に一致します。")  
  
5.  **[次へ]** をクリックします。  
  
6.  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。  
  
7.  をクリックして**参照**を選択し、 **Cleansed Supplier List.xls**、これは、クレンジング アクティビティの出力ファイル。  
  
8.  マップ**SupplierID**を基になる列、 **Supplier ID**ドメイン、 **Supplier Name**列**Supplier Name**ドメイン、および**ContactEmailAddress**列**Contact Email**ドメイン。  
  
9. をクリックして**次**に切り替えるには、**照合**ページ。  
  
10. をクリックして**開始**照合プロセスを開始します。 照合ポリシーを定義する際に同じ入力ファイルを使用したため、前のタスクの結果と同様の結果が表示されます。  
  
11. リスト ボックスのすべての一致レコードと照合スコアを確認します。 この結果は、前のタスクで表示された結果と同じになります。 この照合アクティビティの結果を解析するには、前のタスクの手順を参照してください。  
  
12. をクリックして**次**に切り替えるには、**エクスポート**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)  
  
  