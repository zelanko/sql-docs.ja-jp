---
title: backup_devices (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b70d87a6f1a72662c1ca466a532d3050b4fe58ab
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942587"
---
# <a name="sysbackup_devices-transact-sql"></a>backup_devices (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sp_addumpdevice**を使用して登録された、またはで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]作成されたバックアップデバイスごとに1行の値を格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|バックアップ デバイスの名前。 セット内で一意です。|  
|**type**|**tinyint**|バックアップ デバイスの種類。<br /><br /> 2 = ディスク<br /><br /> 3 = フロッピーディスク (廃止)<br /><br /> 5 = テープ<br /><br /> 6 = パイプ (obsolete)<br /><br /> 7 = 仮想デバイス (サードパーティのバックアップベンダーがオプションで使用)<br /><br /> 通常は、ディスク (2) またはテープ (5) のみが使用されます。|  
|**type_desc**|**nvarchar(60)**|バックアップ デバイスの種類の説明。<br /><br /> DISK<br /><br /> フロッピーディスク (廃止)<br /><br /> TAPE<br /><br /> パイプ (obsolete)<br /><br /> VIRTUAL_DEVICE (サード パーティ バックアップ ベンダーがオプションで使用)<br /><br /> 通常は、DISK および TAPE のみが使用されます。|  
|**physical_name**|**nvarchar(260)**|バックアップデバイスの物理ファイル名またはパス。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [バックアップデバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [データベースとファイルのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
