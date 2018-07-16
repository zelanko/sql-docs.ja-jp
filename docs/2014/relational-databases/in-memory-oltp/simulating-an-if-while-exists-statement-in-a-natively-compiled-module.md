---
title: ネイティブ コンパイル ストアド プロシージャ内の EXISTS 句のシミュレーション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ed6265a67d32407b22c14f9f6b2b850a1421915
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281078"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>ネイティブ コンパイル ストアド プロシージャ内の EXISTS 句のシミュレーション
  ネイティブ コンパイル ストアド プロシージャでは `EXISTS` 句はサポートされませんが、対応策があります。  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
