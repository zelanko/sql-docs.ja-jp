---
title: "FILE_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_NAME_TSQL
- FILE_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file names
- file names [SQL Server], FILE_NAME
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- displaying file names
- identification numbers [SQL Server], files
- FILE_NAME function
- logical file names [SQL Server]
ms.assetid: 68b298aa-ce47-4af5-b59f-9a1b46d48326
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 35b7f2b516227e00af629cadb5c1dccadad2b092
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="filename-transact-sql"></a>FILE_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたファイル識別 (ID) 番号の論理ファイル名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
FILE_NAME ( file_id )   
```  
  
## <a name="arguments"></a>引数  
 *file_id*  
 ファイル名を返す基になるファイル識別番号です。 *file_id*は**int**です。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar(128)**  
  
## <a name="remarks"></a>解説  
 *file_ID* sys.master_files または sys.database_files カタログ ビューの file_id 列に対応しています。  
  
## <a name="examples"></a>使用例  
 次の例は、のファイル名を返す`file_ID 1`と`file_ID`で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```sql  
SELECT FILE_NAME(1) AS 'File Name 1', FILE_NAME(2) AS 'File Name 2';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
File Name 1           File Name 2  
----------------      ------------------------  
AdventureWorks2012_Data   AdventureWorks2012_Log  

(1 row(s) affected)
``` 
  
## <a name="see-also"></a>参照  
 [FILE_IDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/file-idex-transact-sql.md)   
 [メタデータ関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
