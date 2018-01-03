---
title: "ネイティブ コンパイル モジュールでの IF-WHILE EXISTS ステートメントのシミュレーション | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bbe222fa209a5dd399e7f4506684c8f3cb0ebeb2
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>ネイティブ コンパイル モジュールでの IF-WHILE EXISTS ステートメントのシミュレーション
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  ネイティブ コンパイル ストアド プロシージャは、条件ステートメント (IF や WHILE など) の **EXISTS** 句をサポートしていません。  
  
 次の例は、SELECT ステートメントで BIT 変数を使用して EXISTS 句をシミュレートするための回避策を表しています。  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP でサポートされていない Transact-SQL の構造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
