---
title: "sys.dm_os_server_diagnostics_log_configurations |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e5a57c9617191a53545e590aa6695d82c0ee6d30
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  現在の構成で 1 つの行を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター診断ログです。 診断ログのオンまたはオフ、ログ ファイルの場所、数、およびサイズは、これらのプロパティ設定によって決まります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|ログ記録がオンとオフのどちらであるかを示します。<br /><br /> 1 = 診断ログはオンです。<br /><br /> 0 = 診断ログはオフです。|  
|max_size|**int**|各診断ログの最大サイズ (MB 単位)。 既定値は 100 MB です。|  
|max_files|**int**|新しい診断ログとして再利用されるまでにコンピューターに格納できる診断ログ ファイルの最大数。|  
|path|**nvarchar (260)**|診断ログの場所を示すパス。 既定の場所は\<\MSSQL\Log > のインストール フォルダー内で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。|  
  
## <a name="permissions"></a>Permissions  
 SQL Server フェールオーバー クラスター インスタンスに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、sys.dm_os_server_diagnostics_log_configurations を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー診断ログのプロパティ設定を返します。  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program files \microsoft SQL server \mssql13\mssql\log >|10|10|  
  
## <a name="see-also"></a>参照  
 [フェールオーバー クラスター インスタンスの診断ログを表示して読む方法](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
