---
title: sys.dm_os_stacks (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1536c18204a03ce093c40f1313293ef9d997caa9
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  この動的管理ビューは内部で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を次を行うには。  
  
-   未処理の割り当てなど、デバッグ データの追跡  
  
-   想定または検証によって使用されるロジック[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントが特定の呼び出しが行われたことを想定の場所でのコンポーネントです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|このスタック割り当ての一意なアドレス。 NULL 値は許可されません。|  
|**frame_index**|**int**|各行は、関数を表す、特定のフレーム インデックスを使用して昇順で並べ替えられたときに、呼び出す**stack_address**、完全なコール スタックを返します。 NULL 値は許可されません。|  
|**frame_address**|**varbinary(8)**|関数呼び出しのアドレス。 NULL 値は許可されません。|  
  
## <a name="remarks"></a>解説  
 **sys.dm_os_stacks**サーバーとその他のコンポーネントのシンボル情報を正しく表示するサーバー上に存在する必要があります。  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   


## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
