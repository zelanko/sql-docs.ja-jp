---
title: "データベース暗号化キー (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 559e85cf5ba8e565a6afc86d3537b476365bd980
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 データベースを透過的に暗号化するために使用する暗号化キーを作成します。 透過的なデータベースの暗号化の詳細については、次を参照してください。 [Transparent Data Encryption & #40 です。TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY  }  
暗号化キーに使用する暗号化アルゴリズムを指定します。   
>  [!NOTE]
>    SQL Server 2016 以降、AES_128、AES_192、AES_256 以外のすべてのアルゴリズムは推奨されません。 古いアルゴリズムを使用する場合は (推奨されません)、データベース互換性レベルを 120 以下に設定する必要があります。  
  
サーバー証明書 Encryptor_Name による暗号化  
データベース暗号化キーを暗号化するために使用する暗号化処理方法の名前を指定します。  
  
サーバー非対称キー Encryptor_Name による暗号化  
データベース暗号化キーを暗号化するために使用する非対称キーの名前を指定します。 非対称キーでデータベース暗号化キーを暗号化するには、非対称キーが拡張キー管理プロバイダーに存在している必要があります。  
  
## <a name="remarks"></a>解説  
使用してデータベースを暗号化できる前に、データベース暗号化キーが必要な*Transparent Database Encryption* (TDE)。 データベースを透過的に暗号化すると、特別にコードを変更することなく、データベース全体がファイル レベルで暗号化されます。 データベース暗号化キーの暗号化に使用する証明書または非対称キーは、マスター システム データベースに配置されている必要があります。  
  
データベース暗号化ステートメントは、ユーザー データベースでのみ使用できます。  
  
データベース暗号化キーは、データベースからエクスポートできません。 このキーを使用できるのは、システム、サーバーでのデバッグ権限を持つユーザー、およびデータベース暗号化キーを暗号化および暗号化解除する証明書へのアクセス権を持つユーザーに限られています。  
  
データベース所有者 (dbo) が変わっても、データベース暗号化キーを再生成する必要はありません。  
  
データベース暗号化キーが自動的に作成、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベース。 CREATE DATABASE ENCRYPTION KEY ステートメントを使用してキーを作成する必要はありません。  
  
## <a name="permissions"></a>Permissions  
データベースに対する CONTROL 権限と、データベース暗号化キーの暗号化に使用する証明書または非対称キーに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
TDE を使用してその他の例では、次を参照してください。 [Transparent Data Encryption & #40 です。TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)、 [EKM を使用して SQL Server での TDE を有効にする](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)、および[Azure Key Vault &#40; を使用して、拡張キー管理SQL Server &#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
次の例では、`AES_256` アルゴリズムを使用してデータベース暗号化キーを作成し、`MyServerCert` という証明書で秘密キーを保護します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
TDE を使用してその他の例では、次を参照してください。[透過的なデータ暗号化 (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d)です。  
  
次の例では、`AES_256` アルゴリズムを使用してデータベース暗号化キーを作成し、`MyServerCert` という証明書で秘密キーを保護します。  
  
```  
-- Uses AdventureWorks  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>参照  
[透過的なデータ暗号化 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[SQL Server の暗号化](../../relational-databases/security/encryption/sql-server-encryption.md)   
[SQL Server とデータベースの暗号化キー &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[ALTER DATABASE ENCRYPTION KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[DROP DATABASE ENCRYPTION KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    

