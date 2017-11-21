---
title: "FILE_IDEX (TRANSACT-SQL) |Microsoft ドキュメント"
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
- FILE_IDEX
- FILE_IDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILE_IDEX function
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_IDEX
ms.assetid: 7532fea5-ee5e-4edd-b98b-111a7ba56c8e
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 9a65a49a1e6d8c23a28b117fc90b0276ce185556
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="fileidex-transact-sql"></a>FILE_IDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

現在のデータベース内のデータ、ログ、またはフルテキスト ファイルについて、指定された論理ファイル名のファイル識別 (ID) 番号を返します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
FILE_IDEX ( file_name )  
```  
  
## <a name="arguments"></a>引数  
 *file_name*  
 型の式は、 **sysname**ファイル ID を返す対象のファイルの名前を表す  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
 **NULL**エラー  
  
## <a name="remarks"></a>解説  
 *file_name*に表示される論理ファイル名に対応する、**名前**内の列、 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)または[sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)カタログ ビューです。  
  
 FILE_IDEX は、選択リスト、WHERE 句、または式が許容される任意の場所で使用できます。 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-the-file-id-of-a-specified-file"></a>A. 指定されたファイルのファイル ID を取得する  
次の例では、`AdventureWorks_Data` というファイルのファイル ID が返されます。  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX('AdventureWorks2012_Data') AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
### <a name="b-retrieving-the-file-id-when-the-file-name-is-not-known"></a>B. ファイル名が不明の場合のファイル ID を取得する  
次の例のファイル ID を返して、`AdventureWorks`から論理ファイル名を選択して、ログ ファイル、`sys.database_files`カタログ ビューのファイルの種類と等しい`1`(ログ) です。  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX((SELECT TOP (1) name FROM sys.database_files WHERE type = 1)) AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
2  
```  
  
### <a name="c-retrieving-the-file-id-of-a-full-text-catalog-file"></a>C. フルテキスト カタログ ファイルのファイル ID を取得する  
次の例では、フルテキスト ファイルのファイル ID を返してから論理ファイル名を選択して、`sys.database_files`カタログ ビューのファイルの種類と等しい`4`(フル テキスト)。 この例では、フルテキスト カタログが存在しない場合、NULL が返されます。  
  
```tsql  
SELECT FILE_IDEX((SELECT name FROM sys.master_files WHERE type = 4))  
AS 'File_ID';  
```  
  
## <a name="see-also"></a>参照  
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

