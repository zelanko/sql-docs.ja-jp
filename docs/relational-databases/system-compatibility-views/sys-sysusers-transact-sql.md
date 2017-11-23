---
title: "sys.sysusers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs: TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f4c732149e7b7b2aaeb92a6d8930b3f3ecfae388
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  ごとに 1 つの行を含む[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows ユーザー、Windows グループ、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース内のロール。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**uid**|**smallint**|このデータベース内で一意なユーザー ID です。<br /><br /> 1 = データベースの所有者。<br /><br /> ユーザーとロールの数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**ステータス**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|このデータベース内で一意なユーザー名またはグループ名です。|  
|**sid**|**varbinary (85)**|このエントリのセキュリティ識別子です。|  
|**ロール**|**varbinary(2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|アカウントが追加された日付です。|  
|**updatedate**|**datetime**|アカウントが前回変更された日付です。|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> ユーザーとロールの数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**パスワード**|**varbinary (256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**gid**|**smallint**|このユーザーが所属するグループ ID です。 場合**uid**と同じ**gid**、このエントリは、グループを定義します。 グループとユーザーを合計した数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**environ**|**varchar (255)**|予約されています。|  
|**hasdbaccess**|**int**|1 = アカウントはデータベースにアクセスできます。|  
|**islogin**|**int**|1 = アカウントは Windows グループ、Windows ユーザー、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン アカウントを持つユーザーです。|  
|**isntname**|**int**|1 = アカウントは、Windows グループまたは Windows ユーザーです。|  
|**isntgroup**|**int**|1 = アカウントは Windows グループです。|  
|**isntuser**|**int**|1 = アカウントは Windows ユーザーです。|  
|**issqluser**|**int**|1 = アカウントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーです。|  
|**isaliased**|**int**|1 = アカウントは別のユーザーの別名です。|  
|**issqlrole**|**int**|1 = アカウントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロールです。|  
|**isapprole**|**int**|1 = アカウントはアプリケーション ロールです。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
