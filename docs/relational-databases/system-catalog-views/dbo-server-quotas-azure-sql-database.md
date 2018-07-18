---
title: dbo.server_quotas (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ada6f943e451e6c468adaed27bfe4618407d2dc7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38029670"
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **重要!!** これに適用されます **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 のみです。**  
>   
>  この機能は現在プレビュー状態です。 この機能は将来のリリースで変更または削除される可能性があるので、この機能の特定の実装に依存する設定は行わないでください。  
  
 サーバーで利用できるデータベース クォータの種類を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|サーバーのクォータの種類。 型**Premium_database**はリソースの予約を持つデータベースに相当します。|  
|quota_value|**int**|サーバーで許可されているクォータの種類の数。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、仮想に接続するアクセス許可を持つすべてのユーザー ロールに使用可能な**マスター**データベース。  
  
## <a name="see-also"></a>参照  
 [Premium データベースの管理](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
