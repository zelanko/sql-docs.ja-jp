---
title: "プロアクティブ キャッシュ (パーティション) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- hybrid OLAP
- partitions [Analysis Services], proactive caching
- relational OLAP
- multidimensional OLAP
- MOLAP
- proactive caching [Analysis Services]
- ROLAP
- cache [Analysis Services]
ms.assetid: 422660b2-4d80-4165-b1c9-3963bcde556b
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c96a6f6b6cbfc06b94b8707c1cc1a130dbcc934c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="partitions---proactive-caching"></a>パーティションのプロアクティブ キャッシュ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]プロアクティブ キャッシュは、自動 MOLAP キャッシュの作成と管理の OLAP オブジェクトを提供します。 データベース内のデータに加えられた変更は、データベースからの通知に基づき、すぐにキューブに反映されます。 プロアクティブ キャッシュの目標は、従来の MOLAP のパフォーマンスを提供しながら、ROLAP の即時性と管理のしやすさを保つことです。  
  
 簡単な <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトは、タイミングの指定およびテーブル通知で構成されます。 タイミングの指定は、変更通知を受信してからキャッシュが更新されるまでのタイムフレームを定義します。 テーブル通知は、データ テーブルと <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトとの間の通知スキーマを定義します。  
  
 多次元 OLAP (MOLAP) ストレージは、最高のクエリ応答速度を提供していますが、多少のデータ遅延があります。 リアルタイム リレーショナル OLAP (ROLAP) ストレージでは、ユーザーはデータ ソースの最新の変更内容をすぐに参照できますが、多次元 OLAP (MOLAP) ストレージに比べてパフォーマンスははるかに劣ります。これは、計算済みの集約データが存在しないことと、リレーショナル ストレージが OLAP スタイルのクエリに対して最適化されていないためです。 実行中のアプリケーションでユーザーが最新データを参照できるようにする必要があり、同時に、MOLAP ストレージの優れたパフォーマンスも取り入れたい場合、SQL Server Analysis Services では、プロアクティブ キャッシュ機能とパーティションを使用することによってこれを実現できます。 プロアクティブ キャッシュは、パーティションごとおよびディメンションごとに設定します。 プロアクティブ キャッシュ オプションは、MOLAP ストレージのパフォーマンス強化と ROLAP ストレージの即時性のバランスを保ち、基になるデータの変更時、または設定されたスケジュールに従って、自動パーティション処理機能を提供します。  
  
## <a name="proactive-caching-configuration-options"></a>プロアクティブ キャッシュ構成オプション  
 SQL Server Analysis Services には、パフォーマンスの最適化、待機時間の最小化、および処理のスケジュールを可能にするいくつかのプロアクティブ キャッシュ構成オプションが用意されています。 プロアクティブ キャッシュ機能を使用すると、必要でないデータを管理するプロセスが簡単になります。 プロアクティブ キャッシュの設定では、多次元 OLAP 構造 (MOLAP キャッシュ) を再構築する頻度、キャッシュの再構築時に古い MOLAP ストレージに対してクエリを実行するか、または基になる ROLAP データ ソースからデータを取得するか、キャッシュを指定したスケジュールで再構築するか、またはデータソースの変更に基づいて再構築するかを指定します。  
  
### <a name="minimizing-latency"></a>待機時間の最小化  
 プロアクティブ キャッシュで待機時間を最小化するように設定すると、データに最新の変更が行われたかどうかと、プロアクティブ キャッシュの構成方法によって、OLAP オブジェクトに対するユーザー クエリが ROLAP ストレージまたは MOLAP ストレージに対して行われます。 クエリ エンジンは、データ ソースに変更があるまで、MOLAP ストレージのソース データに対してクエリを実行するように指示します。 待機時間を最小化するために、データ ソースの変更後、キャッシュされた MOLAP オブジェクトは削除できます。また、MOLAP オブジェクトがキャッシュで再構築される間、クエリが ROLAP ストレージに切り替わります。 MOLAP オブジェクトが再構築されて処理されると、クエリは MOLAP ストレージに自動的に切り替えられます。 キャッシュの更新は、現在の日付と同じくらい小さい、現在のパーティションなどの小さなパーティションに対しては、非常に高速に行われます。  
  
### <a name="maximizing-performance"></a>パフォーマンスを最大化  
 待機時間を削減する一方でパフォーマンスを最適化するために、現在の MOLAP オブジェクトを削除せずにキャッシュを使用することもできます。 クエリは、データが新しいキャッシュに読み込まれ、処理されている間に MOLAP オブジェクトに対して続行されます。 この方法では、パフォーマンスは向上しますが、新しいキャッシュが構築されている間に、クエリが古いデータを返す場合があります。  
  
## <a name="see-also"></a>参照  
 [ディメンションのストレージ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [パーティション ストレージの設定 (Analysis Services - 多次元)](../../analysis-services/multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)  
  
  
