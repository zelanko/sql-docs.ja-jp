---
title: FILE_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILE_ID
- FILE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], files
- file IDs [SQL Server]
- FILE_ID function
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_ID
ms.assetid: 6a7382cf-a360-4d62-b9d2-5d747f56f076
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: c7aff15d482f4052774eb54299c9f4addcbb2fd2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827038"
---
# <a name="file_id-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

この関数は、現在のデータベースのコンポーネント ファイルの特定の論理名に対するファイル識別 (ID) 番号を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>引数  
*file_name*  
ファイル ID 値 **を取得するファイルの論理名を表す**sysname`FILE_ID` 型の式です。  
  
## <a name="return-types"></a>戻り値の型  
**smallint**  
  
## <a name="remarks"></a>解説  
*file_name* は、カタログ ビュー sys.master_files または sys.database_files の name 列に表示される論理ファイル名に対応します。  

`FILE_ID`file_name`NULL` が現在のデータベースのコンポーネント ファイルの論理名に対応していない場合、*は* を返します。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、フルテキスト カタログに 32,767 より大きいファイル識別番号が割り当てられます。 `FILE_ID` 関数の戻り値の型は **smallint** なので、`FILE_ID` はフルテキスト ファイルをサポートしません。 代わりに [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) を使用してください。  
  
## <a name="examples"></a>例  
この例では、`AdventureWorks_Data` データベースのコンポーネント ファイルである `ADVENTUREWORKS2012` ファイルのファイル ID 値が返されます。  

```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_ID('AdventureWorks2012_Data')AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server 2016 データベース エンジンの非推奨の機能](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [FILE_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [メタデータ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
