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
ms.openlocfilehash: 94bd2c31e8caec8c33f9dd3eb7b3badfa235d60b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752635"
---
# <a name="msrepl_version-transact-sql"></a>MSrepl_version (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
  
  
