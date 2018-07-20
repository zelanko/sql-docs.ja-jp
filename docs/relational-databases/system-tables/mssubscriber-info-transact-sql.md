---
title: MSsubscriber_info (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e8057a5bb1f9e6d6c59402005ea6e19e3f0e89d1
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101360"
---
# <a name="mssubscriberinfo-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriber_info**テーブルには、ローカル ディストリビューターからサブスクリプションがプッシュされるパブリッシャー/サブスクライバー ペアごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
 **注**このシステム テーブルは非推奨し、以前のバージョンをサポートするために保持されている[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前。|  
|**type**|**tinyint**|サブスクライバーの種類:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。<br /><br /> **1** = ODBC データ ソース。|  
|**login**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログインです。 サブスクライバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードで追加されている場合は、暗号化形式で格納されます。|  
|**password**|**nvarchar (524)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワードです。 サブスクライバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードで追加されている場合は、暗号化形式で格納されます。|  
|**description**|**nvarchar (255)**|サブスクライバーの説明です。|  
|**security_mode**|**int**|実装されているセキュリティ モードです。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
