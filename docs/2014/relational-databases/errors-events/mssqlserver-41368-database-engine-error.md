---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2206980d241d3ef0aa683e4f987a4e337a86855
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62913807"
---
# <a name="mssqlserver_41368"></a>MSSQLSERVER_41368
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41368|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|メッセージ テキスト|READ COMMITTED 分離レベルを使用してメモリ最適化テーブルにアクセスする機能は、オートコミット トランザクションでのみサポートされます。 明示的なトランザクションおよび暗黙的なトランザクションではサポートされていません。 メモリ最適化テーブルには WITH (SNAPSHOT) などのテーブル ヒントを使用して、サポートされる分離レベルを指定します。|  
  
## <a name="explanation"></a>説明  
 READ COMMITTED 分離レベルを使用してメモリ最適化テーブルにアクセスする機能は、自動コミット トランザクションでのみサポートされます。 詳細については、「 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)」をご覧ください。  
  
 BEGIN TRANSACTION を使用して開始された明示的なトランザクション、または IMPLICIT_TRANSACTIONS が ON に設定されている状況で暗黙的なトランザクションからメモリ最適化テーブルにアクセスする場合は、READ COMMITTED 分離レベルはサポートされません。  
  
## <a name="user-action"></a>ユーザーの操作  
 明示的または暗黙的な READ COMMITTED トランザクションからメモリ最適化されたテーブルにアクセスする場合は、テーブルにアクセスするために SNAPSHOT を使用します。 これを実現するには、テーブルヒント WITH (SNAPSHOT) を使用します (詳細については、「[メモリ最適化テーブルを使用したトランザクション分離レベルのガイドライン](../in-memory-oltp/memory-optimized-tables.md)」を参照)。または、データベース MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT オプションを ON に設定する (詳細については、「 [ALTER database SET Options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options))」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
