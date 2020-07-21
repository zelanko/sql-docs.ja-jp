---
title: ネイティブコンパイルストアドプロシージャからの TempDB 内のテーブルの作成とアクセス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c66b43d4bad56724817a4d38a810fd150b2b3fd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050249"
---
# <a name="creating-and-accessing-tables-in-tempdb-from-natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャからの TempDB 内のテーブルの作成およびアクセス
  ネイティブ コンパイル ストアド プロシージャからの TempDB 内のテーブルの作成およびアクセスはサポートされていません。 代わりに、テーブル型およびテーブル変数を使用します。 次に例を示します。  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = 'english'  
)  
  -- declare table variables for the list of orders   
  DECLARE @Input dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @Input SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブコンパイルストアドプロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)   
 [インメモリ OLTP でサポートされていない transact-sql の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
