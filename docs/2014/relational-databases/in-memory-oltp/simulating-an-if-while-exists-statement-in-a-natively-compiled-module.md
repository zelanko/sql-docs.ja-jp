---
title: ネイティブ コンパイル ストアド プロシージャ内の EXISTS 句をシミュレートする |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 68515c717fa39cfd626c83625dc7b95c24c68d69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085221"
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
  
  