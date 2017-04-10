---
title: "Audit Fulltext イベント クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95e4c5fd-e16f-446e-b42b-105495a8f39a
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Audit Fulltext イベント クラス
  **Audit Fulltext** イベント クラスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がフルテキスト フィルター デーモン プロセスに接続して通信する際に発生します。  
  
## Audit Fulltext イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**[エラー]**|**int**|(このイベントによってエラーが報告された場合) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー番号。|31|はい|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|不可|  
|**EventSubClass**|**int**|ログインに使用される接続の種類。 1 = プールされていない。2 = プールされた。|21|はい|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|はい|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|可|  
|**成功**|**int**|1 = 成功。 0 = 失敗。 たとえば、値 1 は権限チェックの成功を示し、値 0 は失敗を示します。|23|可|  
|**TargetLoginName**|**int**|新しいログインの追加など、ログインを対象とする操作で、対象となるログインの名前。|42|可|  
|**TargetLoginSid**|**int**|新しいログインの追加など、ログインを対象とする操作で、対象となるログインのセキュリティ識別番号 (SID)。|43|可|  
|**TextData**|**ntext**|フルテキスト イベントに関するテキスト情報。 通常、このフィールドは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスとフルテキスト フィルター デーモン プロセス間の接続情報を示します。|1|はい|  
  
## 参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  