---
title: "DirectQuery モードでモデルをテストする | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# DirectQuery モードでモデルをテストする
  デザインから開発の各段階で DirectQuery モードのテーブル モデルをテストするためのオプションを確認します。  
  
## Excel でテストする 
  
 SSDT でモデルを設計するときに、**Excel で分析**機能を使用して、メモリ内のサンプル データセットやリレーショナル データベースに対してモデリングに関する決定をテストできます。  [Excel で分析] をクリックすると、オプションを指定するダイアログ ボックスが開きます。
 
 ![Excel で分析の DirectQuery オプション](../../analysis-services/tabular-models/media/analyze-in-excel-directquery-options.png)
 
 モデルの DirectQuery モードがオンの場合、DirectQuery 接続モードの 2 つのオプションを指定できます。
 - **[サンプル データ ビュー]** - Excel からのすべてのクエリが、メモリ内のサンプル データセットを含むサンプル パーティションに送られます。 このオプションは、メジャー、計算列、行レベルのセキュリティに含まれる DAX 式が正常に実行されることを確認する場合に便利です。
 
 - **[フル データ ビュー]** - Excel からのクエリは、Analysis Services を経てリレーショナル データベースに送られます。 このオプションは、事実上、完全に機能する DirecQuery モードです。
 
 ### その他のクライアント
 Excel で分析を使用すると、.odc 接続ファイルが作成されます。 このファイルの接続文字列情報を使用して、他のクライアント アプリケーションからモデルに接続できます。 追加パラメーター DataView=Sample は、クライアントがサンプル データ パーティションに接続する必要があることを指定します。  
  
## xEvents または SQL Profiler を使ってバックエンド システムでクエリの実行を監視する 
 SQL Server のリレーショナル データベースに接続されたセッション トレースを開始して、表形式モデルからの接続を監視します。  
  
-   [SQL Server 拡張イベントを使用した Analysis Services の監視](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
-   [SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 Oracle または Teradata を使用している場合は、それらのシステムのトレース監視ツールを使用してください。  
  
  