---
title: "MSmerge_history (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bec33dfc63fb25943be93ff79c2a15136473c06a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_history**テーブルに履歴行以前のマージ エージェント ジョブ セッションの結果の詳細な説明にはが含まれています。 このテーブルは、エージェントの出力行ごとに 1 行のデータを保持します。 このテーブルは、ディストリビューション データベースと各サブスクリプション データベースで使用されます。 ディストリビューション データベースでは、ディストリビューターを使用するすべてのマージ パブリケーションとマージ サブスクリプションの履歴がこのテーブルに格納されます。 各サブスクリプション データベースでは、サブスクライバーがサブスクライブされるパブリケーションの履歴がこのテーブルに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|マージ エージェント ジョブの ID です。|  
|**agent_id**|**int**|マージ エージェントの ID です。|  
|**コメント**|**nvarchar (255)**|メッセージ テキストです。|  
|**error_id**|**int**|エラーの ID、 [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md)システム テーブル。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
|**updatable_row**|**bit**|設定**1**履歴行を上書きできる場合です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
