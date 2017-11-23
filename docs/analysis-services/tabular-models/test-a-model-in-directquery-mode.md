---
title: "DirectQuery モードでモデルのテスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d6f55de10089d304fe5dc5d00c388d007a2241a6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="test-a-model-in-directquery-mode"></a>DirectQuery モードでモデルをテストする

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  デザインから開発の各段階で DirectQuery モードのテーブル モデルをテストするためのオプションを確認します。  
  
## <a name="test-in-excel"></a>Excel でテストする 
  
 SSDT でモデルを設計するときに、 **Excel で分析** 機能を使用して、メモリ内のサンプル データセットやリレーショナル データベースに対してモデリングに関する決定をテストできます。  [Excel で分析] をクリックすると、オプションを指定するダイアログ ボックスが開きます。
 
 ![Excel で分析の DirectQuery オプション](../../analysis-services/tabular-models/media/analyze-in-excel-directquery-options.png)
 
 モデルの DirectQuery モードがオンの場合、DirectQuery 接続モードの 2 つのオプションを指定できます。
 - **[サンプル データ ビュー]** - Excel からのすべてのクエリが、メモリ内のサンプル データセットを含むサンプル パーティションに送られます。 このオプションは、メジャー、計算列、行レベルのセキュリティに含まれる DAX 式が正常に実行されることを確認する場合に便利です。
 
 - **[フル データ ビュー]** - Excel からのクエリは、Analysis Services を経てリレーショナル データベースに送られます。 このオプションは、事実上、完全に機能する DirecQuery モードです。
 
 ### <a name="other-clients"></a>その他のクライアント
 Excel で分析を使用すると、.odc 接続ファイルが作成されます。 このファイルの接続文字列情報を使用して、他のクライアント アプリケーションからモデルに接続できます。 追加パラメーター DataView=Sample は、クライアントがサンプル データ パーティションに接続する必要があることを指定します。  
  
## <a name="monitor-query-execution-on-backend-systems-using-xevents-or-sql-profiler"></a>xEvents または SQL Profiler を使ってバックエンド システムでクエリの実行を監視する 
 SQL Server のリレーショナル データベースに接続されたセッション トレースを開始して、表形式モデルからの接続を監視します。  
  
-   [SQL Server 拡張イベントを使用した Analysis Services の監視](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
-   [SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 Oracle または Teradata を使用している場合は、それらのシステムのトレース監視ツールを使用してください。  
  
  
