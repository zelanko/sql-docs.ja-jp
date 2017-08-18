---
title: "Transact-SQL によるインメモリ OLTP のサポート | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cc975fbbdb4118158e4beacef63f45a63c479d38
ms.contentlocale: ja-jp
ms.lasthandoff: 08/18/2017

---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Transact-SQL によるインメモリ OLTP のサポート
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  インメモリ OLTP をサポートするために、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに構文オプションが追加されました。  
  
-   [ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md) (**MEMORY_OPTIMIZED_DATA** を追加)  
  
-   [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) (**MEMORY_OPTIMIZED_DATA** を追加)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
-   [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)  
  
-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
    ネイティブ コンパイル ストアド プロシージャでは、変数を **NOT NULL**として宣言できます。 通常のストアド プロシージャでは行えません。  
  
 SQL Server 2016 以降では、メモリ最適化テーブルの **AUTO_UPDATE_STATISTICS** を **ON** に設定することができます。 詳細については、「[sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)」を参照してください。  
  
 [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md) ON はネイティブ コンパイル ストアド プロシージャに対してサポートされていません。  
  
 サポートされていない機能の詳細については、「[インメモリ OLTP でサポートされていない Transact-SQL の構造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。  
  
 ネイティブ コンパイル ストアド プロシージャでサポートされている構造については、「 [ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md) 」および「 [ネイティブ コンパイル ストアド プロシージャ上でサポートされる構造](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md)」 を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP に対してサポートされていない SQL Server の機能](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)   
 [ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
