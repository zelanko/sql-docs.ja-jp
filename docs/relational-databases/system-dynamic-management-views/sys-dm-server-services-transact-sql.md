---
title: "sys.dm_server_services (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8642cd9036fcaf7835c6dffc01f60817bdaa82bb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL Server に関する情報を返すフルテキスト、および SQL Server エージェント サービスの現在のインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 これらのサービスに関する状態情報を報告するには、この動的管理ビューを使用します。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar (256)**|SQL Server、フルテキスト、または SQL Server エージェント サービスの名前。 null にすることはできません。|  
|startup_type|**int**|サービスの開始モードが表示されます。 使用可能な値とその対応する説明を次に示します。<br /><br /> 0: その他の<br />1: その他の<br />2: 自動<br />3: 手動<br />4: 無効になっています。<br /><br /> NULL 値が許可されます。|  
|startup_desc|**nvarchar (256)**|サービスの開始モードを記述します。 使用可能な値とその対応する説明を次に示します。<br /><br /> その他: その他 (ブート開始)<br />その他: その他 (システム開始)<br />自動: 自動開始<br />[手動]: 要求の開始<br />Disabled: 無効になっています。<br /><br /> null にすることはできません。|  
|ステータス|**int**|サービスの現在の状態を示します。 使用可能な値とその対応する説明を次に示します。<br /><br /> 1: が停止しました<br />2: その他 (開始保留中)<br />3: その他 (停止保留中)<br />4: を実行しています。<br />5: その他の (継続保留中)<br />6: その他 (一時停止保留中の)<br />7: 一時停止<br /><br /> NULL 値が許可されます。|  
|status_desc|**nvarchar (256)**|サービスの現在の状態を記述します。 使用可能な値とその対応する説明を次に示します。<br /><br /> 停止しました。 サービスが停止します。<br />その他 (開始操作保留中): サービスは開始処理中です。<br />その他 (停止操作保留中): サービスは停止処理中です。<br />実行: サービスが実行されます。<br />その他の (継続操作保留中): サービスが保留中の状態。<br />その他 (一時停止保留中の): サービスが一時停止中です。<br />一時停止: サービスが一時停止します。<br /><br /> null にすることはできません。|  
|process_id|**int**|サービスのプロセス ID。 null にすることはできません。|  
|last_startup_time|**datetimeoffset (7)**|サービスが最後に開始された日時。 NULL 値が許可されます。|  
|service_account|**nvarchar (256)**|サービスを管理するために承認されているアカウント。 このアカウントでは、サービスの開始や停止、またはサービス プロパティの変更が可能です。 null にすることはできません。|  
|filename|**nvarchar (256)**|サービス実行可能ファイルのパスおよびファイル名。 null にすることはできません。|  
|is_clustered|**nvarchar(1)**|サービスがクラスター サーバーのリソースとしてインストールされているかどうかが表示されます。 null にすることはできません。|  
|cluster_nodename|**nvarchar (256)**|サービスがインストールされているクラスター ノードの名前。 NULL 値が許可されます。|
|instant_file_initialization_enabled|**nvarchar(1)**|**適用されます: [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 以降[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1**です。<br /><br />SQL Server データベース エンジン サービスのファイルの瞬時初期化が有効になっているかどうかを指定します。 このプロパティは、サービスには適用されません (例: SQL Server エージェント) SQL Server データベース エンジン サービス以外です。 Null 値を許容します。<br /><br />Y = サービスのファイルの瞬時初期化が有効にします。<br /><br />N = ファイルの瞬時初期化は、サービスで無効にします。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.dm_server_registry &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
  
