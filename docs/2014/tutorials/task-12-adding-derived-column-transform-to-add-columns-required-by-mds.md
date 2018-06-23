---
title: 'タスク 12: 派生 Required by MDS 列を追加する列の変換. |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b81dd18f0ba79167a66b5cdd09c2059fcd0e0a96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176070"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>タスク 12: 派生列変換を追加して MDS で必要な列を追加する
  ここでは、派生列変換をデータ フローに追加します。 2 つの派生列を追加する**ImportType**と**BatchTag**をこの変換に渡されるレコード。 MDS のステージング テーブルにデータをアップロードする前に、これらの列を追加する必要があります。 これら 2 つは、MDS のステージング テーブルに必要な列です。 参照してください[リーフ メンバー ステージング テーブル](http://msdn.microsoft.com/library/ee633854.aspx)詳細についてはします。  
  
1.  ドラッグ アンド ドロップ**派生列変換**から**共通**」の「、 **SSIS ツールボックス**を**データ フロー**タブです。  
  
2.  右クリック**派生列**変換を実行、**データ フロー**タブをクリックし、をクリックして**の名前を変更**です。 型**Add Columns Required by MDS**とキーを押します**ENTER**です。  
  
3.  接続**Filter Duplicates**に**Add Columns Required by MDS**青色コネクタを使用します。 表示されるはずの**入出力の選択** ダイアログ ボックス。  
  
4.  **入出力の選択**ダイアログ ボックスで、**一意のレコード**、 をクリック**OK**です。  
  
     ![出力の選択 ダイアログ ボックスの入力](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "出力の選択 ダイアログ ボックスの入力")  
  
5.  をクリックして**SSIS**クリックしてメニュー バー**変数**です。  
  
6.  **変数**ウィンドウで、をクリックして**変数の追加**ツールバーのボタンをクリックします。  
  
     ![SSIS 変数 ウィンドウ](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS 変数 ウィンドウ")  
  
7.  型**ImportType**の**名前**と**2**の**値**です。 MDS のエンティティに新しいメンバーを追加するため、値には 2 を指定します。 このパラメーターの詳細については、「[リーフ メンバー ステージング テーブル](http://msdn.microsoft.com/library/ee633854.aspx)です。  
  
8.  をクリックして**変数の追加**ツールバーを再度クリックします。  
  
9. 型**BatchTag**の**名前****文字列**の**データ型**、および**EIMBatch**の**値**です。 **BatchTag**を MDS に送信されるバッチの一意の名前だけです。  
  
10. **データ フロー**  タブをダブルクリックして**Add Columns Required by MDS**です。  
  
11. **派生列変換エディター**  ダイアログ ボックスで、**下のペインで、リスト ボックス**、型**ImportType**の**派生列名**.  
  
12. 展開**変数とパラメーター** 、左ペインで、ドラッグ アンド ドロップ**user::importtype**を**式**列です。  
  
     ![派生列変換エディター](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "派生列変換エディター")  
  
13. 型**BatchTag**の次の行で、**派生列名**です。  
  
14. ドラッグ アンド ドロップ**user::batchtag**から**変数とパラメーター**を**式**列です。  
  
15. をクリックして**OK**を閉じる、**派生列変換** ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 13: データを書き込む OLE DB 変換先を MDS ステージング テーブルに追加する](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  