---
title: sys.dm_os_cluster_properties (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_cluster_properties_TSQL
- sys.dm_os_cluster_properties
- dm_os_cluster_properties_TSQL
- dm_os_cluster_properties
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_cluster_properties
- sys.dm_os_cluster_properties
ms.assetid: 6d82e770-fba7-49e0-9a0c-3b34b393e4a7
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 617f40a71074c8480d38e2eb5f59e108ee2d6ff7
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosclusterproperties-transact-sql"></a>sys.dm_os_cluster_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  1 つの行の現在の設定を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスター リソース プロパティがこのトピックに記載します。 このビューのスタンドアロン インスタンスで実行される場合にデータが返されない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 これらのプロパティは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのエラー検出、障害応答時間、および正常性状態の監視のログ記録に影響を与える値を設定するために使用されます。  
  

|列名|プロパティ|Description|  
|-----------------|--------------|-----------------|  
|VerboseLogging|bigint|SQL Server フェールオーバー クラスターのログ記録レベルです。 詳細ログをオンにすると、トラブルシューティングを目的とした詳細情報をエラー ログに追加できます。 次のいずれかの値です。<br /><br /> 0: ログ記録はオフです (既定)。<br /><br /> 1: エラーのみ。<br /><br /> 2: エラーおよび警告。<br /><br /> 詳細については、次を参照してください。 [ALTER SERVER CONFIGURATION &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)です。|  
|SqlDumperDumpFlags|bigint|SQLDumper ダンプ フラグによって生成されたダンプ ファイルの種類を決定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 既定の設定は 0 です。|  
|SqlDumperDumpPath|nvarchar (260)|SQLDumper ユーティリティがダンプ ファイルを生成する場所です。|  
|SqlDumperDumpTimeOut|bigint|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でエラーが発生した場合の、SQLDumper ユーティリティによるダンプの生成のタイムアウト値 (ミリ秒単位) です。 既定値は 0 です。|  
|FailureConditionLevel|bigint|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターのエラーまたは再起動の条件を設定します。 既定値は、3 です。 詳細については、またはプロパティの設定を変更するを参照してください。 [FailureConditionLevel プロパティ設定の構成](../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md)です。|  
|HealthCheckTimeout|bigint|SQL Server データベース エンジンのリソース DLL が、サーバーの状態情報を待機する時間のタイムアウト値です。この待機時間を経過すると、SQL Server のインスタンスが応答不能と見なされます。 このタイムアウト値は、ミリ秒単位で指定します。 既定値は 60000 です。 詳細については、またはこのプロパティの設定を変更するを参照してください。 [HealthCheckTimeout プロパティ設定の構成](../../sql-server/failover-clusters/windows/configure-healthchecktimeout-property-settings.md)です。|  
  
## <a name="permissions"></a>権限  
 に対する VIEW SERVER STATE 権限が必要です、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。  
  
## <a name="examples"></a>使用例  
 次の例では、sys.dm_os_cluster_properties を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター リソースのプロパティ設定を返します。  
  
```  
SELECT VerboseLogging, SqlDumperDumpFlags, SqlDumperDumpPath, SqlDumperDumpTimeOut, FailureConditionLevel, HealthCheckTimeout  
FROM sys.dm_os_cluster_properties;  
```  
  
 次に結果セットの例を示します。  
  
|VerboseLogging|SqlDumperDumpFlags|SqlDumperDumpPath|SqlDumperDumpTimeOut|FailureConditionLevel|HealthCheckTimeout|  
|--------------------|------------------------|-----------------------|--------------------------|---------------------------|------------------------|  
|0|0|NULL|0|3|60000|  
  
  
