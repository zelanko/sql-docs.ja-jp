---
title: sys.remote_data_archive_databases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_databases
- sys.remote_data_archive_databases_TSQL
- remote_data_archive_databases
- remote_data_archive_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_databases catalog view
ms.assetid: 25bffb0c-9821-40b4-88cf-75f854891a09
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 74a44e8c3e6b0be026ac716d43b539869345b3b9
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945610"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>カタログ ビューでの Stretch Database sys.remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch が有効なローカル データベースからデータを格納する各リモート データベースの 1 つの行が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|自動生成されたローカルの識別子、リモート データベース。|  
|**remote_database_name**|**sysname**|リモート データベースの名前。|  
|**data_source_id**|**int**|リモート サーバーへの接続に使用するデータ ソース|  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
