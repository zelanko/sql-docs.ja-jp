---
title: FILEGROUP_ID (Transact-SQL) | Microsoft Docs
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
- FILEGROUP_ID_TSQL
- FILEGROUP_ID
dev_langs:
- TSQL
helpviewer_keywords:
- FILEGROUP_ID function
- identification numbers [SQL Server], filegroups
- filegroups [SQL Server], IDs
- IDs [SQL Server], filegroups
- names [SQL Server], filegroups
ms.assetid: 852a76d8-9e61-4a31-84ee-c7edb84a061c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 62b561d476debacc5f76be8f465b2f14f178ffd9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="filegroupid-transact-sql"></a>FILEGROUP_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたファイル グループ名のファイル グループ識別 (ID) 番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FILEGROUP_ID ( 'filegroup_name' )   
```  
  
## <a name="arguments"></a>引数  
 **'** *filegroup_name* **'**  
 ファイル グループ ID を返すファイル グループの名前を表す **sysname** 型の式を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 *filegroup_name* に対応する、 **名前** 内の列、 **sys.filegroups** カタログ ビューです。  
  
## <a name="examples"></a>使用例  
 次の例では、`PRIMARY` データベース内の [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] という名前のファイル グループのファイル グループ ID を返します。  
  
```  
  
SELECT FILEGROUP_ID('PRIMARY') AS [Filegroup ID];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
Filegroup ID  
------------  
1  

(1 row(s) affected)
 ```  
  
## <a name="see-also"></a>参照  
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [メタデータ関数 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
