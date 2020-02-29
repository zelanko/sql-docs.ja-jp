---
title: 'タスク 3: 照合用のデータ品質プロジェクトを作成して実行する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c6953214bd5e5353643cb16b75ed51ac18783256
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171771"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>タスク 3: 照合するデータ品質プロジェクトを作成および実行する
  ここでは、照合アクティビティ用のデータ品質プロジェクトを作成し、クレンジングされた仕入先データで照合プロセスを実行して、データ内の重複部分を削除します。

1.  **DQS クライアント**のメインページで、[**新しいデータ品質プロジェクト**] をクリックします。

2.  「**削除業者の重複**を**プロジェクトの名前**から削除」と入力します。

3.  [**ナレッジベースを使用**] フィールドの kb の一覧から [**仕入先**] を選択します。 前のレッスンでは、このナレッジ ベースの照合ポリシーを作成しました。

4.  右下のペインで、**アクティビティの一覧**から [**照合**] を選択します。

     ![新しいデータ品質プロジェクト - 照合が選択された状態](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "新しいデータ品質プロジェクト - 照合が選択された状態")

5.  **[次へ]** をクリックします。

6.  
  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。

7.  [**参照**] をクリックして、クレンジングアクティビティの出力ファイルである [クレンジングされた**Supplier List .xls**] を選択します。

8.  [**仕入先** **ID** ] ドメイン、[ **supplier name** ] 列を [supplier **Name** domain] にマップし、 **ContactEmailAddress**列を [ **Contact Email** domain] にマップします。

9. [**次へ**] をクリックして、**一致**するページに移動します。

10. [**開始**] をクリックして照合プロセスを開始します。 照合ポリシーを定義する際に同じ入力ファイルを使用したため、前のタスクの結果と同様の結果が表示されます。

11. リスト ボックスのすべての一致レコードと照合スコアを確認します。 この結果は、前のタスクで表示された結果と同じになります。 この照合アクティビティの結果を解析するには、前のタスクの手順を参照してください。

12. [**次へ**] をクリックして、[**エクスポート**] ページに移動します。

## <a name="next-step"></a>次のステップ
 [タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


