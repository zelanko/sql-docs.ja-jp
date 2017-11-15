---
title: "ネイティブ コンパイル モジュールでの IF-WHILE EXISTS ステートメントのシミュレーション | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 344c7581c9265eca529d4749b5614a66d4e60239
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>ネイティブ コンパイル モジュールでの IF-WHILE EXISTS ステートメントのシミュレーション
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  ネイティブ コンパイル ストアド プロシージャは、条件ステートメント (IF や WHILE など) の **EXISTS** 句をサポートしていません。  
  
 次の例は、SELECT ステートメントで BIT 変数を使用して EXISTS 句をシミュレートするための回避策を表しています。  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP でサポートされていない Transact-SQL の構造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
