---
title: cursor (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b9fa1c8e8fea6aabf8fe8a0e6e84f82f7220facf
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

カーソルへの参照を格納している変数やストアド プロシージャの OUTPUT パラメーターを表すデータ型です。
  
## <a name="remarks"></a>Remarks  
**cursor** 型の変数とパラメーターを参照できる操作は次のとおりです。
-   DECLARE *@local_variable* および SET *@local_variable* ステートメント。  
-   OPEN、FETCH、CLOSE、および DEALLOCATE の各カーソル ステートメント  
-   ストアド プロシージャ出力パラメーター  
-   CURSOR_STATUS 関数  
-   **sp_cursor_list**、**sp_describe_cursor**、**sp_describe_cursor_tables**、および **sp_describe_cursor_columns** の各システム ストアド プロシージャ  
  
**sp_cursor_list** および **sp_describe_cursor** の **cursor_name** 出力列に、カーソル変数の名前が返されます。
  
作成された任意の変数、 **カーソル** データ型は null を許容します。
  
**カーソル** CREATE TABLE ステートメント内の列のデータ型を使用することはできません。
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[データ型の変換 &#40;Database Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
