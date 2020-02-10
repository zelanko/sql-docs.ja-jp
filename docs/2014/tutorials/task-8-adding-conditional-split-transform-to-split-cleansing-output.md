---
title: 'タスク 8: 条件分割変換を追加してクレンジング出力を分割する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d5a55f0694094e6fe88a42946bcff34f420210f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489672"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>タスク 8: 条件分割変換を追加してクレンジング出力を分割する
  この変換では、データ フローに条件分割変換を追加します。 条件分割変換では、データの内容に応じて別の出力に行をルートできます。 このチュートリアルでは、DQS クレンジング変換の [**レコードの状態**] 出力列を使用します。 このチュートリアルでは、適切なレコードまたは修正されたレコードのみを MDS サーバーにアップロードします。 そのため、レコードの**状態**が**適切**であるか、**修正**されたかを確認し、レコードを MDS にアップロードする前にレコードを結合します。  
  
1.  **SSIS ツールボックス**の [**共通**] セクションから [**仕入先データのクレンジング**] の [**データフロー** ] タブに**条件分割変換**をドラッグアンドドロップします。  
  
2.  [**条件分割**] を右クリックし、[**名前の変更**] をクリックします。 「**正しいレコードと修正**されたレコードを選択する **」と入力**し、enter キーを押します。  
  
3.  Blue コネクタを使用して、 **Supplier データをクレンジング**し、**正しいレコードと修正**されたレコードを選択します。  
  
     ![仕入先データのクレンジング-適切な & 修正 > 選択](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "仕入先データのクレンジング -> 適切なデータと修正済みのデータの選択")  
  
4.  [**データフロー** ] タブで、[**適切なレコードを選択して修正し**ました] をダブルクリックします。  
  
5.  画面の下部にある**既定の出力名**を [**修正**] に変更します。  
  
6.  左上のペインで [**列** **]** を展開します。  
  
     ![条件分割変換エディター](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "条件分割変換エディター")  
  
7.  [レコードの**状態**] を [**条件**] 列にドラッグアンドドロップします。  
  
8.  [**条件**] 列の **[レコードの状態]** の横に「 **= = "修正済み"」** と入力します。  
  
9. [**出力名] 列**の**ケース 1**をクリックし、名前を "**修正**済み" に変更します。  
  
10. [ **OK** ] をクリックして [**条件分割変換エディター** ] ダイアログボックスを閉じます。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 9: 全体結合変換を追加して適切なレコードと修正済みレコードを結合する](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
