---
title: 'タスク 10: 重複部分を識別するあいまいグループ化変換を追加する |Microsoft ドキュメント'
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
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cf9ad3dff4737d7308e7ec3434985b18015f29d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083560"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>タスク 10: あいまいグループ化変換を追加して重複を識別する
  ここでは、あいまいグループ化変換をデータ フローに追加します。 あいまいグループ化変換は、変換元データの重複を識別する際に役立ちます。 参照してください[Fuzzy Grouping Transformation](http://msdn.microsoft.com/library/ms141764.aspx)詳細についてはします。  
  
1.  ドラッグ アンド ドロップ**あいまいグループ化**で変換**その他の変換**上、 **SSIS ツールボックス**を**データ フロー**  タブの下にある**正しい、修正されたレコードを結合**です。  
  
2.  右クリック**あいまいグループ化**変換を実行、**データ フロー**タブをクリックし、をクリックして**の名前を変更**です。 型**Id と一致するグループ仕入先**とキーを押します**ENTER**です。  
  
3.  接続**Combine Correct and Corrected Records**に**Id と一致するグループ仕入先**青色コネクタを使用します。  
  
     ![Id と一致するグループ仕入先への接続を](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Id と一致するグループ仕入先への接続")  
  
4.  ダブルクリックして**Id と一致するグループ仕入先**です。  
  
5.  **あいまいグループ化変換エディター**をクリックして**新規** の横に**OLE DB 接続マネージャーのドロップダウン リスト**を起動する**OLE DB 接続の構成Manager**  ダイアログ ボックス。  
  
6.  ダイアログ ボックスで、**新規**を起動する**接続マネージャー**  ダイアログ ボックス。  
  
7.  型 **(ローカル)** または**期間**(.) のサーバー名。  
  
8.  選択**MDS**の**を選択するか、データベースの名前を入力**フィールドです。 一時ストレージとして MDS データベースを使用する、**あいまいグループ化変換**です。 **あいまいグループ化**変換には、作業のために、変換アルゴリズムが必要な一時 SQL Server テーブルを作成する SQL Server のインスタンスへの接続が必要です。 これを行うには、データベースを作成するか、別の既存のデータベースを使用します。  
  
9. をクリックして**接続のテスト**接続をテストし、をクリックする**OK**メッセージ ボックスにします。  
  
10. **接続マネージャー**ダイアログ ボックスで、をクリックして**OK**です。  
  
11. 選択 **(ローカル)。MDS** (または**localhost です。MDS**) から、**データ接続の一覧** をクリック**OK**です。  
  
12. **あいまいグループ化変換エディター**、いることを確認 **(ローカル)。MDS**または**localhost です。MDS**が選択されて、 **OLE DB 接続マネージャー**です。  
  
13. 切り替えて、**列**タブです。  
  
14. 選択 (チェック ボックス) **SupplierID_Output**の一覧から**使用できる入力列**です。 変換を構成するには、重複部分を識別する際に使用する入力列を選択します。 わかりやすくするために、この手順では SupplierID のみを使用します。  
  
     ![あいまいグループ化変換エディター](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "あいまいグループ化変換エディター")  
  
15. をクリックして**OK**を閉じる、**あいまいグループ化変換エディター**です。  
  
## <a name="next-step"></a>次の手順  
 [タスク 11: 条件分割変換を追加して重複をフィルターする](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  