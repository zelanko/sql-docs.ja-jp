---
title: "SQL Server データを扱うスケーラ関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5f3c9864-9c75-4688-947d-0940045b2671
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# SQL Server データを扱うスケーラ関数
このトピックでは、それぞれの構文に関するコメントと共に SQL Server で使用するためスケーラの主要機能の概要を示します。

スケーラ関数とその使用方法の完全な一覧については、 [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/index#) MSDN ライブラリ内の参照。 

## SQL Server データ ソースを扱う関数
次の関数が定義するため、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データ ソース。 データ ソース オブジェクトは、目的のテーブル、ビュー、またはクエリのいずれかで定義されるデータのセットと一緒に接続文字列を指定するコンテナーです。 ストアド プロシージャの呼び出しはサポートされていません。  

データ ソースを定義するだけでなく、インスタンスとデータベースで必要なアクセス許可がある場合に、R から DDL ステートメントを実行できます。 
+ [RxSqlServerData](https://msdn.microsoft.com/microsoft-r/scaler/RxSqlServerData) の定義、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データ ソース オブジェクト
+ [rxSqlServerDropTable](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerDropTable) のドロップ、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] テーブル
+ [rxSqlServerTableExists](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerTableExists) -データベースのテーブルまたはオブジェクトの存在を確認
+ [rxExecuteSQLDDL](https://msdn.microsoft.com/microsoft-r/scaler/rxExecuteSQLDDL) - 定義、操作、または SQL のデータを制御するためのコマンドを実行してもデータを返しません  

## 定義または計算コンテキストを管理するための関数
次の関数では、新しい計算コンテキストを定義する、コンピューティングのコンテキストの切り替え、または現在の計算コンテキストを識別できます。
+ [RxComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/RxComputeContext) -計算コンテキストを作成します。 
+ [rxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxInSqlServer) -できる SQL Server の計算コンテキストを生成 **スケーラ** 関数は、SQL Server の R のサービスで実行します。
+ [rxGetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxGetComputeContext) -現在の計算コンテキストを取得します。 
+ [rxSetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxSetComputeContext) の計算に使用されるコンテキストを指定します。 

## データ ソースを使用するための関数
データ ソース オブジェクトを作成した後は、ファイルを開いて、データを取得または新しいデータを書き込めません。 ソース内のデータのサイズによっても、データ ソースの一部としてバッチ サイズを定義し、チャンク単位でデータを移動できます。 
+ [rxIsOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxIsOpen) -データ ソースが利用できるかどうかを確認
+ [rxOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxOpen) -読み取り用のデータ ソースを開く
+ [rxReadNext](https://msdn.microsoft.com/microsoft-r/scaler/rxReadNext) のソースからデータを読み取る
+ [rxWriteNext](https://msdn.microsoft.com/microsoft-r/scaler/rxWriteNext) のターゲットにデータを書き込む
+ [rxClose](https://msdn.microsoft.com/microsoft-r/scaler/rxclose) -データ ソースを閉じる

スケーラ関数を使用した作業の詳細については、動作できるようにデータ ソース以外の [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], を参照してください [ Microsoft R Server - 作業の開始](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started)します。

## および XDF ファイルを操作する関数
および XDF 形式でローカル データ キャッシュを作成する次の関数を使用できます。 1 つのバッチでデータベースから転送できるより多くのデータまたはメモリに収まりきらない場合より多くのデータを使用する場合、このファイルは役に立ちます。

ローカル ワークステーションに、データベースから定期的に大量のデータを移動する場合のクエリではなく R 操作ごとに繰り返しデータベースできますファイルを使用する、および XDF データをローカルに保存し、操作、ワークスペースでは R、および XDF ファイルをキャッシュとして使用します。

+ `rxImport` データを odbc 入力元に移動および XDF ファイル
+ `RxXdfData` -および XDF データ オブジェクトを作成します。
+ `RxDataStep` -データの読み取りおよび XDF int から、データ フレーム
+ `rxXdfToDataFrame` -からデータを読み取るおよび XDF データ フレームに
+ `rxReadXdf` のデータ フレームにおよび XDF から読み取りデータ

および XDF ファイルの使用方法の例は、このチュートリアルを参照してください:  [データ サイエンスの詳細情報 - スケーラ関数を使用します。](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)

さまざまなソースからデータを転送するために使用、これらのスケーラ関数の詳細については、次を参照してください。[ Microsoft R Server - 作業の開始](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started)します。

## 参照
[R の基本クラスおよびスケーラ関数の比較](https://msdn.microsoft.com/microsoft-r/scaler/compare-base-r-scaler-functions)
