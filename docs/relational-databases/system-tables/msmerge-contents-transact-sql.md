---
title: MSmerge_contents (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0d0dc39424f0636d975195b00580a4ff7649ec64
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82805456"
---
# <a name="msmerge_contents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_contents**テーブルは、パブリッシュされてから現在のデータベースで変更された行ごとに1行のデータを格納します。 このテーブルは、変更された行を確認するために、マージプロセスによって使用されます。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|パブリッシュされたテーブルのニックネーム。|  
|**rowguid**|**uniqueidentifier**|指定された行の行識別子。|  
|**generation**|**bigint**|**Tablenick**および**rowguid**によって識別される行の生成。|  
|**partchangegen**|**bigint**|行がフィルター選択されたパブリケーションに属しているかどうかを変更した可能性のある、最後のデータ変更に関連付けられた生成。|  
|**継承**|**varbinary (501)**|この行に対する変更の履歴を保持するために使用されるサブスクライバーのニックネームとバージョン番号のペアです。|  
|**colvl**|**varbinary (7489)**|列のバージョン情報です。|  
|**記号**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|論理レコード内の対応する各子行について、( **rowguid**によって) **MSmerge_contents**の最上位レベルの親行を識別します。|  
|**logical_record_lineage**|**varbinary (501)**|サブスクライバーのニックネーム。バージョン番号のペアです。論理レコードの最上位の親行に対する変更の履歴を保持するために使用されます。 論理レコードのすべての子行に対しては、この値は NULL です。|  
|**logical_relation_change_gen**|**bigint**|論理レコードの再調整の原因となった最後の変更に関連付けられている生成値。既存の行が論理レコードの内外に移動された場合。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
