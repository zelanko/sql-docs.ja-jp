---
title: dbo.sysjobstepslogs (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a975f79f4b0adc3c752e2674d847eed02bff81e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべてのジョブ ステップ ログを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルにジョブ ステップの出力を書き込むように構成されているエージェントのジョブ ステップ。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|ジョブ ステップ ログの ID。|  
|**log**|**nvarchar(max)**|ジョブ ステップ ログの内容。|  
|**date_created**|**datetime**|ジョブ ステップ ログが作成された日時。|  
|**date_modified**|**datetime**|ジョブ ステップ ログが最後に変更された日時。|  
|**log_size**|**int**|ジョブ ステップ ログのサイズ (バイト単位)。|  
|**step_uid**|**uniqueidentifier**|ジョブ ステップの一意識別子。|  
  
## <a name="see-also"></a>参照  
 [sp_help_jobsteplog &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
