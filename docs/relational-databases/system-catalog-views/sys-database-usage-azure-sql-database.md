---
description: sys.database_usage (Azure SQL データベース)
title: sys.database_usage (Azure SQL Database) |Microsoft Docs
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
monikerRange: = azuresqldb-current
ms.openlocfilehash: e80549106907d042a16197b3ecaf4d6b2dd3f6c7
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475203"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL データベース)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **注: これは Azure SQL Database V11 にのみ適用されます。**  
  
 サーバー上のデータベースの数、種類、および期間を一覧表示し [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ます。  
  
 **Sys.database_usage** ビューには、次の列があります。  
  
|列名|説明|  
|-----------------|-----------------|  
|time|使用状況イベントが発生した日付。|  
|sku|データベースのサービス階層の種類: **Web**、 **Business**、 **Basic**、 **Standard**、 **Premium**|  
|数量|その日に存在した、SKU の種類のデータベースの最大数。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューへの読み取り専用アクセスは、 **master** データベースに接続する権限を持つすべてのユーザーが使用できます。  
  
## <a name="remarks"></a>解説  
 **Sys.database_usage** ビューでは、サブスクリプションの日ごとに1つの行が返されます。  
  
## <a name="see-also"></a>参照  
 [SQL Database の料金詳細](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Azure SQL データベースのアカウントと課金](/previous-versions/azure/ee621788(v=azure.100))  
  
