---
title: "dbo.server_quotas (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 08/02/2016
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs: TSQL
helpviewer_keywords: server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 612f4d0a819c1271ca9b5e8b9fda8f224ae6fbe6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **重要!!** これに当てはまります **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 のみです。**  
>   
>  この機能は現在プレビュー状態です。 この機能は将来のリリースで変更または削除される可能性があるので、この機能の特定の実装に依存する設定は行わないでください。  
  
 サーバーで利用できるデータベース クォータの種類を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|サーバーのクォータの種類。 型**Premium_database**はリソースの予約を含むデータベースに相当します。|  
|quota_value|**int**|サーバーで許可されているクォータの種類の数。|  
  
## <a name="permissions"></a>Permissions  
 このビューは、仮想に接続する権限を持つすべてのユーザー ロールに利用可能な**マスター**データベース。  
  
## <a name="see-also"></a>参照  
 [Premium データベースの管理](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
