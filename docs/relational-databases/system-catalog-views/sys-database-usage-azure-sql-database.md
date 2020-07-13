---
title: database_usage (Azure SQL Database) |Microsoft Docs
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 4b68fbc20fb220af49036890edc2b67d1a4f7b65
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724682"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL データベース)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **注: これは Azure SQL Database V11 にのみ適用されます。**  
  
 サーバー上のデータベースの数、種類、および期間を一覧表示し [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ます。  
  
 **Database_usage**ビューには、次の列が含まれています。  
  
|列名|説明|  
|-----------------|-----------------|  
|time|使用状況イベントが発生した日付。|  
|sku|データベースのサービス階層の種類: **Web**、 **Business**、 **Basic**、 **Standard**、 **Premium**|  
|数量|その日に存在した、SKU の種類のデータベースの最大数。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューへの読み取り専用アクセスは、 **master**データベースに接続する権限を持つすべてのユーザーが使用できます。  
  
## <a name="remarks"></a>Remarks  
 **Database_usage**ビューでは、サブスクリプションの日ごとに1つの行が返されます。  
  
## <a name="see-also"></a>関連項目  
 [SQL Database の料金詳細](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Azure SQL データベースのアカウントと課金](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
