---
title: sys.database_usage (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f17e34de7c230b111652ea57a3baa072a442a6a5
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656741"
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **注意: Azure SQL Database V11 にのみ適用します。**  
  
 上の数、型、およびデータベースの期間を一覧表示、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーです。  
  
 **Sys.database_usage**ビューには、次の列が含まれています。  
  
|列名|説明|  
|-----------------|-----------------|  
|time|使用状況イベントが発生した日付。|  
|sku|データベースのサービス層の種類: **Web**、**ビジネス**、**基本的な**、**標準**、 **Premium**|  
|quantity|その日に存在していた SKU の種類のデータベースの最大数。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューに読み取り専用のアクセスに接続するアクセス許可を持つすべてのユーザーには、**マスター**データベース。  
  
## <a name="remarks"></a>コメント  
 **Sys.database_usage**ビューは、サブスクリプションの各日の 1 つの行を返します。  
  
## <a name="see-also"></a>参照  
 [SQL Database の料金詳細](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [アカウントと Windows Azure SQL Database での課金](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
