---
title: MSrepl_version (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_version
- MSrepl_version_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_version system table
ms.assetid: c1330f03-940b-4564-ac42-6030c6e21173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3176da347195e7410c5062a442c7f1d5b5881791
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889473"
---
# <a name="msrepl_version-transact-sql"></a>MSrepl_version (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSrepl_version**テーブルには、現在のバージョンのレプリケーションがインストールされている1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**major_version**|**int**|ディストリビューション データベースのメジャー バージョン番号。|  
|**minor_version**|**int**|ディストリビューション データベースのマイナー バージョン番号。|  
|**改定**|**int**|リビジョン番号。|  
|**db_existed**|**bit**|**Sp_adddistributiondb**が呼び出される前に、ディストリビューションデータベースが存在するかどうかを示します。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
