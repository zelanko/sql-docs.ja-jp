---
title: sp_helpxactsetjob (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords:
- sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bcea94b8d7e83d74ee9295658943ac41c619628
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oracle パブリッシャーに対する Xactset ジョブの情報を表示します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>引数  
 [**@publisher** =] **'***パブリッシャー***'**  
 ジョブが属する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**仕事番号**|**int**|Oracle のジョブ番号です。|  
|**lastdate**|**varchar(22)**|ジョブが最後に実行された日付です。|  
|**thisdate**|**varchar(22)**|変更時刻です。|  
|**nextdate**|**varchar(22)**|ジョブを次に実行する日付です。|  
|**分割**|**varchar (1)**|ジョブが壊れているかどうかを示すフラグです。|  
|**間隔**|**varchar(200)**|ジョブの間隔です。|  
|**エラー**|**int**|ジョブの失敗の回数です。|  
|**xactsetjobwhat**|**varchar(200)**|ジョブによって実行されるプロシージャの名前です。|  
|**xactsetjob**|**varchar (1)**|ジョブの状態です。次のいずれかになります。<br /><br /> **1** -ジョブが有効にします。<br /><br /> **0** -ジョブが無効にします。|  
|**xactsetlonginterval**|**int**|ジョブの長い間隔です。|  
|**xactsetlongthreshold**|**int**|ジョブの長いしきい値です。|  
|**xactsetshortinterval**|**int**|ジョブの短い間隔です。|  
|**xactsetshortthreshold**|**int**|ジョブの短いしきい値です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpxactsetjob**はスナップショット レプリケーションおよび Oracle パブリッシャーに対してトランザクション レプリケーションで使用します。  
  
 **sp_helpxactsetjob**常に、パブリッシャーで Xactset ジョブ (HREPL_XactSetJob) の現在の設定を返します。 Xactset ジョブが現在ジョブ キューに入っている場合は、Oracle パブリッシャーにおいて、管理者アカウントで作成された USER_JOB データ辞書ビューから、ジョブの属性も返します。  
  
## <a name="permissions"></a>権限  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_helpxactsetjob**です。  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシャー用のトランザクション セット ジョブの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
