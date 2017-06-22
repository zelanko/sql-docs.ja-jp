---
title: "ネイティブ コンパイル T-SQL モジュールでサポートされる DDL | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6468568f12555425cb038ce6293f8777e0a3689
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="supported-ddl-for-natively-compiled-t-sql-modules"></a>ネイティブ コンパイル T-SQL モジュールでサポートされる DDL
  このトピックでは、ストアド プロシージャ、スカラー UDF、インライン TVF、トリガーなど、ネイティブ コンパイル T-SQL モジュールでサポートされている DDL 構文を示します。  
  
 ネイティブ コンパイル T-SQL モジュールの一部として使用できる機能と T-SQL 対象領域の詳細については、「 [ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)」を参照してください。  
  
 サポートされていない構造については、「 [インメモリ OLTP でサポートされていない Transact-SQL の構造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。  
  
 サポート対象は次のとおりです。  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [DROP PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
-   [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
-   [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md) ステートメントと INSERT SELECT ステートメント  
  
-   SCHEMABINDING と BEGIN ATOMIC (ネイティブ コンパイル ストアド プロシージャで必要です)  
  
     詳細については、「 [Creating Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)」を参照してください。  
  
-   NATIVE_COMPILATION  
  
     詳細については、「 [Native Compilation of Tables and Stored Procedures](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md)」を参照してください。  
  
-   パラメーターと変数を NOT NULL として宣言できます (ネイティブ コンパイル モジュールのネイティブ コンパイル ストアド プロシージャとネイティブ コンパイル スカラー ユーザー定義関数のみ)。  
  
-   テーブル値パラメーター  
  
     詳細については、「[テーブル値パラメーターの使用 &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)」を参照してください。  
  
-   EXECUTE AS OWNER、SELF、CALLER、ユーザー。  
  
-   テーブルおよびプロシージャに対する GRANT 権限および DENY 権限。  
  
     詳細については、「[GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)」と「[DENY (オブジェクトの権限の拒否) &#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
