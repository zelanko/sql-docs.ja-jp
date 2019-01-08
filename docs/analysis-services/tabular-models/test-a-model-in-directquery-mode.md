---
title: DirectQuery モードで Analysis Services 表形式モデルのテスト |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: def4c6231ef180e0fc7ff42bed1f170bf36884dd
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071889"
---
# <a name="test-a-model-in-directquery-mode"></a>DirectQuery モードでモデルをテストする
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
  
