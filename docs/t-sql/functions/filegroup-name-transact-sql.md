---
title: "FILEGROUP_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEGROUP_NAME_TSQL
- FILEGROUP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- displaying filegroup names
- identification numbers [SQL Server], filegroups
- filegroups [SQL Server], IDs
- IDs [SQL Server], filegroups
- FILEGROUP_NAME function
- filegroups [SQL Server], names
- names [SQL Server], filegroups
- viewing filegroup names
ms.assetid: 26add1c0-56e5-47a8-b489-ae56784a7ee9
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3560dc757c9e1f8d6c294f35e69653ba511f96e1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="filegroupname-transact-sql"></a>FILEGROUP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたファイル識別 (ID) 番号のファイル グループ名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FILEGROUP_NAME ( filegroup_id )   
```  
  
## <a name="arguments"></a>引数  
 *filegroup_id*  
 ファイル グループ名を返す基になるファイル グループ ID 番号を指定します。 *filegroup_id*は**smallint**です。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (128)**  
  
## <a name="remarks"></a>解説  
 *filegroup_id*に対応する、 **data_space_id**内の列、 **sys.filegroups**カタログ ビューです。  
  
## <a name="examples"></a>使用例  
 次の例は、ファイル グループ ID のファイル グループ名を返します`1`で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
  
SELECT FILEGROUP_NAME(1) AS [Filegroup Name];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Filegroup Name   
-----------------------  
PRIMARY  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
