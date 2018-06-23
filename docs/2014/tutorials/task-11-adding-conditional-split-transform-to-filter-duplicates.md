---
title: 'タスク 11: 重複をフィルターする変換の分割条件を追加する |Microsoft ドキュメント'
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
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7f61fa706659a6f71b2c69f18bcf7b694993ed00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085117"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>タスク 11: 条件分割変換を追加して重複をフィルターする
  ここでは、データ フローに条件分割変換を追加します。 この変換は、受信するレコード セットから重複をフィルターする際に役立ちます。 あいまいグループ化変換では、一致として検出したレコードがグループ化され、ピボット レコードとしてレコードのいずれかが選択されます。 グループ内のすべてのレコードは、同じ _key_out 値を持ちます。 グループ内のピボット レコードは _key_out 値と同じ _key_in 値を持ちます。 グループ内のその他のレコードでは、_key_in と _key_out の値が異なります。 そのため、条件の _key_in==_key_out を使用してフィルターすると、グループ内のピボット行のみが取得されます。  
  
1.  ドラッグ アンド ドロップ**条件分割**から変換**共通**」の「、 **SSIS ツールボックス**を**データ フロー**タブです。  
  
2.  右クリック**条件分割変換**で、**データ フロー**タブをクリックし、をクリックして**の名前を変更**です。 型**Filter Duplicates**とキーを押します**ENTER**です。  
  
3.  接続**Id と一致する仕入先をグループ化**に**重複をフィルター**です。  
  
4.  ダブルクリックして**Filter Duplicates**を起動する、**条件分割変換エディター**  ダイアログ ボックス。  
  
5.  展開**列**左ペインでします。  
  
6.  ドラッグ アンド ドロップ **_key_in**を**条件**列です。  
  
7.  型 (に等しい) を横に = = **_key_in**およびドラッグ アンド ドロップ **_key_out**です。  
  
8.  をクリックして**ケース 1**で、**出力名**列に「**一意のレコード**、とキーを押します**ENTER**です。  
  
     ![条件分割変換エディター](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "条件分割変換エディター")  
  
9. をクリックして**OK**を閉じる、**条件分割変換エディター**  ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 12: 派生列変換を追加して MDS で必要な列を追加する](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  