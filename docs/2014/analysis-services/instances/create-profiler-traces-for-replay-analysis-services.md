---
title: 再生用のプロファイラートレースの作成 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- replaying queries
- replaying discovers
- events [Analysis Services]
- replaying commands
- Profiler [SQL Server Profiler], Analysis Services
- performance [Analysis Services], replays
- traces [Analysis Services]
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 994fa58d9def8048f7fb88e09721055d2b184bb0
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544004"
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>再生用のプロファイラー トレースの作成 (Analysis Services)
  ユーザーによってに送信されたクエリ、検出、およびコマンドを再生するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 必要なイベントを収集する必要があります。 このようなイベントの収集を開始するには、 **[トレースのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブで適切なイベント クラスを選択する必要があります。 たとえば、Query Begin イベント クラスが選択されている場合は、クエリを含んでいるイベントが収集され、再生に使用されます。 また、トレース ファイルには、分散環境におけるサーバー トランザクションを当初のトランザクション シーケンスで再生するための十分な情報が含まれています。  
  
## <a name="replay-for-queries"></a>クエリの再生  
 クエリを再生するには、次のイベントを [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でキャプチャする必要があります。  
  
-   すべてのデータ列が含まれた Audit Login イベント クラス。 このイベント クラスでは、ログインしたユーザーとセッションの設定に関する情報が提供されます。 サーバー プロセス ID (SPID) では、ユーザー セッションに対する参照が提供されます。 詳細については、「 [Security Audit のデータ列](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns)」を参照してください。  
  
-   すべてのデータ列が含まれた Query Begin イベント クラス。 このイベント クラスでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に送信されたクエリに関する情報が提供されます。 イベント サブクラス列では、クエリの種類に関する情報が提供されます。 TextData 列では、クエリの実際のテキストが提供されます。 RequestParameters 列では、パラメーター化クエリのパラメーターが提供され、RequestProperties 列では、XML for Analysis (XMLA) 要求のプロパティが提供されます。 詳細については、「 [Queries イベントのデータ列](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns)」を参照してください。  
  
-   すべてのデータ列が含まれた Query End イベント クラス。 このイベント クラスでは、クエリの実行状態が検証されます。 詳細については、「 [Queries イベントのデータ列](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns)」を参照してください。  
  
## <a name="replay-for-discovers"></a>検出の再生  
 検出を再生するには、次のイベントを [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でキャプチャする必要があります。  
  
-   すべてのデータ列が含まれた Audit Login イベント クラス。 このイベント クラスでは、ログインしたユーザーとセッションの設定に関する情報が提供されます。 SPID では、ユーザー セッションに対する参照が提供されます。 詳細については、「 [Security Audit のデータ列](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns)」を参照してください。  
  
-   すべてのデータ列が含まれた Discover Begin イベント クラス。 TextData 列は \<RequestType> discover 要求の一部を提供し、RequestProperties 列は \<Properties> discover 要求の一部を提供します。 EventSubclass 列では、検出の種類が提供されます。 詳細については、「 [Discover イベントのデータ列](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns)」を参照してください。  
  
-   すべてのデータ列が含まれた Discover End イベント クラス。 このイベント クラスでは、検出要求の状態が検証されます。 詳細については、「 [Discover イベントのデータ列](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns)」を参照してください。  
  
## <a name="replay-for-commands"></a>コマンドの再生  
 コマンドを再生するには、次のイベントを [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でキャプチャする必要があります。  
  
-   すべてのデータ列が含まれた Command Begin イベント クラス。 TextData 列では、処理の種類、データベース ID、キューブ ID などのコマンドの詳細情報が提供されます。 RequestParameters 列では、パラメーター化コマンドのパラメーターが提供され、RequestProperties 列では、XMLA 要求のプロパティが提供されます。 詳細については、「 [Command イベントのデータ列](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns)」を参照してください。  
  
-   すべてのデータ列が含まれた Command End イベント クラス。 このイベント クラスでは、コマンドの状態が検証されます。 詳細については、「 [Command イベントのデータ列](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [トレースイベントの Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)   
 [SQL Server Profiler による Analysis Services の監視の概要](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
