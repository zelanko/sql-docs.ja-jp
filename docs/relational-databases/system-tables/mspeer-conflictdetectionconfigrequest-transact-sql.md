---
title: MSpeer_conflictdetectionconfigrequest (Transact-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_conflictdetectionconfigrequest_TSQL
- MSpeer_conflictdetectionconfigrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigurerequest
ms.assetid: 83afa0ca-707e-4468-a888-228268ed4e10
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2ecd4ef541422b1241689f17ab5c4f1a53bcc0a6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68115038"
---
# <a name="mspeer_conflictdetectionconfigrequest-transact-sql"></a>MSpeer_conflictdetectionconfigrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ピア ツー ピア レプリケーションで、パブリケーションに対するトポロジ全体の構成要求を追跡するために使用されます。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**int**|競合構成要求を識別します。 Request_id 列に[MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)はこの値を使用します。|  
|publication|**sysname**|競合構成要求が発行されたパブリケーションの名前です。|  
|sent_date|**datetime**|日付と競合構成要求が開始された時刻。|  
|timeout|**int**|すべてのピアから競合情報が返されるのをプロシージャが待機する時間です。|  
|modified_date|**datetime**|日付と時刻のフェーズが完了したこと。|  
|progress_phase|**nvarchar(32)**|次の値のいずれかを使用して、処理の現在のフェーズを識別します。<br /><br /> Started<br /><br /> トポロジの調査<br /><br /> 状態の収集<br /><br /> 収集された状態|  
|phase_timed_out|**bit**|現在のフェーズがタイムアウトしているかどうかを示します。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
