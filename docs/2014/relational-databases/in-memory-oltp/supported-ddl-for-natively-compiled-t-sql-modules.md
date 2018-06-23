---
title: ネイティブ コンパイル ストアド プロシージャでコンス トラクターはサポートされて |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: c54f811f2257adcb5c08f1741018be3211c1e874
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178652"
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
  
  