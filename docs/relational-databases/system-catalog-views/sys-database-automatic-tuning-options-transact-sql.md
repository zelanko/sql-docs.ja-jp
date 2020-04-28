---
title: database_automatic_tuning_options (Transact-sql) |Microsoft Docs
description: SQL Database で自動チューニングオプションを表示する方法について説明します。
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 437dbbc4ea7deb32a9723febb443cc67941fdc5e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67940225"
---
# <a name="sysdatabase_automatic_tuning_options-transact-sql"></a>データベース\_の自動\_tuning_options (transact-sql)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  このデータベースの自動チューニングオプションを返します。  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|自動チューニングオプションの名前。 使用可能なオプションについては、 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)を参照してください。|  
|**desired_state**|**smallint**|自動チューニングオプションの目的の操作モードを示します。ユーザーによって明示的に設定されます。<br />0 = OFF<br />1 = ON|  
|**desired_state_desc**|**nvarchar(60)**|自動チューニングオプションの目的の操作モードの説明テキスト。<br />OFF<br />ON|  
|**actual_state**|**smallint**|自動チューニングオプションの操作モードを示します。<br />0 = OFF<br />1 = ON|  
|**actual_state_desc**|**nvarchar(60)**|自動チューニングオプションの実際の操作モードの説明テキストです。<br />OFF<br />ON|  
|**reason**|**smallint**|実際の状態と目的の状態が異なる理由を示します。<br />2 = 無効<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|実際の状態と目的の状態が異なる理由の説明テキスト。<br />DISABLED = オプションはシステムによって無効にされています<br />QUERY_STORE_OFF = クエリストアがオフになっています<br />QUERY_STORE_READ_ONLY = クエリストアが読み取り専用モードです。<br />NOT_SUPPORTED = Enterprise edition で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみ使用可能| 
  
## <a name="permissions"></a>アクセス許可  
 `VIEW DATABASE STATE` アクセス許可が必要です。  
  
## <a name="see-also"></a>参照  
 [自動チューニング](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [database_query_store_options &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [dm_db_tuning_recommendations &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
