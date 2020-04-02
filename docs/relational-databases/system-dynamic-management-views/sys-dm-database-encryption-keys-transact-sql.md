---
title: dm_database_encryption_keys (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6e716c826fd366fda4505b7fcf9ec8e3b756ec25
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531058"
---
# <a name="sysdm_database_encryption_keys-transact-sql"></a>dm_database_encryption_keys (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベースの暗号化状態と、関連付けられているデータベース暗号化キーに関する情報を返します。 データベース暗号化の詳細については、「[Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**int**|データベースの ID です。|  
|encryption_state|**int**|データベースが暗号化されているかどうかを示します。<br /><br /> 0 = データベース暗号化キーが存在しない、暗号化なし<br /><br /> 1 = 暗号化されていない<br /><br /> 2 = 暗号化処理中<br /><br /> 3 = 暗号化済み<br /><br /> 4 = キーの変更中<br /><br /> 5 = 復号化が進行中<br /><br /> 6 = 保護の変更が進行中です (データベース暗号化キーを暗号化している証明書または非対称キーが変更されています)。|  
|create_date|**Datetime**|暗号化キーが作成された日付 (UTC) を表示します。|  
|regenerate_date|**Datetime**|暗号化キーが再生成された日付 (UTC) を表示します。|  
|modify_date|**Datetime**|暗号化キーが変更された日付 (UTC) を表示します。|  
|set_date|**Datetime**|暗号化キーがデータベースに適用された日付 (UTC) を表示します。|  
|opened_date|**Datetime**|データベース キーが最後に開かれた時刻 (UTC) を示します。|  
|key_algorithm|**nvarchar(32)**|キーに使用されるアルゴリズムを表示します。|  
|key_length|**int**|キーの長さを表示します。|  
|encryptor_thumbprint|**varbinary(20)**|暗号化のサムプリントを表示します。|  
|encryptor_type|**nvarchar(32)**|**に適用されます**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : ([現在のバージョン](https://go.microsoft.com/fwlink/p/?LinkId=299658)まで )。<br /><br /> 暗号化器について説明します。|  
|percent_complete|**real**|データベース暗号化状態の変更の完了率。 状態が変更されていない場合は 0 になります。|
|encryption_state_desc|**nvarchar(32)**|**に適用されます**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]および後で。<br><br> データベースが暗号化されているかどうかを示す文字列です。<br><br>NONE<br><br>暗号化<br><br>暗号化<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**に適用されます**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]および後で。<br><br>暗号化スキャンの現在の状態を示します。 <br><br>0 = スキャンが開始されていません。<br><br>1 = スキャンが進行中です。<br><br>2 = スキャンは進行中ですが、中断されています。<br><br>3 = スキャンが中止された理由は何らかの理由で、手動による介入が必要です。 詳細については、マイクロソフト サポートにお問い合わせください。<br><br>4 = スキャンが正常に完了し、TDE が有効になり、暗号化が完了しました。|
|encryption_scan_state_desc|**nvarchar(32)**|**に適用されます**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]および後で。<br><br>暗号化スキャンの現在の状態を示す文字列。<br><br> NONE<br><br>RUNNING<br><br>SUSPENDED<br><br>ABORTED<br><br>完了|
|encryption_scan_modify_date|**Datetime**|**に適用されます**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]および後で。<br><br> 暗号化スキャンの状態が最後に変更された日付 (UTC) を表示します。|
  
## <a name="permissions"></a>アクセス許可

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、アクセス`VIEW SERVER STATE`許可が必要です。   
Premium[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベースに`VIEW DATABASE STATE`対する権限が必要です。 標準[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]および基本レベルでは、**サーバー管理者**または**Azure アクティブ ディレクトリ管理者**アカウントが必要です。   

## <a name="see-also"></a>参照  

 [セキュリティ関連の動的管理ビューと関数&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [TDE&#41;&#40;透過的なデータ暗号化](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL サーバーの暗号化](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [データベース エンジン&#41;&#40;SQL Server およびデータベース暗号化キー](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [データベース セット オプション&#40;の変更&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [データベース暗号化キー&#40;作成&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [データベース暗号化キー&#40;の変更&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
