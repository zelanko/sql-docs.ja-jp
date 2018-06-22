---
title: 'タスク 13: MDS ステージング テーブルにデータを書き込む OLE DB 変換先を追加する |Microsoft ドキュメント'
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
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 75e77579857852e607b783534d149367a946318f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074491"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>タスク 13: データを書き込む OLE DB 変換先を MDS ステージング テーブルに追加する
  これで追加した**ImportType**と**BatchTag**を経由して送信を MDS にステージングする準備ができたら、すべてのレコードに値。 このタスクでデータの書き込みを OLE DB 変換先を使用して**stg.supplier_Leaf**ステージング テーブル。  
  
1.  ドラッグ**OLE DB 変換先**から**その他の変換先**」の「、 **SSIS ツールボックス**を**データ フロー**タブし、下にドロップ**MDS で必要な列を追加**です。  
  
2.  右クリック**OLE DB 変換先**で、**データ フロー**タブをクリックし、をクリックして**の名前を変更**です。 型**MDS ステージング テーブルにサプライヤー データを書き込む**とキーを押します**ENTER**です。  
  
3.  接続、 **Add Columns Required by MDS**に**MDS ステージング テーブルにサプライヤー データを書き込む**青色コネクタを使用します。  
  
4.  ダブルクリックして**MDS ステージング テーブルにサプライヤー データを書き込む**で、**データ フロー**タブです。  
  
5.  **OLE DB 変換先エディター**  ダイアログ ボックスで、ことを確認して **(ローカル)。MDS** (または**localhost です。MDS**) が選択されて、 **OLE DB 接続マネージャー**フィールドです。  
  
6.  選択**stg.Supplier_Leaf**の一覧からテーブル **、テーブルまたはビューの名前**です。  
  
     ![OLEDB 変換先エディター](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB 変換先エディター")  
  
7.  切り替えて、**マッピング**をクリックしてページ**マッピング**左側のメニュー上。  
  
8.  マップ**入力**と**先**列次の表に示すようにします。  
  
     ![OLEDB 変換先エディター - マッピング](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB 変換先エディター - マッピング")  
  
9. 使用していることを確認 **_Output**入力列の列されません、 **_Status**または **_Source**列です。 **_Output** DQS クレンジングの出力値を含む列。  
  
10. をクリックして**OK**を閉じる、 **OLE DB 変換先エディター**  ダイアログ ボックス。  
  
11. データ フローは次の図のようになります。  
  
     ![データ フローを完了した](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "データ フローの完了")  
  
## <a name="next-step"></a>次の手順  
 [タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアド プロシージャを実行する](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  