---
title: sp_helpxactsetjob (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords:
- sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
author: stevestein
ms.author: sstein
ms.openlocfilehash: db259133a2ddd7ebe18b6d198c0f91e8ffc7b8bf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048188"
---
# <a name="sphelpxactsetjob-transact-sql"></a>sp_helpxactsetjob (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oracle パブリッシャーの Xactset ジョブの情報を表示します。 このストアド プロシージャは、ディストリビューターのすべてのデータベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher** =] **'***パブリッシャー***'**  
 以外の名前を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーは、ジョブが属しています。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**仕事番号**|**int**|Oracle のジョブの数。|  
|**lastdate**|**varchar(22)**|ジョブが実行された最後の日付。|  
|**thisdate**|**varchar(22)**|変更時刻です。|  
|**nextdate**|**varchar(22)**|[次へ] の日付、ジョブの実行です。|  
|**分割**|**varchar (1)**|ジョブが破損している場合を示すフラグします。|  
|**間隔**|**varchar(200)**|ジョブの間隔。|  
|**エラー**|**int**|ジョブの失敗の回数です。|  
|**xactsetjobwhat**|**varchar(200)**|ジョブによって実行されるプロシージャの名前です。|  
|**xactsetjob**|**varchar (1)**|次のいずれかの値と、ジョブの状態です。<br /><br /> **1** -ジョブが有効にします。<br /><br /> **0** -ジョブは無効です。|  
|**xactsetlonginterval**|**int**|ジョブの長い間隔です。|  
|**xactsetlongthreshold**|**int**|ジョブの長いしきい値です。|  
|**xactsetshortinterval**|**int**|ジョブの間隔を短くします。|  
|**xactsetshortthreshold**|**int**|ジョブの短いしきい値です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpxactsetjob**スナップショット レプリケーションと、Oracle パブリッシャーのトランザクション レプリケーションで使用されます。  
  
 **sp_helpxactsetjob**常に、パブリッシャーで Xactset ジョブ (HREPL_XactSetJob) の現在の設定を返します。 Xactset ジョブが現在ジョブ キューである場合は、さらに、Oracle パブリッシャーでの管理者アカウントで作成された USER_JOB データ辞書ビューから、ジョブの属性を返します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_helpxactsetjob**します。  
  
## <a name="see-also"></a>関連項目  
 [Oracle パブリッシャー用のトランザクション セット ジョブの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
