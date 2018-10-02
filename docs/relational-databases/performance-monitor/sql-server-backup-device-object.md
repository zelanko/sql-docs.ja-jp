---
title: 'SQL Server: Backup Device オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b622b17b19d3fedf192eecc1d976330c685752c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602750"
---
# <a name="sql-server-backup-device-object"></a>SQL Server: Backup Device オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **Backup Device** オブジェクトには、バックアップ操作と復元操作に使用する Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ デバイスを監視するためのカウンターがあります。 バックアップ デバイスを監視するのは、バックアップ操作と復元操作のスループット、または進行状況やパフォーマンスをデバイスごとに調べる場合です。 データベースのバックアップ操作または復元操作全体のスループットを監視するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** オブジェクトの **Backup/Restore Throughput/sec** カウンターを使用します。 詳しくは、「 [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md)」をご覧ください。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** カウンターについて説明します。  
  
|SQL Server Backup Device カウンター|[説明]|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes/sec**|データベースをバックアップまたは復元するときに使用するバックアップ デバイスの読み取りおよび書き込み操作のスループット (1 秒あたりのバイト数)。 このカウンターは、バックアップ操作または復元操作の実行中のみ存在します。|  
  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
