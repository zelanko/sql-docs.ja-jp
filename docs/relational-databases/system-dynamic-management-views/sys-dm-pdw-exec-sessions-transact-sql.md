---
title: sys.dm_pdw_exec_sessions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f8d910bc9b6d85475a937940787aec7a312ef3bf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781170"
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  アプライアンス上に現在または最近開いているすべてのセッションに関する情報を保持します。 これには、セッションごとに 1 行が一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|現在のクエリまたは前回のクエリの id は、(セッションが終了して、終了時に、クエリが実行されている) 場合に実行します。 このビューのキーです。|システム内のすべてのセッション間で一意です。|  
|status|**nvarchar(10)**|現在のセッションでは、セッションがアクティブまたはアイドル状態では現在あるかどうかを識別します。 過去のセッションでは、状態を表示することがありますセッションが終了するか、または (この場合、セッションが強制的に切断されました) を強制終了します。|'ACTIVE'、'CLOSED'、'アイドル状態の'、' 終了 '|  
|request_id|**nvarchar(32)**|現在のクエリまたはクエリの実行の最後の id。|システム内のすべての要求間で一意です。 [なし] が実行されている場合は null です。|  
|security_id|**varbinary(85)**|セッションを実行するプリンシパルのセキュリティ ID。||  
|login_name|**nvarchar(128)**|セッションを実行するプリンシパルのログイン名。|ユーザーの名前付け規則に準拠している任意の文字列。|  
|login_time|**datetime**|日付と時間でユーザーがログインして、このセッションが作成されました。|有効な**datetime**現在時刻より前にします。|  
|query_count|**int**|キャプチャのクエリ/requeststhis セッションの数が作成されてから実行します。|以上の値を 0 にします。|  
|is_transactional|**bit**|セッションが現在のトランザクション内でかしないかどうかをキャプチャします。|自動コミットの場合は 0、1 をトランザクションです。|  
|client_id|**nvarchar (255)**|セッションのクライアント情報をキャプチャします。|任意の有効な文字列。|  
|app_name|**nvarchar (255)**|必要に応じて、接続処理の一部として設定するアプリケーション名の情報をキャプチャします。|任意の有効な文字列。|  
|sql_spid|**int**|SPID の id 番号。 使用して、`session_id`このセッションです。 使用して、`sql_spid`に結合する列**sys.dm_pdw_nodes_exec_sessions**します。<br /><br /> **\*\* 警告\* \*** この列には、閉じている Spid が含まれています。||  
  
 このビューで保持される最大行数は、詳細については、システム ビューの最大値」セクションを参照してください、[最小値と最大値 (SQL Server PDW)](http://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9)トピック。  
  
## <a name="permissions"></a>アクセス許可  
 `VIEW SERVER STATE` アクセス許可が必要です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
