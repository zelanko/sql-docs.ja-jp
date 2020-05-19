---
title: Transact-SQL によるインメモリ OLTP のサポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8042534c8b22863c5a00abf4969bdb9754cef892
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702210"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Transact-SQL によるインメモリ OLTP のサポート
  Transact-SQL クエリまたは DML ステートメント (SELECT、INSERT、UPDATE、または DELETE)、アドホック ステートメント、および SQL モジュール (ストアド プロシージャ、テーブル-値関数、スカラー関数、トリガー、ビューなど) を使用して、メモリ最適化テーブルにアクセスできます。 詳細については、「解釈された[Transact-sql を使用したメモリ最適化テーブルへのアクセス](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)」を参照してください。  
  
 メモリ最適化テーブルのみを参照するストアド プロシージャは、マシン コードにネイティブ コンパイルできます。これにより、一般に、インタープリタ式の (ディスク ベースの) ストアド プロシージャよりも大幅に高いパフォーマンスが得られます。 メモリ最適化テーブル アクセスを最適化するには、ネイティブ コンパイル ストアド プロシージャを使用します。 詳細については、次を参照してください。 [ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md)です。  
  
 データベース オブジェクト (DDL ステートメント) を作成および変更する場合に、次のステートメントが修正されました。  
  
-   [Transact-sql&#41;&#40;の ALTER database の File および Filegroup オプション](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)(「」を参照 `MEMORY_OPTIMIZED_DATA` )  
  
-   [Transact-sql&#41;SQL Server のデータベース &#40;の作成](/sql/t-sql/statements/create-database-sql-server-transact-sql)(「」を参照 `MEMORY_OPTIMIZED_DATA` )  
  
-   [Transact-sql&#41;&#40;プロシージャを作成する](/sql/t-sql/statements/create-procedure-transact-sql)(「」、「」、「」、「」、「」、「」を参照 `NATIVE_COMPILATION` `SCHEMABINDING` `EXECUTE AS` `BEGIN ATOMIC` )  
  
-   [Transact-sql&#41;を CREATE TABLE &#40;](/sql/t-sql/statements/create-table-transact-sql) (「」、「」、「」、「」、「」、「」、および「」を参照 `MEMORY_OPTIMIZED` `DURABILITY` `BUCKET_COUNT` `INDEX` `HASH` )  
  
-   [Transact-sql&#41;&#40;型を作成する](/sql/t-sql/statements/create-type-transact-sql)(「」、「」、「」、「」、「」、「」を参照 `MEMORY_OPTIMIZED` `BUCKET_COUNT` `INDEX` `HASH` )  
  
-   [ @local_variable Transact-sql&#41;の &#40;宣言](/sql/t-sql/language-elements/declare-local-variable-transact-sql)(「」を参照 `NULL`  |  `NOT NULL` )  
  
 メモリ最適化テーブルは、`PRIMARY KEY` および `NOT NULL` の制約をサポートしています。 サポートされていない制約の実装の詳細については、「 [Check 制約と Foreign Key 制約の移行](../../database-engine/migrating-check-and-foreign-key-constraints.md)」を参照してください。  
  
 サポートされていない機能の詳細については、「[インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [サポートされるデータ型](supported-data-types-for-in-memory-oltp.md)  
  
-   [解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [インメモリ OLTP 向けのシステム ビュー、ストアド プロシージャ、DMV、待機の種類](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](in-memory-oltp-in-memory-optimization.md)   
 [ネイティブコンパイルストアドプロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)   
 [サポートされている SQL Server 機能](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [ネイティブコンパイルストアドプロシージャ](natively-compiled-stored-procedures.md)  
  
  
