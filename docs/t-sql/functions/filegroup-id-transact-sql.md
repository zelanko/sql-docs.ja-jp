---
title: FILEGROUP_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1ce9b0d41ae0d1acf097999cd274c76e8e0571df
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781633"
---
# <a name="filegroupid-transact-sql"></a>FILEGROUP_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

この館数は、指定されたファイル グループ名のファイル グループ識別 (ID) 番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
FILEGROUP_ID ( 'filegroup_name' )   
```  
  
## <a name="arguments"></a>引数  
*filegroup_name* **sysname** 型の式。ファイル グループ ID `FILEGROUP_ID` を取得するファイル グループの名前を表します。  
  
## <a name="return-types"></a>戻り値の型  
**int**  
  
## <a name="remarks"></a>Remarks  
*filegroup_name* に対応する、 **名前** 内の列、 **sys.filegroups** カタログ ビューです。  
  
## <a name="examples"></a>使用例  
この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `PRIMARY` という名前のファイル グループのファイル グループ ID を取得します。  
  
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
  
  
