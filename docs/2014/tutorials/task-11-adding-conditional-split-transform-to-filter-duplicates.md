---
title: 'タスク 11: 条件分割変換を追加して重複をフィルター処理する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 71b050e49440764d355d4658607600c135741f50
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65476752"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>タスク 11: 条件分割変換を追加して重複をフィルターする
  ここでは、データ フローに条件分割変換を追加します。 この変換は、受信するレコード セットから重複をフィルターする際に役立ちます。 あいまいグループ化変換では、一致として検出したレコードがグループ化され、ピボット レコードとしてレコードのいずれかが選択されます。 グループ内のすべてのレコードは、同じ _key_out 値を持ちます。 グループ内のピボット レコードは _key_out 値と同じ _key_in 値を持ちます。 グループ内のその他のレコードでは、_key_in と _key_out の値が異なります。 そのため、条件の _key_in==_key_out を使用してフィルターすると、グループ内のピボット行のみが取得されます。  
  
1.  **SSIS ツールボックス**の [**共通**] セクションから [**データフロー** ] タブに**条件分割**変換をドラッグアンドドロップします。  
  
2.  [**データフロー** ] タブの [**条件分割変換**] を右クリックし、[**名前の変更**] をクリックします。 「**フィルターの重複**を入力し、 **enter**キーを押します。  
  
3.  **一致する id を持つグループサプライヤー**を接続して、**重複をフィルター処理**します。  
  
4.  [重複の**フィルター** ] をダブルクリックして、[**条件分割変換エディター** ] ダイアログボックスを開きます。  
  
5.  左上のペインで [**列**] を展開します。  
  
6.  **_Key_in**を [**条件**] 列にドラッグアンドドロップします。  
  
7.  [ **_Key_in** ] の横に「= = (等しい)」と入力し、 **_key_out**をドラッグアンドドロップします。  
  
8.  [**出力名**] 列の [**ケース 1** ] をクリックし、「**一意のレコード**」と入力して、 **enter**キーを押します。  
  
     ![条件分割変換エディター](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "条件分割変換エディター")  
  
9. [ **OK** ] をクリックして [**条件分割変換エディター** ] ダイアログボックスを閉じます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 12: 派生列変換を追加して MDS で必要な列を追加する](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
