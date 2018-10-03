---
title: sys.sp_rda_reauthorize_db (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sp_rda_reauthorize_db
- sp_rda_reauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reauthorize_db stored procedure
ms.assetid: f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f16a46c9461e7870897582fe2094fa233232973e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790440"
---
# <a name="syssprdareauthorizedb-transact-sql"></a>sys.sp_rda_reauthorize_db (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch とリモートのデータベースを有効になっているローカル データベースのデータベース間での認証済みの接続を復元します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_reauthorize_db @credential = @credential, @with_copy = @with_copy [ , @azure_servername = @azure_servername, @azure_databasename = @azure_databasename ]  
```  
  
## <a name="arguments"></a>引数  
 @credential = *@credential*  
 ローカルの Stretch 対応データベースに関連付けられたデータベース スコープ資格情報。  
  
 @with_copy = *@with_copy*  
 リモート データのコピーを作成し、コピー (推奨) に接続するかどうかを指定します。 *@with_copy* bit です。  
  
 @azure_servername = *@azure_servername*  
 リモート データを格納している Azure サーバーの名前を指定します。 *@azure_servername* sysname です。  
  
 @azure_databasename = *@azure_databasename*  
 リモート データを含む Azure のデータベースの名前を指定します。 *@azure_databasename* sysname です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  
  
## <a name="remarks"></a>Remarks  
 実行すると[sys.sp_rda_reauthorize_db (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)リモート Azure データベースに再接続すると、この操作が自動的にリセット クエリ モード LOCAL_AND_REMOTE に Stretch Database の既定の動作です。 つまり、クエリは、ローカルとリモートの両方のデータから結果を返します。  
  
## <a name="example"></a>例  
 次の例では、Stretch とリモートのデータベースが有効なローカル データベースの間で認証された接続を復元します。 (推奨)、リモート データのコピーを作成し、新しいコピーに接続します。  
  
```sql  
DECLARE @credentialName nvarchar(128);   
SET @credentialName = N'<existing_database_scoped_credential_name>';   
EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
```  
  
## <a name="see-also"></a>関連項目  
 [sys.sp_rda_deauthorize_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
