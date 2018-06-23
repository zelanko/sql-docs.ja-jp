---
title: 'タスク 8: クレンジングの出力を分割する変換の分割条件を追加する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6dc3b98e03a7940841bc97012c1a4e4220bb970d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164484"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>タスク 8: 条件分割変換を追加してクレンジング出力を分割する
  この変換では、データ フローに条件分割変換を追加します。 条件分割変換では、データの内容に応じて別の出力に行をルートできます。 このチュートリアルを使用して、**レコードの状態**DQS クレンジング変換からの出力列です。 このチュートリアルでは、適切なレコードまたは修正されたレコードのみを MDS サーバーにアップロードします。 場合を確認するため、**レコードの状態**は**修正**または**修正済み**と、レコードを MDS にアップロードする前に、レコードを結合します。  
  
1.  ドラッグ アンド ドロップ**条件分割変換**から**共通**」の「、 **SSIS ツールボックス**を**データ フロー** ] タブの [ **仕入先データをクレンジング**です。  
  
2.  右クリック**条件分割**、 をクリック**の名前を変更**です。 型**Pick Correct and Corrected Records**とキーを押します**ENTER**です。  
  
3.  接続**Cleanse Supplier Data**と**Pick Correct and Corrected Records**青色コネクタを使用します。  
  
     ![Cleanse Supplier データが正しいと修正済みの選択]-> [](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier データが正しいと修正済みの選択 ->")  
  
4.  ダブルクリックして**Pick Correct and Corrected Records**で、**データ フロー**タブです。  
  
5.  変更、**既定の出力名**画面の下部にある**修正**です。  
  
6.  展開**列**で、**左上ペイン**です。  
  
     ![条件分割変換エディター](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "条件分割変換エディター")  
  
7.  ドラッグ アンド ドロップ**レコードの状態**を**条件**列です。  
  
8.  型 **「修正済み」= =**  の横に **[レコードの状態]** の**条件**列です。  
  
9. をクリックして**ケース 1**で、**出力名 列**、名前を変更し、**修正済み**です。  
  
10. をクリックして**OK**を閉じる、**条件分割変換エディター**  ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 9: 全体結合変換を追加して適切なレコードと修正済みレコードを結合する](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  