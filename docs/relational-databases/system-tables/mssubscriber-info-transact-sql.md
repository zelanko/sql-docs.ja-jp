---
title: "MSsubscriber_info (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: acbbf203509f1d2ddd4c3604e8cfce8067132d76
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriberinfo-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriber_info**テーブルには、プッシュ サブスクリプションされる、ローカル ディストリビューターからパブリッシャー/サブスクライバーのペアごとに 1 行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
 **注**このシステム テーブルは廃止されており、以前のバージョンをサポートするために保持されている[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前。|  
|**型**|**tinyint**|サブスクライバーの種類:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。<br /><br /> **1** = ODBC データ ソース。|  
|**ログイン**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログインです。 サブスクライバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードで追加されている場合は、暗号化形式で格納されます。|  
|**パスワード**|**nvarchar (524)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワードです。 サブスクライバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードで追加されている場合は、暗号化形式で格納されます。|  
|**説明**|**nvarchar (255)**|サブスクライバーの説明です。|  
|**security_mode**|**int**|実装されているセキュリティ モードです。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
