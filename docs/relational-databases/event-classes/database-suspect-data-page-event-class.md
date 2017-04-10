---
title: "Database Suspect Data Page イベント クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント通知 [SQL Server], データベース ミラーリング"
  - "suspect_pages システム テーブル"
  - "データベース ミラーリング [SQL Server], イベント通知"
  - "Database Suspect Data Page イベント クラス"
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Database Suspect Data Page イベント クラス
  **Database Suspect Data Page** イベント クラスは、[msdb](../../relational-databases/databases/msdb-database.md) の [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md) テーブルにページがいつ追加されたかを示します。 このイベント クラスは、問題があると思われるページの発生を監視するトレースに含めます。  
  
> [!NOTE]  
>  このイベントは、**suspect_pages** テーブルへの対応する行の挿入とは非同期に発行されます。 したがって、このイベントを受信待ちするジョブでは、対応する **suspect_pages** エントリを直ちに見つけることができない場合があります。  
  
 **Database Suspect Data Page** イベント クラスをトレースに含めても、相対的なオーバーヘッドは低くなります。 問題があると思われるページ数が増えた場合 (ディスク ドライブで問題が発生した場合など) はオーバーヘッドが大きくなる可能性があります。  
  
## Database Suspect Data Page イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|問題があると思われるページのイベントが発生したデータベースの ID。 これは **suspect_pages** テーブルの **database_id** 列と同じです。|3|可|  
|**EventClass**|**int**|イベントの種類は 213 です。|27|いいえ|  
|**EventSequence**|**int**|バッチ内のイベント クラスのシーケンス。|51|いいえ|  
|**SPID**|**int**|問題があると思われるページが発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] タスクの ID。|12|はい|  
|**StartTime**|**datetime**|イベントが発生した時刻。|14|可|  
|**ObjectID**|**int**|問題があると思われるページを格納しているデータベース ファイルの ID。 これは **suspect_pages** テーブルの **file_id** 列と同じです。|22|可|  
|**ObjectID2**|**int**|ファイル内の問題があると思われるページの ID。 これは **suspect_pages** テーブルの **page_id** 列と同じです。|56|はい|  
|**[エラー]**|**int**|発生したエラーの種類。 この値は、**suspect_pages** テーブルのページの **event_type** 値と同じです。|31|はい|  
  
## 参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  