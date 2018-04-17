---
title: sys.database_scoped_credentials (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 132b61dc36489f0f4b93514e16f804f2745321b4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabasescopedcredentials-transact-sql"></a>sys.database_scoped_credentials (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  データベースごとに 1 つの行を返しますでは、データベース内の資格情報がスコープ設定されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|データベースの ID には、資格情報がスコープ設定されます。 データベース内で一意です。|  
|name|**sysname**|データベースの名前には、資格情報がスコープ設定されます。 データベース内で一意です。|  
|credential_identity|**nvarchar (4000)**|使用する識別情報の名前。 通常は Windows ユーザーです。 一意である必要はありません。|  
|create_date|**datetime**|データベース スコープの資格情報が作成された時刻です。|  
|modify_date|**datetime**|データベース スコープの資格情報が最後に変更された時刻です。|  
|target_type|**nvarchar(100)**|データベースの種類には、資格情報がスコープ設定されます。 返します`NULL`データベース スコープ資格情報。|  
|target_id|**int**|データベース スコープの資格情報にマップされているオブジェクトの ID。 データベースの 0 を返します。 資格情報のスコープ|  
  
## <a name="permissions"></a>権限  
 データベースに対する `CONTROL` 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [#40 です。 (&)、データベース スコープ ベースの資格情報を変更します。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
