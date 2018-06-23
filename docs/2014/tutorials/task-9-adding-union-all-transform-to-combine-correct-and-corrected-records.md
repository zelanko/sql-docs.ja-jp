---
title: 'タスク 9: 全体結合を追加するレコードと修正のレコードを結合する変換 |Microsoft ドキュメント'
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
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: df61e9219c179ab934a33a78f13499351047bf4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177631"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>タスク 9: 全体結合変換を追加して適切なレコードと修正済みレコードを結合する
  ここでは、全体結合変換をデータ フローに追加します。 全体結合変換は、複数の入力を 1 つの出力に結合します。 このシナリオでは、1 つのストリームに適切なレコードと修正済みレコードを結合します。  
  
1.  ドラッグ アンド ドロップ**共用体すべて**から変換**共通**のセクション、 **SSIS ツールボックス**を**データ フロー**タブし、の下に置きます**レコードと修正のレコードを選択**です。  
  
2.  右クリック**共用体すべて**変換を実行、**データ フロー**タブをクリックし、をクリックして**の名前を変更**です。 型**Combine Correct and Corrected Records**、キーを押します**ENTER**です。  
  
     ![レコードと修正 Reocrds を組み合わせる](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "レコードと修正 Reocrds の結合")  
  
3.  接続**Pick Correct and Corrected Records**に**Combine Correct and Corrected Records**で、**データ フロー**青色コネクタを使用してタブです。 表示されるはずの**入出力の選択** ダイアログ ボックス。  
  
4.  **入出力**ダイアログ ボックスで、**修正**の**出力** をクリック**OK**です。  
  
     ![出力の選択 ダイアログ ボックスの入力](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "出力の選択 ダイアログ ボックスの入力")  
  
5.  というタイトルのコネクタ**修正**ドラッグ アンド ドロップ左へのコネクタの末尾にドットを左にします。  
  
     ![結合レコードと修正に正しい接続](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "結合レコードと修正に正しい接続")  
  
6.  選択した場合**Pick Correct and Corrected Records**変換、別の青色コネクタが表示されます。 その青色コネクタをドラッグして**Combine Correct and Corrected Records**です。  
  
     ![結合レコードと修正に修正された接続](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "結合レコードと修正に修正された接続")  
  
7.  これは、**コネクタ**タイトルを付ける必要があります**修正済み**です。 2 つの条件があるため**修正**と**修正済み**、1 つの条件が既に使用されていると、**入出力の選択** ダイアログ ボックスではこの時刻は表示されません。 コネクタが重複する場合は、左側のコネクタを右側のコネクタに、または右側のコネクタを左側のコネクタにドラッグ アンド ドロップします。  
  
## <a name="next-step"></a>次の手順  
 [タスク 10: あいまいグループ化変換を追加して重複を識別する](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  