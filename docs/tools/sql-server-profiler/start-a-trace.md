---
title: トレースの開始
titleSuffix: SQL Server Profiler
description: SQL Server Profiler で、新しいトレースを定義するかテンプレートを作成した後、トレースを開始し、そのデータを見つける方法について説明します。
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 261c18ff809bd8a6fb1a7960c753c6fd64bbc462
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753672"
---
# <a name="start-a-trace"></a>トレースの開始

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して新しいトレース定義するか、テンプレートを作成したら、新しいトレース定義またはテンプレートを使用してデータのキャプチャを開始、一時停止、または停止することができます。  
  
## <a name="starting-a-trace"></a>トレースの開始

定義されているトレース元が [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスである場合、トレースを開始すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、キャプチャしたサーバー イベントを一時的に保持する場所を提供するキューが作成されます。  
  
[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して SQL トレースにアクセスすると、トレース ウィンドウが表示されていない場合、トレースの開始時に新しいトレース ウィンドウが表示され、データがすぐにキャプチャされます。  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャを使用して SQL トレースにアクセスする際には、データをキャプチャする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されるたびにトレースを開始する必要があります。 トレースの開始後に変更できるのはトレースの名前のみです。  
  
> [!NOTE]  
>  既存のトレースを使用する場合、プロパティを参照できますが、変更できません。 プロパティを変更するには、トレースを停止または一時停止する必要があります。  
  
## <a name="see-also"></a>参照

[サーバーへの接続後の自動的なトレースの開始 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   

[トレースの一時停止 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   

[トレースの停止 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   

[トレース ウィンドウの消去 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   

[一時停止または停止したトレースの再開 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)