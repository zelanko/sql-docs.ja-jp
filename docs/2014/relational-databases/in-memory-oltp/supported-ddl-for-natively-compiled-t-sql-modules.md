---
title: 構造をネイティブ コンパイル ストアド プロシージャでサポートされています |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6cdd5c7d154f1841aa5c90e110a596d8684a535
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233272"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャ上でサポートされる構造
  このトピックでは、ネイティブ コンパイル ストアド プロシージャでサポートされる構造について説明します。  
  
 サポートされていない構造については、「[インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。  
  
## <a name="procedure-ddl"></a>プロシージャ DDL  
 サポート対象は次のとおりです。  
  
-   CREATE PROCEDURE  
  
-   DROP PROCEDURE  
  
-   SCHEMABINDING (ネイティブ コンパイル ストアド プロシージャで必要です)  
  
-   NATIVE_COMPILATION  
  
-   パラメーターは NOT NULL として宣言できます。  
  
-   テーブル値パラメーター  
  
## <a name="security"></a>Security  
 サポート対象は次のとおりです。  
  
-   プロシージャの場合: EXECUTE AS OWNER、SELF、およびユーザー。  
  
-   テーブルおよびプロシージャに対する GRANT 権限および DENY 権限。  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md)  
  
  
