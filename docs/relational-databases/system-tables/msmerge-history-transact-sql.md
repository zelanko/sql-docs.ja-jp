---
title: MSmerge_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bde1a345f03eb93dbc02b630df6889efe9b8568
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737580"
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_history**テーブルに履歴行以前のマージ エージェント ジョブ セッションの結果の詳細な説明にはが含まれています。 このテーブルは、エージェントの出力行ごとに 1 行のデータを保持します。 このテーブルは、ディストリビューション データベースと各サブスクリプション データベースで使用されます。 ディストリビューション データベースでは、ディストリビューターを使用するすべてのマージ パブリケーションとマージ サブスクリプションの履歴がこのテーブルに格納されます。 各サブスクリプション データベースでは、サブスクライバーがサブスクライブされるパブリケーションの履歴がこのテーブルに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|マージ エージェント ジョブの ID です。|  
|**agent_id**|**int**|マージ エージェントの ID です。|  
|**comments**|**nvarchar (255)**|メッセージ テキストです。|  
|**error_id**|**int**|エラーの ID、 [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md)システム テーブル。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
|**updatable_row**|**bit**|設定**1**履歴行を上書きできる場合。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
