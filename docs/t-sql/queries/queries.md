---
title: クエリ | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5ff02a32-e8d3-479c-ae8b-07581e41f5f8
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 12216fc788040d946983e7da6e0683723826902b
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084173"
---
# <a name="queries"></a>クエリ
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データ操作言語 (DML) は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および SQL Database でデータを取得して操作するために使用される用語の集まりです。 そのほとんどは、SQL Data Warehouse と PDW で利用できます (詳細については個々のステートメントを確認してください)。 DML ステートメントを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに対してデータの追加、変更、クエリ、または削除を実行できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用する DML ステートメントを示しています。  
  
|||  
|-|-|  
|[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)|[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|  
|[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)|  
|[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)|[UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)|  
|[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)|[WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)|  
|[READTEXT &#40;Transact-SQL&#41;](../../t-sql/queries/readtext-transact-sql.md)||  
  
 次の表は、複数の DML ステートメントまたは DML 句で使用される句を示しています。  
  
|句|使用対象のステートメントまたは句|  
|------------|-------------------------------------|  
|[FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)|DELETE、SELECT、UPDATE|  
|[Hints &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql.md)|DELETE、INSERT、SELECT、UPDATE|  
|[OPTION 句 &#40;Transact-SQL&#41;](../../t-sql/queries/option-clause-transact-sql.md)|DELETE、SELECT、UPDATE|  
|[OUTPUT 句 &#40;Transact-SQL&#41;](../../t-sql/queries/output-clause-transact-sql.md)|DELETE、INSERT、MERGE、UPDATE|  
|[検索条件 &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md)|DELETE、MERGE、SELECT、UPDATE|  
|[テーブル値コンストラクター &#40;Transact-SQL&#41;](../../t-sql/queries/table-value-constructor-transact-sql.md)|FROM、INSERT、MERGE|  
|[TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md)|DELETE、INSERT、MERGE、SELECT、UPDATE|  
|[WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)|DELETE、SELECT、UPDATE、MATCH|  
|[WITH common_table_expression &#40;Transact-SQL&#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md)|DELETE、INSERT、MERGE、SELECT、UPDATE|  
  
  
