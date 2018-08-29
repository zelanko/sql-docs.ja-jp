---
title: sys.dm_os_stacks (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2b1c72f0fe51052cefc366b7b7f81444e77e94de
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43104618"
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  この動的管理ビューは内部で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以下を実行します。  
  
-   未処理の割り当てなど、デバッグ データの追跡  
  
-   想定または検証で使用されるロジック[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特定の呼び出しが行われたことを想定の場所でのコンポーネント。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|このスタック割り当ての一意なアドレス。 NULL 値は許可されません。|  
|**frame_index**|**int**|各行は、関数を表す特定のフレーム インデックスを使用して昇順で並べ替えられる場合、呼び出す**stack_address**、完全なコール スタックを返します。 NULL 値は許可されません。|  
|**frame_address**|**varbinary(8)**|関数呼び出しのアドレス。 NULL 値は許可されません。|  
  
## <a name="remarks"></a>コメント  
 **sys.dm_os_stacks**サーバーとその他のコンポーネントのシンボル情報を正しく表示するサーバー上に存在できる必要があります。  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   


## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
