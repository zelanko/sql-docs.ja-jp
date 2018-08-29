---
title: トレースおよび再生のイベント |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 35e887a1f065840f7ff9b8264ec8d4e24bd7c920
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43061047"
---
# <a name="tracing-and-replaying-events"></a>イベントのトレースおよび再生
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO では、**トレース**と**再生**内のオブジェクト、<xref:Microsoft.SqlServer.Management.Trace>名前空間へのプログラムによるアクセスを提供する、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] のインスタンスを監視するために使用される機能、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 各イベントに関するデータをキャプチャし、ファイルやテーブルに保存して、後で分析できます。 たとえば、実稼動環境を監視して、どのプロシージャの実行が遅く、パフォーマンスに影響を与えているかを確認できます。  
  
 **トレース**と**再生**オブジェクトのインスタンスでトレースの作成に使用できるオブジェクトのセットを提供する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 これらのオブジェクトをユーザー独自のアプリケーションから使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] に対してトレースを手動で作成することもできます。 さらに、SMO**トレース**オブジェクトは、SQL トレース ファイルと監視することによって作成されたテーブルの読み取りに使用できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、または DTS ログを記録します。  
  
 SMO**トレース**オブジェクトでは、次の関数を実行できます。  
  
-   トレースの作成。  
  
-   トレース上でのフィルターの設定。  
  
-   トレースするイベントの設定。  
  
-   トレースの停止または開始。  
  
-   トレース ファイルおよびトレース テーブルの読み取り。  
  
-   トレースでのイベントに関する情報の取得。  
  
-   トレースでのフィルターに関する情報の取得。  
  
-   プログラムを使用したトレース データの操作。  
  
-   トレース テーブルおよびトレース ファイルの書き込み。  
  
-   トレース ファイルまたはトレース テーブルの再生。  
  
 トレース データ、**トレース**と**再生**オブジェクトは、SMO アプリケーションで使用できるかを使用して手動で調べることができます[SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md)します。 トレース データと互換性のあるでも、 [SQL トレース](../../../relational-databases/sql-trace/sql-trace.md)トレース機能を提供するストアド プロシージャ。  
  
 SMO トレース オブジェクトは、Microsoft.SQLServer.ConnectionInfo.dll ファイルへの参照が必要となる <xref:Microsoft.SqlServer.Management.Trace> 名前空間に存在します。  
  
 **トレース**と**再生**オブジェクトを必要とする[ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A>オブジェクトのインスタンスとの接続を確立するために[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)オブジェクトに格納されて、 [Microsoft.SqlServer.Management.Common](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common)名前空間は、Microsoft.SQLServer.ConnectionInfo.dll ファイルへの参照が必要です。  
  
> [!NOTE]  
>  **トレース**と**再生**オブジェクトは、64 ビット プラットフォームでサポートされていません。  
  
  
