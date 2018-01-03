---
title: "表示し、SQL (チュートリアル) を使用してデータを探索 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: "33"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6bf3d5ea1e1018a727f94bc2ae2682fc8f7e5e3
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="view-and-explore-the-data-using-sql-walkthrough"></a>表示して、SQL (チュートリアル) を使用してデータの探索

データ探査は、データのモデリングの重要な部分であり、解析およびデータの視覚化で使用するデータ オブジェクトを確認する作業を伴います。 このレッスンでの データ オブジェクトを調査して両方を使用して、プロットを生成した[!INCLUDE[tsql](../../includes/tsql-md.md)]と R 関数に含まれる[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]です。

インストールされているパッケージによって提供される新しい関数を使用して、データを視覚化するプロットを生成する、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]です。

> [!TIP]
> R をマスターできましたか?
>   
> これで、すべてのデータをダウンロードし、環境が整いました。RStudio または他のあらゆる環境で完全な R スクリプトを実行して、ご自身で機能を探索してみてください。 RSQL_Walkthrough.R ファイルを開き、デモとして個々の行を強調表示して実行するか、スクリプト全体を実行します。
>   
> RevoScaleR 関数に関するその他の説明および、R で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを使用するときのヒントについては、チュートリアルをお続けください。 完全に同じスクリプトを使用しています。

## <a name="verify-downloaded-data-using-sql-server"></a>SQL Server を使用してデータをダウンロードしたことを確認します。

まず、少し時間をかけて、データが正しく読み込まれたことを確認します。

1. 接続、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスなど、お気に入りのデータベース管理ツールを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Visual Studio または Visual Studio Code のサーバー エクスプ ローラー。

2. 展開すると、新しいデータベース、テーブル、および関数を表示し、作成したデータベースを選択します。
  
    ![rsql_e2e_ssms_newobjects](media/rsql-e2e-ssms-newobjects.PNG)
  
3.  データが正しく読み込まれていることを確認し、テーブルを右クリックして、選択**上位 1000 行**です。 メニュー オプションは、このクエリを実行します。

    ```SQL
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]
    ```
    テーブル内のデータが表示されない場合は、前のセクションの「 [トラブルシューティング](walkthrough-prepare-the-data.md) 」セクションを参照してください。

4. このデータ テーブルは、[columnstore インデックス](../../relational-databases/indexes/columnstore-indexes-overview.md)を追加することにより、セットベースの計算に対して最適化されています。 テーブルに簡単な概要を生成するには、このステートメントを実行します。

    ```SQL
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
    次のレッスンでは、R を使用してより複雑な概要を生成します。

## <a name="next-lesson"></a>次のレッスン

[R を使用するデータを概要します。](walkthrough-view-and-summarize-data-using-r.md)

## <a name="previous-lesson"></a>前のレッスン

[PowerShell を使用してデータを準備します。](walkthrough-prepare-the-data.md)
