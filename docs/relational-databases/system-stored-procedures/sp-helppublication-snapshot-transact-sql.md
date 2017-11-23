---
title: "sp_helppublication_snapshot (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_helppublication_snapshot
- sp_helppublication_snapshot_TSQL
helpviewer_keywords: sp_helppublication_snapshot
ms.assetid: 97b4a7ae-40a5-4328-88f1-ff5d105bbb34
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 823e243240143e04902e86c03f81882ed517679e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelppublicationsnapshot-transact-sql"></a>sp_helppublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたパブリケーションのスナップショット エージェントに関する情報を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helppublication_snapshot [ @publication = ] 'publication'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@publisher =** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*にアーティクルを追加するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|スナップショット エージェントの ID です。|  
|**name**|**nvarchar (100)**|スナップショット エージェント名です。|  
|**publisher_security_mode**|**smallint**|次のいずれかと、パブリッシャーに接続するときに、エージェントで使用されるセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証です。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログイン。|  
|**publisher_password**|**nvarchar (524)**|セキュリティ上の理由の値 **\* \* \* \* \* \* \* \* \* \*** は常に返されます。|  
|**job_id**|**uniqueidentifier**|エージェント ジョブの一意な ID。|  
|**job_login**|**nvarchar(512)**|形式で返される、スナップショット エージェントを実行する Windows アカウントは、*ドメイン*\\*username*です。|  
|**job_password**|**sysname**|セキュリティ上の理由の値 **\* \* \* \* \* \* \* \* \* \*** は常に返されます。|  
|**schedule_name**|**sysname**|このエージェント ジョブに使用されるスケジュールの名前です。|  
|**frequency_type**|**int**|スケジュールに組み込まれているエージェントの実行の頻度。次のいずれかの値になります。<br /><br /> **1** = 1 回<br /><br /> **2** = 要求時<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32** = 月単位<br /><br /> **64**自動開始を =<br /><br /> **128** = 定期的|  
|**frequency_interval**|**int**|エージェントの実行日。次のいずれかの値になります。<br /><br /> **1**日曜日を =<br /><br /> **2**月曜日を =<br /><br /> **3** = 火曜日<br /><br /> **4** = 水曜日<br /><br /> **5** = 木曜日<br /><br /> **6** = 金曜日<br /><br /> **7** = 土曜日<br /><br /> **8** = 日<br /><br /> **9** = 平日<br /><br /> **10**週末の曜日を =|  
|**frequency_subday_type**|**int**|エージェントを実行時にどのくらいの頻度を定義する型は、 *frequency_type*は**4** (毎日)、これらの値のいずれかを指定できます。<br /><br /> **1** = 指定した時刻<br /><br /> **2**秒を =<br /><br /> **4**分を =<br /><br /> **8**時間を =|  
|**frequency_subday_interval**|**int**|間隔数*frequency_subday_type*エージェントのスケジュールされた実行の間で発生します。|  
|**frequency_relative_interval**|**int**|特定の月にエージェントを実行する週とき*frequency_type*は**32** (月単位)、これらの値のいずれかを指定できます。<br /><br /> **1**最初を =<br /><br /> **2**秒を =<br /><br /> **4**サードパーティを =<br /><br /> **8**第 4 を =<br /><br /> **16**最後を =|  
|**frequency_recurrence_factor**|**int**|週または月を単位とした、エージェントの予定実行間隔。|  
|**active_start_date**|**int**|エージェントの最初の実行予定日。日付の形式は YYYYMMDD です。|  
|**active_end_date**|**int**|エージェントの最後の実行予定日。日付の形式は YYYYMMDD です。|  
|**active_start_time**|**int**|エージェントの最初の実行予定時刻。時刻の形式は HHMMSS です。|  
|**active_end_time**|**int**|エージェントの最後の実行予定時刻。時刻の形式は HHMMSS です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_help_publication_snapshot**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**のメンバーまたはパブリッシャーの固定サーバー ロール、 **db_owner** 、パブリケーション データベースの固定データベース ロールが実行できる**sp_help_publication_snapshot**.  
  
## <a name="see-also"></a>参照  
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication_snapshot &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication_snapshot &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_dropmergepublication &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_droppublication &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)  
  
  
