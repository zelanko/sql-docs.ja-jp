---
title: 'タスク 9: 全体結合変換を追加して、正しいレコードと修正されたレコードを結合する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 93b160b6e513ad866126df8b401b82ee1270be84
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489647"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>タスク 9: 全体結合変換を追加して適切なレコードと修正済みレコードを結合する
  ここでは、全体結合変換をデータ フローに追加します。 全体結合変換は、複数の入力を 1 つの出力に結合します。 このシナリオでは、1 つのストリームに適切なレコードと修正済みレコードを結合します。  
  
1.  **SSIS ツールボックス**の [**共通**] セクションから [**データフロー** ] タブに [全体**結合**変換] をドラッグアンドドロップし、[**適切なレコードと修正済みレコードを選択**] の下に配置します。  
  
2.  [**データフロー** ] タブで [全体**結合**変換] を右クリックし、[**名前の変更**] をクリックします。 「**正しいレコードと修正**されたレコードの組み合わせ」と入力し、 **enter**キーを押します。  
  
     ![適切なレコードと修正済みレコードの結合](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "適切なレコードと修正済みレコードの結合")  
  
3.  Blue コネクタを使用して、[**データフロー** ] タブで正しいレコードと修正された**レコードを結合**するには、 **[適切なレコードを選択**する] を選択します。 [**入力出力の選択**] ダイアログボックスが表示されます。  
  
4.  [**入力出力**] ダイアログボックスで、[**出力**] の [**適切**] を選択し、[ **OK**] をクリックします。  
  
     ![[入出力の選択] ダイアログ ボックス](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "[入出力の選択] ダイアログ ボックス")  
  
5.  コネクタの最後にあるドットを左にドラッグアンドドロップして、**コネクタを左に移動**します。  
  
     ![適切なレコードと修正済みレコードを結合するために適切なレコードを接続](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "適切なレコードと修正済みレコードを結合するために適切なレコードを接続")  
  
6.  [**正しいレコードの選択**] を選択すると、別の青いコネクタが表示されます。 青いコネクタをドラッグして **、正しいレコードと修正**されたレコードを結合します。  
  
     ![正しい結合と修正された接続を修正しました](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "正しい結合と修正された接続を修正しました")  
  
7.  この**コネクタ**のタイトルは "**修正**済み" にする必要があります。 **正しい**条件は2つ**だけであり、1**つの条件が既に使用されているため、[**入力出力の選択**] ダイアログボックスは表示されません。 コネクタが重複する場合は、左側のコネクタを右側のコネクタに、または右側のコネクタを左側のコネクタにドラッグ アンド ドロップします。  
  
## <a name="next-step"></a>次の手順  
 [タスク 10: あいまいグループ化変換を追加して重複を識別する](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
