---
title: sys.database_usage (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
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
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 56e09dc849223832bbd65c09c16e1f6aeed09e17
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716572"
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **注:これは、Azure SQL Database V11 にのみ適用されます。**  
  
 上の数、種類、およびデータベースの期間を一覧表示、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。  
  
 **Sys.database_usage**ビューには、次の列が含まれています。  
  
|列名|説明|  
|-----------------|-----------------|  
|time|使用状況イベントが発生した日付。|  
|sku|データベースのサービス層の種類:**Web**、**ビジネス**、**基本的な**、**標準**、 **Premium**|  
|quantity|その日に存在していた SKU の種類のデータベースの最大数。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューに読み取り専用のアクセスに接続するアクセス許可を持つすべてのユーザーには、**マスター**データベース。  
  
## <a name="remarks"></a>コメント  
 **Sys.database_usage**ビューは、サブスクリプションの各日の 1 つの行を返します。  
  
## <a name="see-also"></a>関連項目  
 [SQL Database の料金詳細](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [アカウントと Windows Azure SQL Database での課金](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
