---
title: 'タスク 10: あいまいグループ化変換を追加して重複を識別する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 48e233c6f2c7a55bf2420825b9fb3064db6e89e1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481250"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>タスク 10: あいまいグループ化変換を追加して重複を識別する
  ここでは、あいまいグループ化変換をデータ フローに追加します。 あいまいグループ化変換は、変換元データの重複を識別する際に役立ちます。 詳細については、「[あいまいグループ化変換](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)」を参照してください。  
  
1.  **SSIS ツールボックス**の [**その他の変換**] にある [**あいまいグループ化**変換] を [**データフロー** ] タブにドラッグアンドドロップします。 [**正しいレコードと修正**されたレコードを結合します。  
  
2.  [**データフロー** ] タブの [**あいまいグループ化**変換] を右クリックし、[**名前の変更**] をクリックします。 「 **Id が一致するグループ仕入先**」と入力し、 **enter**キーを押します。  
  
3.  Blue コネクタを使用して、**適切なレコードと修正**されたレコードを結合し、 **id が一致する仕入先をグループ化**します。  
  
     ![ID が一致するグループ仕入先への接続](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "ID が一致するグループ仕入先への接続")  
  
4.  [ **Id が一致するグループ仕入先] を**ダブルクリックします。  
  
5.  [**あいまいグループ化変換エディター**] で、[ **OLE DB 接続マネージャー** ] ボックスの一覧の [**新規作成**] をクリックして、[ **OLE DB 接続マネージャーの構成**] ダイアログボックスを開きます。  
  
6.  ダイアログボックスで、[**新規**] をクリックして [**接続マネージャー** ] ダイアログボックスを開きます。  
  
7.  サーバー名として「 **(local)** 」または「**ピリオド**(.)」と入力します。  
  
8.  **[データベース名の選択または入力**] フィールドに [ **MDS** ] を選択します。 MDS データベースは、**あいまいグループ化変換**の一時ストレージとして使用されます。 **あいまいグループ化**変換では、SQL Server のインスタンスに接続して、変換アルゴリズムで処理を行うために必要な一時 SQL Server テーブルを作成する必要があります。 これを行うには、データベースを作成するか、別の既存のデータベースを使用します。  
  
9. [**接続テスト**] をクリックして接続をテストし、メッセージボックスの [ **OK** ] をクリックします。  
  
10. [**接続マネージャー** ] ダイアログボックスで、[ **OK]** をクリックします。  
  
11. [ **(ローカル)] を選択します。MDS** (または**localhost。****データ接続の一覧**から MDS) をクリックし、[ **OK]** をクリックします。  
  
12. [**あいまいグループ化変換エディター**] で、[(ローカル)] を確認し**ます。MDS**または**localhost。** **OLE DB 接続マネージャー**に対して MDS が選択されています。  
  
13. [**列**] タブに切り替えます。  
  
14. **使用できる入力列**の一覧から [(チェックボックス) **SupplierID_Output**を選択します。 変換を構成するには、重複部分を識別する際に使用する入力列を選択します。 わかりやすくするために、この手順では SupplierID のみを使用します。  
  
     ![あいまいグループ化変換エディター](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "あいまいグループ化変換エディター")  
  
15. [ **OK]** をクリックして、[**あいまいグループ化変換エディター**] を閉じます。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 11: 条件分割変換を追加して重複をフィルターする](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
