---
title: "sys.database_mirroring_witnesses (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_witnesses
- sys.database_mirroring_witnesses_TSQL
- database_mirroring_witnesses
- database_mirroring_witnesses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_witnesses catalog view
- witness [SQL Server], sys.database_mirroring_witnesses catalog view
ms.assetid: 0dd5b794-733b-4a3c-b5a4-62f9f1f0f22d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ce23f7d9f763bf08842a1f121c881fb5fbdcee0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="database-mirroring-witness-catalog-views---sysdatabasemirroringwitnesses"></a>データベース ミラーリング監視サーバーのカタログ ビューの sys.database_mirroring_witnesses
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  ミラーリング監視サーバーのロールごとに 1 行のデータを格納します。このロールは、データベース ミラーリング パートナーシップで 1 台のサーバーに与えられるロールです。 
  
  データベース ミラーリング セッションで、自動フェールオーバーを行うには、ミラーリング監視サーバーが必要です。 ミラーリング監視サーバーは、プリンシパル サーバーおよびミラー サーバーとは別のコンピューター上にあるのが理想的です。 ミラーリング監視サーバーでは、データベースが提供される代わりに プリンシパル サーバーとミラー サーバーの状態が監視され、 プリンシパル サーバーで障害が発生した場合はミラーリング監視サーバーへの自動フェールオーバーが開始されます。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|データベース ミラーリング セッションにおける、データベースの 2 つのコピーに関する名前。|  
|**principal_server_name**|**sysname**|現在データベースのコピーがプリンシパル データベースとなっているパートナー サーバーの名前。|  
|**mirror_server_name**|**sysname**|現在データベースのコピーがミラー データベースとなっているパートナー サーバーの名前。|  
|**safety_level**|**tinyint**|ミラー データベースの更新におけるトランザクションの安全性の設定。<br /><br /> 0 = 状態不明<br /><br /> 1 = オフ (非同期)<br /><br /> 2 = 完全 (同期)<br /><br /> 自動フェールオーバーに対してミラーリング監視サーバーを使用する場合は、トランザクションの安全性が「完全」であること必要です。また、「完全」は既定の設定になっています。|  
|**safety_level_desc**|**nvarchar(60)**|ミラー データベースの更新に関する安全性の保証についての説明。<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL|  
|**safety_sequence_number**|**int**|更新シーケンス番号の変更を**safety_level**です。|  
|**role_sequence_number**|**int**|ミラーリング パートナーに与えられているプリンシパル ロールまたはミラー ロールに変更があった場合の更新シーケンス番号。|  
|**mirroring_guid**|**uniqueidentifier**|ミラーリング パートナーシップの識別子。|  
|**family_guid**|**uniqueidentifier**|データベースのバックアップ ファミリの識別子。 一致する復元状態を検出するために使用します。|  
|**is_suspended**|**bit**|データベース ミラーリングが一時中断していることを示す値。|  
|**is_suspended_sequence_number**|**int**|設定のシーケンス番号**is_suspended**です。|  
|**partner_sync_state**|**tinyint**|ミラーリング セッションの同期状態 :<br /><br /> 5 = パートナーが同期されています。 フェールオーバーできる可能性があります。 フェールオーバーでは、「要件については[ロール切り替えセッション中のデータベース ミラーリング &#40;SQL Server &#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).<br /><br /> 6 = パートナーが同期されていません。 現在フェールオーバーはできません。|  
|**partner_sync_state_desc**|**nvarchar(60)**|ミラーリング セッションの同期状態の説明 :<br /><br /> SYNCHRONIZED<br /><br /> UNSYNCHRONIZED|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリング監視サーバー](../../database-engine/database-mirroring/database-mirroring-witness.md)   
 [sys.database_mirroring &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
