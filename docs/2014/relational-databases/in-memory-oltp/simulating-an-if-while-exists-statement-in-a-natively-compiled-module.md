---
title: ネイティブ コンパイル ストアド プロシージャ内の EXISTS 句のシミュレーション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac041e19aeb5948a644a9fcf82b3e687472b7259
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535624"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>ネイティブ コンパイル ストアド プロシージャ内の EXISTS 句のシミュレーション
  ネイティブ コンパイル ストアド プロシージャでは `EXISTS` 句はサポートされませんが、対応策があります。  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
