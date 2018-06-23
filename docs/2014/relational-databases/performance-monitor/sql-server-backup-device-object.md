---
title: 'SQL Server: Backup Device オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 62ba36e83f08cabda85fd71a02d4e22842fb0e8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174154"
---
# <a name="sql-server-backup-device-object"></a>SQL Server: Backup Device オブジェクト
  **Backup Device** オブジェクトには、バックアップ操作と復元操作に使用する Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ デバイスを監視するためのカウンターがあります。 バックアップ デバイスを監視するのは、バックアップ操作と復元操作のスループット、または進行状況やパフォーマンスをデバイスごとに調べる場合です。 データベースのバックアップ操作または復元操作全体のスループットを監視するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** オブジェクトの **Backup/Restore Throughput/sec** カウンターを使用します。 詳しくは、「 [SQL Server, Databases Object](sql-server-databases-object.md)」をご覧ください。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** カウンターについて説明します。  
  
|SQL Server Backup Device カウンター|説明|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes/sec**|データベースをバックアップまたは復元するときに使用するバックアップ デバイスの読み取りおよび書き込み操作のスループット (1 秒あたりのバイト数)。 このカウンターは、バックアップ操作または復元操作の実行中のみ存在します。|  
  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](monitor-resource-usage-system-monitor.md)  
  
  