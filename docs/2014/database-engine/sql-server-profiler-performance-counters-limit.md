---
title: SQL Server Profiler - [パフォーマンス カウンター制限ダイアログ] |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2548fbd28af45cbd888a183a739362f0e7767218
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082835"
---
# <a name="sql-server-profiler---performance-counters-limit"></a>[SQL Server Profiler] - [パフォーマンス カウンター制限ダイアログ]
  [パフォーマンス カウンター制限ダイアログ] ダイアログ ボックスを使用すると、システム モニターのパフォーマンス ログ ファイルと [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] トレースを相関させるときに、ファイルからの情報を制限できます。 このダイアログ ボックスで、相関のために表示して使用するカウンターを選択できます。  
  
 **[パフォーマンス カウンター制限ダイアログ ボックス]** ダイアログ ボックスには、パフォーマンス ログ ファイルに含まれているパフォーマンス オブジェクトおよびカウンターによって値が入力されます。  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a>トレースと相関させるパフォーマンス オブジェクトおよびカウンターを選択するには  
  
1.  パフォーマンス オブジェクトを展開して、パフォーマンス ログ ファイルに含まれているカウンターを確認します。  
  
2.  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] トレース ファイルと相関させる対象カウンターをオンにします。  
  
     パフォーマンス オブジェクトに対してすべてのカウンターを選択する場合は、パフォーマンス オブジェクトの横にあるボックスをオンにします。 コンピューターを示している最上位ノードをオンにすると、パフォーマンス ログ ファイル内のすべてのパフォーマンス オブジェクトおよびカウンターが選択されます。  
  
## <a name="see-also"></a>参照  
 [トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  