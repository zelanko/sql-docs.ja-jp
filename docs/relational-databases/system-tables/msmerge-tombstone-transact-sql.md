---
title: MSmerge_tombstone (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 24aed42066963852fe7850caaebd54328d53f407
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msmergetombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_tombstone**テーブルは、削除された行に関する情報を格納でき、他のサブスクライバーに反映されるまで削除します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**rowguid**|**uniqueidentifier**|行識別子 (ROWID) です。|  
|**tablenick**|**int**|テーブルのニックネームです。|  
|**type**|**tinyint**|削除のタイプです。<br /><br /> 1 = ユーザー削除です。<br /><br /> 5 = フィルター選択されたパーティションに既に行が属していません。<br /><br /> 6 = システム削除です。|  
|**系列**|**varbinary(249)**|削除されたレコードのバージョンと、削除されたときに認識された更新を示します。 これによって、あるサブスクライバーによって行が削除されているときに、別のサブスクライバーがこれを更新するという競合を、一貫して回避するための規則が定められます。|  
|**生成**|**int**|行が削除されると、割り当てられます。 サブスクライバーが generation 値 N を要求する場合、generation 値 >= N を満たす廃棄標識だけが送信されます。|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|削除された行が属する論理レコードを識別します。|  
|**logical_record_lineage**|**Varbinary(501)**|この行が属する論理レコードについて削除の履歴を管理するために使用するサブスクライバーのニックネームとバージョン番号のペアです。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
