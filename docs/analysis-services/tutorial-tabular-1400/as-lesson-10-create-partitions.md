---
title: 'Analysis Services のチュートリアル レッスン 10: パーティションの作成 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: 8dc8e91271451d3f24df95846f32af8dbd9ca346
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="create-partitions"></a>パーティションの作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、他のパーティションに依存しないより小さな論理部分を処理するのには、FactInternetSales テーブルを分割する (更新) パーティションが作成されます。 モデルに含めるすべてのテーブルの使用には既定では 1 つのパーティションは、すべてのテーブルの列と行が含まれています。 FactInternetSales テーブルの年です。 別のデータを分割します。1 つの各パーティション テーブルの 5 年です。 これにより、各パーティションを個別に処理できるようにします。 詳細については、次を参照してください。[パーティション](../tabular-models/partitions-ssas-tabular.md)です。 
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 9: 階層の作成](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)です。  
  
## <a name="create-partitions"></a>パーティションの作成  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>FactInternetSales テーブルでパーティションを作成するには  
  
1.  表形式モデル エクスプ ローラーで、展開**テーブル**、し、右クリックし、 **FactInternetSales** > **パーティション**です。  
  
2.  パーティション マネージャーで、をクリックして**コピー**からに名前を変更および**FactInternetSales2010**です。
  
    2010 年の特定の期間内の行だけを含めるパーティションの目的であるために、クエリ式を変更する必要があります。
  
4.  をクリックして**デザイン**クエリ エディターを開き、をクリックする、 **FactInternetSales2010**クエリ。

5.  プレビューで下向きの矢印をクリックして、 **OrderDate**列見出しをクリックして**日付/時刻フィルター** > **間**です。

    ![as-lesson10-query-editor](../tutorial-tabular-1400/media/as-lesson10-query-editor.png)

6.  行のフィルター選択 ダイアログ ボックスで**行を表示: OrderDate**のままにして**後か等しい**、し、日 フィールドで、次のように入力します。 **2010 年 1 月 1 日**です。 ままにして、**と**選択すると、演算子を選択し、**する前に**、し、[日] フィールドで、次のように入力します。 **2011 年 1 月 1 日**、順にクリック **[ok]** です。

    ![as-lesson10-filter-rows](../tutorial-tabular-1400/media/as-lesson10-filter-rows.png)
    
    通知クエリ エディターで、適用の手順では、フィルター選択された行をという名前の別の手順を表示します。 このフィルターでは、2010年からの注文日のみを選択します。

8.  **[インポート]** をクリックします。

    パーティション マネージャーは、クエリ式は、追加の行のフィルター句に注意してください。

    ![as-lesson10-query](../tutorial-tabular-1400/media/as-lesson10-query.png)
  
    このステートメントでは、このパーティションは、2010 年のフィルター選択された行の句で指定したとおりに、OrderDate がある場合、行のデータのみを含める必要がありますを指定します。  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>2011 年用のパーティションを作成するには  
  
1.  パーティションの一覧で、 **FactInternetSales2010**パーティションを作成して、をクリックして**コピー**です。  パーティション名に変更**FactInternetSales2011**です。 

    クエリ エディターを使用して、フィルター選択された行の新しい句を作成する必要はありません。 2010 のクエリのコピーを作成するために行う必要は 2011年のクエリでわずかな変更を行ったです。
  
2.  **クエリ式**、するには、2011 年の行だけを含める、年を含む行のフィルター句で置き換えるには、このパーティションの順序で**2011**と**2012**をそれぞれのように。  
  
    ```  
    let
        Source = #"SQL/localhost;AdventureWorksDW2014",
        dbo_FactInternetSales = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
        #"Removed Columns" = Table.RemoveColumns(dbo_FactInternetSales,{"OrderDateKey", "DueDateKey", "ShipDateKey"}),
        #"Filtered Rows" = Table.SelectRows(#"Removed Columns", each [OrderDate] >= #datetime(2011, 1, 1, 0, 0, 0) and [OrderDate] < #datetime(2012, 1, 1, 0, 0, 0))
    in
        #"Filtered Rows"
   
    ```  
  
#### <a name="to-create-partitions-for-2012-2013-and-2014"></a>2012、2013、および 2014 のパーティションを作成します。  
  
- 2012、2013、および 2014 年にその年の行のみを含める行のフィルター選択句の年を変更するパーティションを作成する前の手順に従います。 
  

## <a name="delete-the-factinternetsales-partition"></a>FactInternetSales のパーティションを削除します。

これで、各年のパーティションがある、パーティションを削除する、FactInternetSales です。パーティションを処理するときに、すべてのプロセスを選択するときに、重複を防止します。

#### <a name="to-delete-the-factinternetsales-partition"></a>FactInternetSales パーティションを削除するには

-  クリックして、 **FactInternetSales** 、パーティション分割し、をクリックして**削除**です。



## <a name="process-partitions"></a>パーティションの処理  

パーティション マネージャーで、確認、**最後処理**列の新しい各パーティションを作成するためにこれらのパーティションが処理されていない表示します。 パーティションを作成するときに、それらのパーティションでデータを更新するパーティションの処理またはテーブルの処理操作を実行する必要があります。  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>FactInternetSales パーティションを処理するには  
  
1.  をクリックして**OK**パーティション マネージャーを閉じます。  
  
2.  クリックして、 **FactInternetSales**テーブルをクリック、**モデル**メニュー >**プロセス** > **パーティションの処理**です。  
  
3.  パーティションの処理 ダイアログ ボックスで、次を確認してください。**モード**に設定されている**既定の処理**です。  
  
4.  作成した 5 つのパーティションのそれぞれについて、 **[処理]** 列のチェック ボックスをオンにし、 **[OK]** をクリックします。  

    ![として-lesson10--パーティションの処理](../tutorial-tabular-1400/media/as-lesson10-process-partitions.png)
  
    権限借用の資格情報の入力を求められたら、Windows ユーザー名とレッスン 2 で指定したパスワードを入力します。  
  
    **[データ処理]** ダイアログ ボックスが表示され、各パーティションのプロセスの詳細が表示されます。 転送される行数はパーティションごとに異なります。 各パーティションには、SQL ステートメントの WHERE 句で指定された年の行だけが含まれています。 処理が完了したら、[データ処理] ダイアログ ボックスをクリックします。  
  
    ![as-lesson10-process-complete](../tutorial-tabular-1400/media/as-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>次の操作

次のレッスンに移動:[レッスン 11: ロールの作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)です。 
