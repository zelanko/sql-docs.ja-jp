---
title: トレースと Windows パフォーマンス ログ データの関連付け | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e17eddc2b6ff02968709b6f1bb7c8de5557211fa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317492"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>トレースと Windows パフォーマンス ログ データの関連付け
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、Microsoft Windows パフォーマンス ログを開き、トレースと関連付けるカウンターを選択し、選択したパフォーマンス カウンターをトレースと共に [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のグラフィカル ユーザー インターフェイスに表示できます。 トレース ウィンドウでイベントを選択すると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の [システム モニター] データ ウィンドウ画面の赤い縦棒で、選択したトレース イベントに関連付けられているパフォーマンス ログ データが示されます。  
  
 トレースをパフォーマンス カウンターに関連付けるには、 **StartTime** および **EndTime** data columns, および then click **で** [ファイル] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu. パフォーマンス ログを開き、トレースに関連付けるシステム モニター オブジェクトおよびカウンターを選択します。  
  
## <a name="see-also"></a>参照  
 [トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
