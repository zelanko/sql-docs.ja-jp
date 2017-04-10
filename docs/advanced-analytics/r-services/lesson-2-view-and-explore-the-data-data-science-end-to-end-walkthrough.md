---
title: "レッスン 2: データの表示と探査 (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: 32
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 26
---
# レッスン 2: データの表示と探査 (データ サイエンスのエンド ツー エンド チュートリアル)
データ探査は、データのモデリングの重要な部分であり、解析およびデータの視覚化で使用するデータ オブジェクトを確認する作業を伴います。 このレッスンでは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] と R 関数の両方を使用して、データ オブジェクトを探索し、プロットを生成します。  
  
次いで、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] でインストールされるパッケージに含まれる新しい関数を使用して、データを視覚化するプロットを作成します。  
  
> [!TIP]  
> R をマスターできましたか?  
>   
> これで、すべてのデータをダウンロードし、環境が整いました。RStudio または他のあらゆる環境で完全な R スクリプトを実行して、ご自身で機能を探索してみてください。 RSQL_Walkthrough.R ファイルを開き、デモとして個々の行を強調表示して実行するか、スクリプト全体を実行します。  
>   
> RevoScaleR 関数に関するその他の説明および、R で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを使用するときのヒントについては、チュートリアルをお続けください。 完全に同じスクリプトを使用しています。  
  
## <a name="verify-downloaded-data-using-sql"></a>SQL を使用してダウンロードしたデータを確認する  
まず、少し時間をかけて、データが正しく読み込まれたことを確認します。  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。  
  
    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続して、それを表示するには、次などのさまざまなツールを使用できます。  
  
    -   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]    
    -   Visual Studio のサーバー エクスプローラー  
  
2.  作成したデータベースを展開します。 次の図は、**サーバー エクスプローラー**の新しいデータベース、テーブル、および関数を示しています。  
  
    ![new database objects created by script](../../advanced-analytics/r-services/media/rsql-e2e-ssms-newobjects.PNG "new database objects created by script")  
  
3.  データに単純なクエリを実行することもできます。 たとえば、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でテーブルを右クリックして、 **[上位 1000 行を選択]** を選択し、次のクエリを生成して実行します。  
  
    ```  
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]  
    ```  
    テーブル内のデータが表示されない場合は、前のセクションの「[トラブルシューティング](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)」セクションを参照してください。
      
4.  データのスキーマとデータ型を確認するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でシステムの管理ビューを使用します。  
  
    ```  
    SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT  
    FROM [TaxiSample].INFORMATION_SCHEMA.COLUMNS  
    WHERE TABLE_NAME = N'nyctaxi_sample';  
    ```  
  
    > [!TIP]  
    > データ テーブルの作成方法の詳細を確認するには、スクリプト `create-db-tb-upload-data.sql`を確認することも可能です。  
  
### <a name="generate-summaries-using-sql"></a>SQL を使用したサマリーの生成  
R と共に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用すると、セットベースの計算が非常に速くできるという強みがあります。  このチュートリアル用にテーブルを作成したコードは、より早く計算を行うために、[列ストア インデックス](../Topic/Columnstore%20Indexes%20Guide.md)にも適用されます。   
  
```  
SELECT DISTINCT [passenger_count]  
    , ROUND (SUM ([fare_amount]),0) as TotalFares   
    , ROUND (AVG ([fare_amount]),0) as AvgFares  
FROM [dbo].[nyctaxi_sample]  
GROUP BY [passenger_count]   
ORDER BY  AvgFares desc  
```  

次の手順では、SQL Server のデータを使用して、いくつかのより高度なサマリーとプロットを生成するために R を使用します。  
  
## <a name="next-steps"></a>次の手順  
[R を使用したデータの表示と集計 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/view-and-summarize-data-using-r-data-science-end-to-end-walkthrough.md)  
  
[R を使用したグラフとプロットの作成 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>前のレッスン  
[レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>参照  
[列ストア インデックス ガイド](../Topic/Columnstore%20Indexes%20Guide.md)  
  
  
  
