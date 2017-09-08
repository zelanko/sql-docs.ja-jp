---
title: "DROP FULLTEXT INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
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
- DROP_FULLTEXT_INDEX_TSQL
- DROP FULLTEXT INDEX
dev_langs:
- TSQL
helpviewer_keywords:
- deleting full-text indexes
- removing full-text indexes
- full-text indexes [SQL Server], removing
- DROP FULLTEXT INDEX statement
- dropping full-text indexes
ms.assetid: 7443a4ab-1d43-4a22-bbba-a07f620892cb
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d4636ec49342f1028a09b90c348387520e5e4355
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-fulltext-index-transact-sql"></a>DROP FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定したテーブルまたはインデックス付きビューからフルテキスト インデックスを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP FULLTEXT INDEX ON table_name  
```  
  
## <a name="arguments"></a>引数  
 *table_name*  
 削除するフルテキスト インデックスが含まれているテーブルまたはインデックス付きビューの名前を指定します。  
  
## <a name="remarks"></a>解説  
 DROP FULLTEXT INDEX コマンドを使用する前に、フルテキスト インデックスからすべての列を削除する必要はありません。  
  
## <a name="permissions"></a>Permissions  
 ユーザーがテーブルまたはインデックス付きビューに対する ALTER 権限を持っているかのメンバーである必要があります、 **sysadmin**固定サーバー ロール、または**db_owner**または**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、上に存在するフルテキスト インデックスを削除、`JobCandidate`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
DROP FULLTEXT INDEX ON HumanResources.JobCandidate;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_indexes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  
