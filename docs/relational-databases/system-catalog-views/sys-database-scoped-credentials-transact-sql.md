---
title: "sys.database_scoped_credentials (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords: sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
caps.latest.revision: "2"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34db44a8b28ef9441e9bd6214e89ba2ef0e9f41b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
|target_type|**nvarchar (100)**|データベースの種類には、資格情報がスコープ設定されます。 返します`NULL`データベース スコープ資格情報。|  
|target_id|**int**|データベース スコープの資格情報にマップされているオブジェクトの ID。 データベースの 0 を返します。 資格情報のスコープ|  
  
## <a name="permissions"></a>Permissions  
 データベースに対する `CONTROL` 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [データベース スコープの資格情報 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER データベース スコープの資格情報 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [データベース スコープの資格情報 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
