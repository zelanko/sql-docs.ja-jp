---
title: "データ サイエンスの詳細: RevoScaleR パッケージの使用 | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51f4a782ad941d8b9a66ba00cbf2b3540478361c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-science-deep-dive-using-the-revoscaler-packages"></a>データ サイエンスの詳細: RevoScaleR パッケージの使用

このチュートリアルで提供される強化された R パッケージを使用する方法を示します[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]SQL Server のデータを操作および高パフォーマンスのビッグ データ分析のコンピューティング コンテキストとしてサーバーを使用して、スケーラブルな R ソリューションを作成します。

ローカルおよびリモート計算コンテキスト間でデータを移動は、リモート計算コンテキストを作成する方法を学習し、リモートの SQL Server で R コードを実行します。 分析し、ローカルとリモート サーバーの両方にデータをプロットする方法と作成し、モデルを配置する方法も学習します。

> [!NOTE]
> 
> このチュートリアルでは、Windows では、SQL Server のデータで具体的には機能し、データベース内の計算コンテキストを使用します。 Teradata、Linux、Hadoop など、他のコンテキストで R を使用する場合は、これらの Microsoft R Server チュートリアルを参照してください。 
> + [R サーバー sparklyr を使用します](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-spark-interop)
> + [25 の関数で R と ScaleR を探索する](https://msdn.microsoft.com/microsoft-r/microsoft-r-tutorial-r2revoscaler)
> + [Hadoop MapReduce ScaleR を概要します。](https://msdn.microsoft.com/microsoft-r/scaler-hadoop-getting-started)
> + [取得する RevoScaleR Teradata Started Guide](https://msdn.microsoft.com/microsoft-r/scaler-teradata-getting-started)

## <a name="overview"></a>概要

ScaleR パッケージの柔軟性と処理能力を示すため、このチュートリアルでは、データの移動と計算コンテキストの切り替えを頻繁に行います。

+ 最初に、CSV ファイルまたは XDF ファイルからデータを取得します。 RevoScaleR パッケージの関数を使用して、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にインポートします。
+ モデルのトレーニングとスコア付けは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の計算コンテキストで実行されます。
    スコア付けの結果を保存するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rx **関数を使用して新しい** テーブルを作成します。
+ サーバーとローカル両方の計算コンテキストで、プロットを作成します。
+ モデルのトレーニングでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに既に格納されているデータを使用します。 計算はすべて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで実行されます。
+ データのサブセットを抽出し、それを分析時に再利用できるように XDF ファイルとしてローカル ワークステーション上に保存します。
+ スコア付けのプロセス中に使用する新しいデータは、ODBC 接続を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから抽出されます。 すべての計算がローカル ワークステーションで実行されます。
+ 最後に、サーバーの計算コンテキストを使用して、カスタム R 関数に基づくシミュレーションを実行します。

### <a name="get-started-now"></a>作業開始

このチュートリアルでは約 75 分を完了すると、セットアップは含まれません。

1. [R を使用する SQL Server データを操作します。](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [クエリおよび SQL Server データの変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [定義し、計算コンテキストを使用します。](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [作成し、R スクリプトを実行します。](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [R を使用する SQL Server データを視覚化します。](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [R モデルを作成します。](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [新しいデータのスコア](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [R を使用するデータを変換します。](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [RxImport を使用しているメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [RxDataStep を使用して、新しい SQL Server のテーブルを作成します。](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [RxDataStep を使用して、チャンキング分析を実行します。](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [ローカル コンピューティング コンテキストにあるデータを分析します。](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [SQL Server と XDF ファイル間でデータを移動します。](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [単純なシミュレーションを作成します。](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>対象読者

このチュートリアルの対象読者は、データ サイエンティスト、または R、および調査、統計分析、モデル調整などのデータ サイエンス タスクについて既にある程度理解している方です。  ただし、すべてのコードが提供される、R に慣れていない場合でも簡単にコードを実行して進むには、必要なサーバーとクライアントの環境があると仮定するとします。

読者はまた、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文に精通していて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはその他のデータベース ツール (Visual Studio など) を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] データベースにアクセスする方法を理解している必要があります。
  
> [!TIP]
> 中断した箇所からを容易に再開できるように、レッスンの合間に R ワークスペースを保存してください。

### <a name="prerequisites"></a>前提条件

- **SQL Server の R のサポート**
  
    SQL Server 2016 をインストールし、R Services (In-database) を有効にします。 SQL Server 2017 をインストールし、Machine Learning のサービスを有効にし、R 言語を選択します。 セットアップ プロセスについては、「 [SQL Server 2016 オンライン ブック](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx)です。
  
-  **データベース権限**
  
    モデルのトレーニングで使用するクエリを実行するには、データが格納されているデータベースに対して **db_datareader** 権限が必要です。 R を実行するには、EXECUTE ANY EXTERNAL SCRIPT、アクセス許可が、ユーザーに必要です。

-   **データ サイエンス開発用コンピューター**
  
    R 開発環境で、RevoScaleR パッケージと関連するプロバイダーをインストールすることも必要があります。 これを行う最も簡単な方法では、Microsoft R クライアントまたは Microsoft R Server (スタンドアロン) をインストールします。 詳しくは、「 [データ サイエンス クライアントのセットアップ](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx)」をご覧ください。
      
    > [!NOTE] 
    > 他のバージョンの Revolution R Enterprise または Revolution R Open はサポートされていません。
    > 
    > R、R 3.2.2 などのオープン ソース ディストリビューションは、RevoScaleR 関数のみがリモート計算コンテキストを使用できるため、このチュートリアルでは機能しません。
  
-   **追加の R パッケージ**
  
    このチュートリアルでは、 **dplyr**、 **ggplot2**、 **ggthemes**、 **reshape2**、および **e1071**のパッケージをインストールする必要があります。 手順は、チュートリアルの中で説明します。
  
    2 つの場所のすべてのパッケージをインストールする必要があります: R ソリューションの開発では、使用するコンピューターと R スクリプトを実行する SQL Server コンピューター。 サーバー コンピューターにパッケージをインストールするアクセス許可があるない場合、管理者に問い合わせてください。 **ユーザー ライブラリにはパッケージをインストールしないでください。** SQL Server のインスタンスによって使用される R パッケージ ライブラリで、パッケージをインストールすることが重要です。

詳細については、次を参照してください。[データ サイエンスのチュートリアルの前提条件](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md)です。



## <a name="next-step"></a>次の手順

[R を使用する SQL Server データを操作します。](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)


