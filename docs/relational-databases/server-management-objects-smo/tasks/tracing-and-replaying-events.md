---
title: イベントのトレースと再生 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c6a164927ed5a6dd711dc6d2243dd3b96c85ca08
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896308"
---
# <a name="tracing-and-replaying-events"></a>イベントのトレースおよび再生
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  SMO では、名前空間の**Trace**オブジェクトと**Replay**オブジェクトによって、 <xref:Microsoft.SqlServer.Management.Trace> [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] またはのインスタンスの監視に使用される機能にプログラムからアクセス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] できます。 各イベントに関するデータをキャプチャし、ファイルやテーブルに保存して、後で分析できます。 たとえば、実稼動環境を監視して、どのプロシージャの実行が遅く、パフォーマンスに影響を与えているかを確認できます。  
  
 **Trace**オブジェクトと**Replay**オブジェクトには、のインスタンスでトレースを作成するために使用できる一連のオブジェクトが用意されて [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] います。 これらのオブジェクトをユーザー独自のアプリケーションから使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] に対してトレースを手動で作成することもできます。 また、SMO**トレース**オブジェクトを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、または DTS ログを監視することによって作成された SQL トレースファイルとテーブルを読み取ることができます。  
  
 SMO**トレース**オブジェクトを使用すると、次の機能を実行できます。  
  
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
  
 **トレース**オブジェクトと**再生**オブジェクトからのトレースデータは、SMO アプリケーションで使用できます。また、 [SQL Server プロファイラー](../../../tools/sql-server-profiler/sql-server-profiler.md)を使用して手動で調べることもできます。 トレースデータは、トレース機能を提供する[SQL トレース](../../../relational-databases/sql-trace/sql-trace.md)ストアドプロシージャとも互換性があります。  
  
 SMO トレース オブジェクトは、Microsoft.SQLServer.ConnectionInfo.dll ファイルへの参照が必要となる <xref:Microsoft.SqlServer.Management.Trace> 名前空間に存在します。  
  
 **Trace**オブジェクトと**Replay**オブジェクトには、のインスタンスとの接続を確立するための[serverconnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> オブジェクトが必要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] です。 [Serverconnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)オブジェクトは、Microsoft.SQLServer.ConnectionInfo.dll ファイルへの参照を必要とする、 [Microsoft の SqlServer](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common)名前空間に存在します。  
  
> [!NOTE]  
>  **トレース**オブジェクトと**再生**オブジェクトは、64ビットプラットフォームではサポートされていません。  
  
  
