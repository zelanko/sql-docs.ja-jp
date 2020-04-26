---
title: '作業 12: 派生列変換を追加して MDS で必要な列を追加する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 18789f5bc1d97e1531588d50e2430829f95912b8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65485239"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>タスク 12: 派生列変換を追加して MDS で必要な列を追加する
  ここでは、派生列変換をデータ フローに追加します。 この変換に渡されるレコードには、 **Importtype**と**batchtag**という2つの派生列を追加します。 MDS のステージング テーブルにデータをアップロードする前に、これらの列を追加する必要があります。 これら 2 つは、MDS のステージング テーブルに必要な列です。 詳細については、「[リーフメンバーステージングテーブル](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。  
  
1.  **SSIS ツールボックス**の [**共通**] セクションから [**データフロー** ] タブに、**派生列変換**をドラッグアンドドロップします。  
  
2.  [**データフロー** ] タブで [**派生列**変換] を右クリックし、[**名前の変更**] をクリックします。 「 **MDS で必要な列**を追加 **」** と入力し、enter キーを押します。  
  
3.  接続**フィルター**を使用して、blue コネクタを使用して**MDS で必要な列を追加**します。 [**入力出力の選択**] ダイアログボックスが表示されます。  
  
4.  [**入力出力の選択**] ダイアログボックスで、[**一意のレコード**] を選択し、[ **OK**] をクリックします。  
  
     ![[入出力の選択] ダイアログ ボックス](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "[入出力の選択] ダイアログ ボックス")  
  
5.  メニューバーの [ **SSIS** ] をクリックし、[**変数**] をクリックします。  
  
6.  [**変数**] ウィンドウで、ツールバーの [**変数の追加**] ボタンをクリックします。  
  
     ![[SSIS 変数] ウィンドウ](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "[SSIS 変数] ウィンドウ")  
  
7.  [**名前**] に「 **importtype** 」と入力し、**値**に「 **2** 」と入力します。 MDS のエンティティに新しいメンバーを追加するため、値には 2 を指定します。 このパラメーターの詳細については、「[リーフメンバーステージングテーブル](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。  
  
8.  [**変数の追加**] ツールバーボタンをもう一度クリックします。  
  
9. [**名前**] に「 **batchtag** 」と入力し **、データ型**として [**文字列**] を選択し、[**値**] に「 **eimbatch** 」と入力します。 **Batchtag**は、MDS に送信するバッチの一意の名前にすぎません。  
  
10. [**データフロー** ] タブで、[ **MDS に必要な列の追加**] をダブルクリックします。  
  
11. [**派生列変換エディター** ] ダイアログボックスの**下部ペインにあるリストボックス**で、**派生列名**として「 **importtype** 」と入力します。  
  
12. 左上のペインで [**変数とパラメーター** ] を展開し、 **User:: Importtype**を [**式**] 列にドラッグアンドドロップします。  
  
     ![派生列変換エディター](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "派生列変換エディター")  
  
13. **派生列の名前**として、次の行に「 **batchtag** 」と入力します。  
  
14. **ユーザー:: BatchTag**を**変数およびパラメーター**から [**式**] 列にドラッグアンドドロップします。  
  
15. [ **OK** ] をクリックして、[**派生列変換**] ダイアログボックスを閉じます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 13: データを書き込む OLE DB 変換先を MDS ステージング テーブルに追加する](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
