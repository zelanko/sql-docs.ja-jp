---
title: "Trace File Close イベント クラス | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Trace File Close event class
ms.assetid: 128b7bac-cb64-43e7-ae9b-87b7d2ebb4ef
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ce196fb683057e914891ca2a58f7db9b813f74b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="trace-file-close-event-class"></a>Trace File Close イベント クラス
  **Trace File Close** イベント クラスは、トレース ファイルのロールオーバー中にトレース ファイルが閉じられたことを示します。  
  
## <a name="trace-file-close-event-class-data-columns"></a>Trace File Close イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|イベントの種類 = 150。|27|いいえ|  
|**EventSequence**|**int**|このトレースで起動されたこのイベントの固有のタイムスタンプ。 この数字は、イベントが起動されるたびに単調に増加します。|51|いいえ|  
|**FileName**|**nvarchar**|閉じられているトレース ファイルの論理名。|36|可|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 = システム、NULL = ユーザーです。 このイベント クラスでは、この値は常に 1 です。|60|はい|  
|**LoginName**|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。 このイベント クラスでは、この値は常に "sa" です。|11|可|  
|**Exchange Spill**|**int**|システムによって割り当てられたトレースの ID です。|22|可|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|はい|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
