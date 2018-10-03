---
title: dbo.sysjobs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7735873fcad0447099c97171a940d570354552d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796030"
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによる実行が予定されているジョブに関する情報を格納します。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの一意な ID。|  
|**originating_server_id**|**int**|ジョブを実行したサーバーの ID。|  
|**name**|**sysname**|ジョブの名前。|  
|**enabled**|**tinyint**|ジョブが実行可能かどうか。|  
|**description**|**nvarchar(512)**|ジョブの説明。|  
|**start_step_id**|**int**|実行を開始するジョブ ステップの ID。|  
|**category_id**|**int**|ジョブ カテゴリの ID。|  
|**owner_sid**|**varbinary(85)**|ジョブ所有者のセキュリティ識別番号 (SID)。|  
|**notify_level_eventlog**|**int**|**ビットマスク**示すどのような場合は、Microsoft Windows アプリケーション ログに、通知イベントが記録する必要があります。<br /><br /> **0** = なし<br /><br /> **1**ジョブ成功時の =<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_level_email**|**int**|どのような場合に、ジョブの完了時に通知電子メールを送信するかを示すビットマスク。<br /><br /> **0** = なし<br /><br /> **1**ジョブ成功時の =<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_level_netsend**|**int**|どのような場合に、ジョブの完了時にネットワーク メッセージを送信するかを示すビットマスク。<br /><br /> **0** = なし<br /><br /> **1**ジョブ成功時の =<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_level_page**|**int**|どのような場合に、ジョブの完了時にポケットベルのメッセージを送信するのかを示すビットマスク。<br /><br /> **0** = なし<br /><br /> **1**ジョブ成功時の =<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_email_operator_id**|**int**|通知先のオペレーターの電子メール名。|  
|**notify_netsend_operator_id**|**int**|ネットワーク メッセージを送信するときに使用されるコンピューターまたはユーザーの ID。|  
|**notify_page_operator_id**|**int**|ポケットベルのメッセージを送信するときに使用されるコンピューターまたはユーザーの ID。|  
|**delete_level**|**int**|**ビットマスク**示すジョブの完了時にどのような場合、ジョブを削除する必要があります。<br /><br /> **0** = なし<br /><br /> **1**ジョブ成功時の =<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**date_created**|**datetime**|ジョブを作成した日付。|  
|**date_modified**|**datetime**|ジョブを最後に変更した日付。|  
|**version_number**|**int**|ジョブのバージョン。|  
  
  
