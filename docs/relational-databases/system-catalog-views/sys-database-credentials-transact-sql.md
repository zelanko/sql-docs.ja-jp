---
title: database_credentials (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2521d9543c71d9dee298fbb58518163fd45fbfdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67999529"
---
# <a name="sysdatabase_credentials-transact-sql"></a>database_credentials (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  データベース内のデータベーススコープ資格情報ごとに1行のデータを返します。  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、 [sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)を使用してください。    
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|データベーススコープ資格情報の ID。 データベース内で一意です。|  
|name|**sysname**|データベーススコープの資格情報の名前。 データベース内で一意です。|  
|credential_identity|**nvarchar(4000)**|使用する識別情報の名前。 通常、これは Windows ユーザーです。 一意である必要はありません。|  
|create_date|**DATETIME**|データベーススコープの資格情報が作成された時刻。|  
|modify_date|**DATETIME**|データベーススコープの資格情報が最後に変更された時刻。|  
|target_type|**nvarchar (100)**|データベーススコープ資格情報の種類。 データベーススコープの資格情報の場合は NULL を返します。|  
|target_id|**int**|データベーススコープの資格情報のマップ先のオブジェクトの ID。 データベーススコープの資格情報の場合は0を返します|  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する `CONTROL` 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベースエンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Transact-sql&#41;&#40;データベーススコープの資格情報を作成する](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [Transact-sql&#41;&#40;データベーススコープの資格情報の変更](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [Transact-sql&#41;&#40;データベーススコープの資格情報を削除します。](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
