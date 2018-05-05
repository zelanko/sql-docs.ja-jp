---
title: MSmerge_replinfo (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MSmerge_replinfo_TSQL
- MSmerge_replinfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_replinfo system table
ms.assetid: b0924094-c0cc-49c1-869a-65be0d0465a0
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 44bd1de5c31f43c56e2fe7cb90bfe8e6585ad45d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="msmergereplinfo-transact-sql"></a>MSmerge_replinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_replinfo**テーブルには、サブスクリプションごとに 1 つの行が含まれています。 このテーブルは、サブスクリプションに関する情報を追跡します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**repid**|**uniqueidentifier**|レプリカの一意な ID。|  
|**use_interactive_resolver**|**bit**|調整時にインタラクティブ競合回避モジュールを使用するかどうかを指定します。<br /><br /> **0** do = インタラクティブ競合回避モジュールを使用します。<br /><br /> **1** = インタラクティブ競合回避モジュールを使用します。|  
|**validation_level**|**int**|サブスクリプションに対して実行する検証の種類。 指定される検証レベルは次のいずれかの値になります。<br /><br /> **0** = 検証なし。<br /><br /> **1**行数のみの検証を = です。<br /><br /> **2** = 行数とチェックサムの検証。<br /><br /> **3** = 行数とバイナリ チェックサムの検証。|  
|**resync_gen**|**bigint**|サブスクリプションの再同期化で使用される世代番号。 値**– 1**サブスクリプションが再同期にマークされていないことを示します。|  
|**login_name**|**sysname**|サブスクリプションを作成したユーザーの名前。|  
|**ホスト名**|**sysname**|サブスクリプションのパーティションの生成時に、パラメーター化された行フィルターで使用される値。|  
|**merge_jobid**|**binary(16)**|サブスクリプションのマージ ジョブ ID。|  
|**sync_info**|**int**|内部使用のみ。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
