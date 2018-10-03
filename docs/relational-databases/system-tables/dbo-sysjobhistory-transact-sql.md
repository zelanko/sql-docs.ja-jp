---
title: dbo.sysjobhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1797fb6183863bb0249bd0cda6024d0e95914e82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658810"
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スケジュールされたジョブの実行に関する情報を格納[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。 このテーブルに格納されます、 **msdb**データベース。  
  
> **注:** ジョブ ステップの完了後にのみデータを更新します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|行の一意識別子。|  
|**job_id**|**uniqueidentifier**|ジョブ ID。|  
|**step_id**|**int**|ジョブ ステップの ID。|  
|**step_name**|**sysname**|ステップの名前。|  
|**sql_message_id**|**int**|任意の ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ジョブが失敗したかどうかにエラー メッセージが返されます。|  
|**sql_severity**|**int**|いずれかの重要度[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー。|  
|**message**|**nvarchar (4000)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーのテキスト (存在する場合)。|  
|**run_status**|**int**|ジョブ実行のステータス。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **2** = 再試行<br /><br /> **3** = キャンセル<br /><br /> **4** = 実行中|  
|**run_date**|**int**|ジョブまたはステップが実行を開始した日付。 実行中の場合は、履歴が作成された日付/時刻です。|  
|**run_time**|**int**|ジョブまたはステップが実行を開始した時刻。|  
|**run_duration**|**int**|ジョブまたはステップの実行の経過時間**HHMMSS**形式。|  
|**operator_id_emailed**|**int**|ジョブの終了時に電子メールの通知を受けるオペレーターの ID。|  
|**operator_id_netsent**|**int**|ジョブの終了時に Net Send メッセージの通知を受けるオペレーターの ID。|  
|**operator_id_paged**|**int**|ジョブの終了時にポケットベルの通知を受けるオペレーターの ID。|  
|**retries_attempted**|**int**|ジョブまたはステップの再試行回数。|  
|**server**|**sysname**|ジョブが実行されたサーバー名。|  
  
  ## <a name="example"></a>例
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリに変換されます、 **run_time の期限**と**run_duration**列以上のユーザー フレンドリな形式にします。  スクリプトを実行[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。
 
 ```sql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
