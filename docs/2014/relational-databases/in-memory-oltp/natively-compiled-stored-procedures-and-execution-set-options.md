---
title: ネイティブ コンパイル ストアド プロシージャと実行 SET オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 264a2b3ab1e6f3f0bda97bfe89a4438aa641577d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025852"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>ネイティブ コンパイル ストアド プロシージャと実行 SET オプション
  セッションのオプションは、ATOMIC ブロックでは固定されています。 ストアド プロシージャの実行は、セッションの SET オプションの影響を受けません。 ただし、特定の SET オプション (SET NOEXEC や SET SHOWPLAN_XML など) を指定すると、ストアド プロシージャ (ネイティブ コンパイル ストアド プロシージャを含む) が実行されなくなります。  
  
 任意の STATISTICS オプションを有効にしてネイティブ コンパイル ストアド プロシージャを実行すると、統計情報は、ステートメントごとではなく、プロシージャ全体に対して収集されます。 詳細については、「[SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql)」、「[SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql)」、「[SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql)」、「[SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)」を参照してください。 ネイティブ コンパイル ストアド プロシージャのステートメントごとのレベルに対する実行統計を取得するには、ストアド プロシージャの実行に含まれる各クエリが完了したときに開始される sp_statement_completed イベントの拡張イベント セッションを使用します。 拡張イベント セッションの作成の詳細については、「[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)」を参照してください。  
  
 ネイティブ コンパイル ストアド プロシージャでは、`SHOWPLAN_XML` がサポートされています。 `SHOWPLAN_ALL` と `SHOWPLAN_TEXT` は、ネイティブ コンパイル ストアド プロシージャではサポートされていません。  
  
 `SET FMTONLY` は、ネイティブ コンパイル ストアド プロシージャではサポートされていません。 代わりに [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) を使用します。  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md)  
  
  
