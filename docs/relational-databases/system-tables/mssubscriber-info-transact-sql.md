---
title: MSsubscriber_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 454b3504db5c159135d257229bb24581a254cd77
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889385"
---
# <a name="mssubscriber_info-transact-sql"></a>MSsubscriber_info (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSsubscriber_info**テーブルには、ローカルディストリビューターからプッシュされたサブスクリプションのパブリッシャー/サブスクライバーのペアごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
 **メモ**このシステムテーブルは非推奨とされており、以前のバージョンのをサポートするために保持されてい [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|パブリッシャーの名前です。|  
|**サブスクライバ**|**sysname**|サブスクライバーの名前です。|  
|**type**|**tinyint**|サブスクライバーの種類:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバー。<br /><br /> **1** = ODBC データソース。|  
|**ログイン**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログインです。 サブスクライバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードで追加されている場合は、暗号化形式で格納されます。|  
|**password**|**nvarchar (524)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワードです。 サブスクライバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードで追加されている場合は、暗号化形式で格納されます。|  
|**description**|**nvarchar(255)**|サブスクライバーの説明。|  
|**security_mode**|**int**|実装されているセキュリティ モードです。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
