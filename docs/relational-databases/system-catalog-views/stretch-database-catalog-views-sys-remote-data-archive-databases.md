---
title: sys.remote_data_archive_databases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0dbf0566239b6434bb25c707ff2bb3142dbc2b15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607220"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>カタログ ビューでの Stretch Database sys.remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch が有効なローカルのデータベースからデータを格納するリモートのデータベースごとに 1 つの行が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|自動生成されたローカルの識別子、リモート データベース。|  
|**remote_database_name**|**sysname**|リモートのデータベースの名前。|  
|**data_source_id**|**int**|リモート サーバーに接続するために使用するデータ ソース|  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
