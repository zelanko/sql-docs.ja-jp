---
title: Analysis Services チュートリアル レッスン 10:パーティションの作成 |Microsoft Docs
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: f7b6e5bfd4c533028758f553e5d8c9b2ca21e6f2
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401145"
---
# <a name="create-partitions"></a>パーティションの作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、他のパーティションの独立したパーティションをより小さな論理部分を処理できる、FactInternetSales テーブルに分割 (更新) が作成します。 モデルに含めるすべてのテーブルの使用には既定では 1 つのパーティションは、すべてのテーブルの列と行が含まれています。 FactInternetSales テーブルで年間でデータを分割します。各テーブルの 5 年間の 1 つのパーティション。 これにより、各パーティションを個別に処理できるようにします。 詳細については、「 [[パーティション]](../tabular-models/partitions-ssas-tabular.md)」を参照してください。 
  
このレッスンを完了するまでに時間を推定するには。**15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 9:階層を作成する](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)します。  
  
## <a name="create-partitions"></a>パーティションの作成  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>FactInternetSales テーブルにパーティションを作成するには  
  
1.  表形式モデル エクスプ ローラーで**テーブル**、右クリックし、 **FactInternetSales** > **パーティション**します。  
  
2.  パーティション マネージャーで、**コピー**、名前を変更し、 **FactInternetSales2010**します。
  
    パーティションは、2010 年の特定の期間内でこれらの行のみを含める必要があるために、クエリ式を変更する必要があります。
  
4.  クリックして**デザイン**クエリ エディターを開き、クリックして、 **FactInternetSales2010**クエリ。

5.  プレビューでは、下矢印をクリックして、 **OrderDate**列見出しをクリックして**日付/時刻フィルター** > **間**します。

    ![as-lesson10-query-editor](../tutorial-tabular-1400/media/as-lesson10-query-editor.png)

6.  行のフィルター選択 ダイアログ ボックスで**行を表示します。OrderDate**、まま**は次の値以降**、し、日付フィールドに、次のように入力します。 **2010 年 1 月 1 日**します。 ままに、**と**選択すると、演算子を選択し、**する前に**、し、日付フィールドに、次のように入力します。 **2011 年 1 月 1 日**、順にクリックします **[ok]** します。

    ![as-lesson10-filter-rows](../tutorial-tabular-1400/media/as-lesson10-filter-rows.png)
    
    通知クエリ エディターの APPLIED STEPS に Filtered Rows という名前の別の手順を表示します。 このフィルターでは、2010年からの注文日のみを選択します。

8.  **[インポート]** をクリックします。

    Partition Manager では、これで、クエリ式に Filtered Rows 句に注意してください。

    ![as-lesson10-query](../tutorial-tabular-1400/media/as-lesson10-query.png)
  
    このステートメントでは、このパーティションは、OrderDate が 2010年年度 filtered rows 句で指定されているが、行のデータのみを含める必要がありますを指定します。  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>2011 年用のパーティションを作成するには  
  
1.  パーティション一覧で、 **FactInternetSales2010**クリックして、作成したパーティション分割**コピー**します。  パーティション名を変更して**FactInternetSales2011**します。 

    クエリ エディターを使用して、新しい filtered rows 句を作成する必要はありません。 2010 のクエリのコピーを作成しているために、2011 年のクエリにわずかな変更を加えるは行う必要があるすべて。
  
2.  **クエリ式**、2011 年の行だけを含める、Filtered Rows 句の年度の置換には、このパーティションの順序で**2011**と**2012**、それぞれのように。  
  
    ```  
    let
        Source = #"SQL/localhost;AdventureWorksDW2014",
        dbo_FactInternetSales = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
        #"Removed Columns" = Table.RemoveColumns(dbo_FactInternetSales,{"OrderDateKey", "DueDateKey", "ShipDateKey"}),
        #"Filtered Rows" = Table.SelectRows(#"Removed Columns", each [OrderDate] >= #datetime(2011, 1, 1, 0, 0, 0) and [OrderDate] < #datetime(2012, 1, 1, 0, 0, 0))
    in
        #"Filtered Rows"
   
    ```  
  
#### <a name="to-create-partitions-for-2012-2013-and-2014"></a>2012、2013 年および 2014 用のパーティションを作成します。  
  
- 2012、2013、および 2014 では、その年の行のみを含めるに Filtered Rows 句の年度を変更するパーティションを作成する前の手順に従います。 
  

## <a name="delete-the-factinternetsales-partition"></a>FactInternetSales パーティションを削除します。

FactInternetSales パーティションを削除するには各年のパーティションがあることのようになりましたパーティションを処理するときに、すべてのプロセスを選択するときの重複を防ぐ。

#### <a name="to-delete-the-factinternetsales-partition"></a>FactInternetSales パーティションを削除するには

-  をクリックして、 **FactInternetSales**をパーティション分割し、**削除**します。



## <a name="process-partitions"></a>パーティションの処理  

Partition manager での**Last Processed**列の新しい各パーティションを作成するためにこれらのパーティションが処理されていません表示します。 パーティションを作成するときに、それらのパーティションでデータを更新するプロセスのパーティションまたはテーブルの処理操作を実行する必要があります。  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>FactInternetSales パーティションを処理するには  
  
1.  クリックして**OK**パーティション マネージャーを閉じます。  
  
2.  をクリックして、 **FactInternetSales**テーブルををクリックし、**モデル**メニュー >**プロセス** > **パーティションの処理**します。  
  
3.  パーティションの処理 ダイアログ ボックスで、次のように確認します。**モード**に設定されている**既定の処理**します。  
  
4.  作成した 5 つのパーティションのそれぞれについて、 **[処理]** 列のチェック ボックスをオンにし、 **[OK]** をクリックします。  

    ![として-lesson10--パーティションの処理](../tutorial-tabular-1400/media/as-lesson10-process-partitions.png)
  
    権限借用の資格情報を求められたらは、Windows ユーザー名とレッスン 2 で指定したパスワードを入力します。  
  
    **[データ処理]** ダイアログ ボックスが表示され、各パーティションのプロセスの詳細が表示されます。 転送される行数はパーティションごとに異なります。 各パーティションには、SQL ステートメントの WHERE 句で指定された年の行だけが含まれています。 処理が完了したら、[データ処理] ダイアログ ボックスをクリックします。  
  
    ![as-lesson10-process-complete](../tutorial-tabular-1400/media/as-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>次の操作

次のレッスンに移動します。[レッスン 11:ロールを作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)です。 
