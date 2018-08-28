---
title: Background Job Error イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 53a5f6acd5f2b74d10aa2d40957e52ebc16abce9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43064275"
---
# <a name="background-job-error-event-class"></a>Background Job Error イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **Background Job Error** イベント クラスは、バックグラウンド ジョブが異常終了したときに発生します。 このような状況では、システム管理者の注意を喚起する必要性が生じる場合があります。  
  
## <a name="background-job-error-event-class-data-columns"></a>Background Job Error イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ジョブで指定されているデータベースの ID。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|**DatabaseName**|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|[ユーザー アカウント制御]|  
|**Error**|**int**|最後の試行で発生したエラーのエラー番号 (**EventSubClass** が 1 の場合のみ)。|31|[ユーザー アカウント制御]|  
|**EventClass**|**int**|イベントの種類 = 193。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**EventSubClass**|**int**|イベント サブクラスの種類。<br /><br /> 1 = エラーが発生し、バックグラウンド ジョブを中断中です。<br /><br /> 2 = キューがいっぱいなので、バックグラウンド ジョブが削除されました。<br /><br /> 3 = バックグラウンド ジョブからエラーが返されました。|21|[ユーザー アカウント制御]|  
|**IndexID**|**int**|イベントの影響を受けるオブジェクトに付けられたインデックス用の ID。 オブジェクトのインデックス ID を調べるには、 **sysindexes** システム テーブルの **indid** 列を使用します。|24|[ユーザー アカウント制御]|  
|**IntegerData**|**int**|ジョブによって行われた試行回数 (**EventSubClass** が 1 の場合のみ)。|25|[ユーザー アカウント制御]|  
|**IntegerData2**|**int**|ジョブ シーケンス番号。|55|[ユーザー アカウント制御]|  
|**Exchange Spill**|**int**|システムによって割り当てられたオブジェクト ID。|22|[ユーザー アカウント制御]|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|**Severity**|**int**|最後の試行におけるエラーの重要度レベル (**EventSubClass** が 1 の場合のみ)。|20|[ユーザー アカウント制御]|  
|**StartTime**|**datetime**|ジョブが作成された時刻。|14|[ユーザー アカウント制御]|  
|**状態**|**int**|最後の試行におけるエラーの状態 (**EventSubClass** が 1 の場合のみ)。|30|[ユーザー アカウント制御]|  
|**TextData**|**ntext**|イベント サブクラスの値についての説明テキスト。|1|[ユーザー アカウント制御]|  
|**型**|**int**|ジョブの種類。|57|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Auto Stats イベント クラス](../../relational-databases/event-classes/auto-stats-event-class.md)  
  
  
