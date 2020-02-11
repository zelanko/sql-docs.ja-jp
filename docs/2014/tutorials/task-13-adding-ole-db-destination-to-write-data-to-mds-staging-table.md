---
title: 'タスク 13: MDS ステージングテーブルにデータを書き込むための OLE DB 変換先の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7c5fc9d863c23c1cae08c04fef7810aeda446762
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65476992"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>タスク 13: データを書き込む OLE DB 変換先を MDS ステージング テーブルに追加する
  すべてのレコードに**Importtype**と**batchtag**の値を追加したので、ステージング用に MDS に送信する準備ができました。 このタスクでは、OLE DB 変換先を使用して、データを**stg. supplier_Leaf**ステージングテーブルに書き込みます。  
  
1.  **SSIS ツールボックス**の [**その他の変換**先] セクションから [**データフロー** ] タブに [**変換先**] を OLE DB ドラッグし、[ **MDS で必要な列を追加**] の下にドロップします。  
  
2.  [**データフロー** ] タブの [ **OLE DB Destination** ] を右クリックし、[**名前の変更**] をクリックします。 「 **MDS ステージングテーブルにサプライヤーデータを書き込む**」と入力し、 **enter**キーを押します。  
  
3.  Blue コネクタを使用して**Mds ステージングテーブルにサプライヤーデータを書き込む**には、Mds が必要とする**Add 列**を接続します。  
  
4.  [**データフロー** ] タブの [ **MDS ステージングテーブルにサプライヤーデータを書き込む] を**ダブルクリックします。  
  
5.  [ **OLE DB 変換先エディター** ] ダイアログボックスで、[(ローカル)] が選択されていることを確認し**ます。MDS** (または**localhost。**[ **OLE DB 接続マネージャー** ] フィールドに対して [MDS] が選択されています。  
  
6.  [Stg] を選択し**ます。** テーブル**またはビューの名前**の一覧からテーブルを Supplier_Leaf します。  
  
     ![OLEDB 変換先エディター](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB 変換先エディター")  
  
7.  左側のメニューの [**マッピング**] をクリックして、[**マッピング**] ページに切り替えます。  
  
8.  次の表に示すように、**入力**列と**変換先**列をマップします。  
  
     ![OLEDB 変換先エディター - マッピング](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB 変換先エディター - マッピング")  
  
9. **_Status**または **_Source**列ではなく、入力列に **_Output**列を使用していることを確認します。 **_Output**列には、DQS クレンジングの出力値が含まれています。  
  
10. [ **OK** ] をクリックして [ **OLE DB 変換先エディター** ] ダイアログボックスを閉じます。  
  
11. データ フローは次の図のようになります。  
  
     ![完了したデータ フロー](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "完了したデータ フロー")  
  
## <a name="next-step"></a>次のステップ  
 [タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアド プロシージャを実行する](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
