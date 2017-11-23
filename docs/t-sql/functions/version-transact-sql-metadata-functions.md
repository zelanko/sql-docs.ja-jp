---
title: "バージョン (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa9dec84a07189eb3b2c6c9c3d9342db4eac1df6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="version---transact-sql-metadata-functions"></a>バージョン - Transact SQL メタデータ関数
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 バージョンを返します[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)]アプライアンスで実行されています。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>引数  
  
## <a name="general-remarks"></a>全般的な解説  
テーブル名を指定する必要があります、 [FROM](../../t-sql/queries/from-transact-sql.md)結果を返すには、この関数の句。 クエリの結果セットの各行の結果の行が返されます使用して[上部 (TRANSACT-SQL)](../../t-sql/queries/top-transact-sql.md)返された行の数を制限します。  
  
## <a name="examples"></a>使用例  
次の例では、バージョン番号を返します。  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>参照 
[SESSION_ID (TRANSACT-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/db-name-transact-sql.md)  
  
  
