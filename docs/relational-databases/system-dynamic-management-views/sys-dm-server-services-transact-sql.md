---
title: sys.dm_server_services (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8acb2fae0aa0edadf1995a0a103ff60b66a912a9
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072137"
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンス内の SQL Server サービス、フルテキスト サービス、SQL Server エージェント サービスに関する情報を返します。 これらのサービスに関する状態情報を報告するには、この動的管理ビューを使用します。  
  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar (256)**|名前、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]フルテキスト、または SQL Server エージェント サービス。 null にすることはできません。|  
|startup_type|**int**|サービスの開始モードが表示されます。 使用可能な値とその対応する説明を次に示します。<br /><br /> 0: その他<br />1: その他<br />2: 自動<br />3: 手動<br />4: 無効<br /><br /> NULL 値が許可されます。|  
|startup_desc|**nvarchar (256)**|サービスの開始モードを記述します。 使用可能な値とその対応する説明を次に示します。<br /><br /> その他: その他 (ブート開始)<br />その他: その他 (システム開始)<br />自動: 自動開始<br />手動: 要求の開始<br />Disabled: 無効<br /><br /> null にすることはできません。|  
|status|**int**|サービスの現在の状態を示します。 使用可能な値とその対応する説明を次に示します。<br /><br /> 1: 停止<br />2: その他 (開始保留中)<br />3: その他 (停止保留中)<br />4: を実行しています。<br />5: その他 (継続保留中)<br />6: その他 (一時停止保留中)<br />7: 一時停止<br /><br /> NULL 値が許可されます。|  
|status_desc|**nvarchar (256)**|サービスの現在の状態を記述します。 使用可能な値とその対応する説明を次に示します。<br /><br /> 停止: サービスが停止します。<br />その他 (開始操作保留中): サービスは開始処理中です。<br />その他 (停止操作保留中): サービスは停止処理中です。<br />実行中: サービスが実行します。<br />その他 (継続操作保留中): サービスが保留中の状態。<br />その他 (一時停止保留中): サービスが一時停止処理中です。<br />一時停止: サービスが一時停止します。<br /><br /> null にすることはできません。|  
|process_id|**int**|サービスのプロセス ID。 null にすることはできません。|  
|last_startup_time|**datetimeoffset(7)**|サービスが最後に開始された日時。 NULL 値が許可されます。|  
|service_account|**nvarchar (256)**|サービスを管理するために承認されているアカウント。 このアカウントでは、サービスの開始や停止、またはサービス プロパティの変更が可能です。 null にすることはできません。|  
|filename|**nvarchar (256)**|サービス実行可能ファイルのパスおよびファイル名。 null にすることはできません。|  
|is_clustered|**nvarchar(1)**|サービスがクラスター サーバーのリソースとしてインストールされているかどうかが表示されます。 null にすることはできません。|  
|cluster_nodename|**nvarchar (256)**|サービスがインストールされているクラスター ノードの名前。 NULL 値が許可されます。|
|instant_file_initialization_enabled|**nvarchar(1)**|ファイルの瞬時初期化が有効になっているかどうかを指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]サービス。<br /><br />Y = サービスのファイルの瞬時初期化を有効にします。<br /><br />N = サービスのファイルの瞬時初期化が無効になっています。<br /><br /> NULL 値が許可されます。<br /><br /> **注:** SQL Server エージェントなどの他のサービスには適用されません。<br /><br /> **適用されます:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降[!INCLUDE[sssql11](../../includes/sssql11-md.md)]SP4、および[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて SP1 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。|  

## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.dm_server_registry &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
