---
title: SQL Server:HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ea717edbbed863b262617e457ac29fc3d45a4be4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-httpstorageobject"></a>SQL Server:HTTP_STORAGE_OBJECT
  **SQLServer:HTTP_STORAGE_OBJECT** パフォーマンス オブジェクトは、Windows Azure ストレージ アカウントを監視する各種のパフォーマンス カウンターで構成されています。 [Microsoft Azure 内の SQL Server データ ファイル](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) 機能を使用すると、データベース ファイルを Windows Azure ストレージ BLOB に格納できます。 このパフォーマンス オブジェクトでは、各 Windows Azure ストレージ アカウントが別々のドライブとして処理されます。  
  
|カウンター名|説明|  
|------------------|-----------------|  
|**Read Bytes/sec**|読み取り操作中に HTTP ストレージから転送されている 1 秒あたりのデータ量。|  
|**Write Bytes/sec**|書き込み操作中に HTTP ストレージから転送されている 1 秒あたりのデータ量。|  
|**Total Bytes/sec**|読み取りまたは書き込み操作中に HTTP ストレージから転送されている 1 秒あたりのデータ量。|  
|**Reads/sec**|HTTP ストレージでの 1 秒あたりの読み取り数。|  
|**Writes/sec**|HTTP ストレージでの 1 秒あたりの書き込み数。|  
|**Transfers/sec**|HTTP ストレージでの 1 秒あたりの読み取りおよび書き込み操作数。|  
|**平均Bytes/Read**|読み取りごとに HTTP ストレージから転送された平均バイト数。|  
|**平均Bytes/Read BASE**|内部使用のみです。|
|**平均Bytes/Transfer**|読み取りまたは書き込み操作中に HTTP ストレージから転送された平均バイト数。|  
|**平均Bytes/Transfer BASE**|内部使用のみです。|
|**平均Bytes/Write**|書き込みごとに HTTP ストレージから転送された平均バイト数。|  
|**平均Bytes/Write BASE**|内部使用のみです。|
|**Avg. microsec/Read**|HTTP ストレージからの読み取りごとに要する平均マイクロ秒数。|  
|**Avg. microsec/Read BASE**|内部使用のみです。|
|**Avg. microsec/Read Comp**|HTTP がストレージへの読み取り完了にかかる平均マイクロ秒数。| 
|**Avg. microsec/Read Comp BASE**|内部使用のみです。|
|**Avg. microsec/Write**|HTTP ストレージへの書き込みごとに要する平均マイクロ秒数。|  
|**Avg. microsec/Transfer**|HTTP ストレージへの転送ごとに要する平均マイクロ秒数。|  
|**Avg. microsec/Transfer BASE**|内部使用のみです。|
|**Avg. microsec/Write BASE**|内部使用のみです。|
|**Avg. microsec/Write Comp**|HTTP がストレージへの書き込み完了にかかる平均マイクロ秒数。|  
|**Avg. microsec/Write Comp BASE**|内部使用のみです。|
|**Outstanding HTTP Storage I/O**|HTTP ストレージに対する未処理 I/O の合計数。|  
|**HTTP Storage IO failed/sec**|HTTP ストレージに送信されて失敗した書き込み要求の 1 秒あたりの数。| 
|**HTTP Storage I/O Retry/sec**|HTTP ストレージに送信された 1 秒あたりの再試行要求数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  

