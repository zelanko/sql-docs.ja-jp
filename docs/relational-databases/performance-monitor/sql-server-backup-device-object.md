---
title: "SQL Server: Backup Device オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4a89a457d90882db719c387a317a6944aed7d745
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-backup-device-object"></a>SQL Server: Backup Device オブジェクト
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  **Backup Device** オブジェクトには、バックアップ操作と復元操作に使用する Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ デバイスを監視するためのカウンターがあります。 バックアップ デバイスを監視するのは、バックアップ操作と復元操作のスループット、または進行状況やパフォーマンスをデバイスごとに調べる場合です。 データベースのバックアップ操作または復元操作全体のスループットを監視するには、 **** Databases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. 詳しくは、「 [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md)」をご覧ください。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** カウンターについて説明します。  
  
|SQL Server Backup Device カウンター|説明|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes/sec**|データベースをバックアップまたは復元するときに使用するバックアップ デバイスの読み取りおよび書き込み操作のスループット (1 秒あたりのバイト数)。 このカウンターは、バックアップ操作または復元操作の実行中のみ存在します。|  
  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
