---
title: 概要については Analysis Services インスタンスの監視 |Microsoft Docs
ms.date: 11/16/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39cc5a22165d07aafce29e4216548c4e8d226892
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62709466"
---
# <a name="monitoring-overview"></a>監視の概要
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services は、監視し、サーバーのパフォーマンスを調整するのに役立つさまざまなツールです。 どのツールを選択するかは、実行する監視またはチューニングの種類や、監視するイベントによって異なります。

SQL Server Analysis Services の監視の詳細については、次を参照してください。、 [SQL Server 2008 R2 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539)します。  
  
## <a name="monitoring-tools"></a>監視ツール  

|ツール  |説明  |
|---------|---------|
|[SQL Server Profiler](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)      |   エンジン プロセス イベントを追跡します。 サーバーおよびデータベースの利用状況の監視を有効にすると、それらのイベントに関するデータもキャプチャします。      |
| [拡張イベント](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)     |   軽量のトレースとパフォーマンスがわずかなシステム リソースを使用するシステムの監視、運用環境とテストの両方のサーバー上の問題を診断するための最適なツールになります。       |
| [動的管理ビュー &#40;Dmv&#41;](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)      |   モデル オブジェクト、サーバーの操作、およびサーバーの正常性に関する情報を返すクエリです。 SQL、に基づいて、クエリは、スキーマ行セット インターフェイスです。      |
| [トレース イベント](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)     |  インスタンスのアクティビティをキャプチャし、インスタンスによって生成されたトレース イベントを分析してに従います。 トレース イベントは、関連するトレース イベントをより簡単に見つけることができるようにグループ化されます。        |
|   [パフォーマンス カウンター](../../analysis-services/instances/performance-counters-ssas.md)\*    |    パフォーマンス モニターを使用すると、Microsoft SQL Server Analysis Services (SSAS) インスタンスのパフォーマンスをパフォーマンス カウンターで監視できます。     |
|[ログ操作](../../analysis-services/instances/performance-counters-ssas.md)\*|SQL Server Analysis Services インスタンスは、サーバーの通知、エラー、および警告を msmdsrv.log ファイルをインストールするインスタンスごとに 1 つにログインがします。 |

\* SQL Server Analysis Services のみに適用されます。

## <a name="see-also"></a>関連項目

[Azure Analysis Services サーバーのメトリックを監視します。](https://docs.microsoft.com/azure/analysis-services/analysis-services-monitor)   
[Azure Analysis Services の診断ログをセットアップします。](https://docs.microsoft.com/azure/analysis-services/analysis-services-logging)
