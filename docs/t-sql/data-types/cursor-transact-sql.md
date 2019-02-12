---
title: cursor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1849a138410485a26be32e6a15603d5aa1a56de8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024023"
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
[データ型の変換 (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
