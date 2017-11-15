---
title: "メモリ最適化テーブルへの IDENTITY の実装 | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ff2fc2a470d0382dfe92a91b996b178ee938337
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>メモリ最適化テーブルへの IDENTITY の実装
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

シードと増分値がいずれも 1 (既定である) 限り、メモリ最適化テーブルでは IDENTITY がサポートされています。 IDENTITY(x, y) という定義を持つ ID 列で、x != 1 または y != 1 の場合は、メモリ最適化テーブルでサポートされません。   
    
IDENTITY シードを増やすには、セッション オプション `SET IDENTITY_INSERT table_name ON`を使用して、ID 列に対する明示的な値を指定して新しい行を挿入します。 行を挿入すると、IDENTITY シードは明示的に挿入された値 +1 に変更されます。 たとえば、シードを 1000 に増やすには ID 列に値 999 を含む行を挿入します。 生成される ID 値は、1000 から開始されます。     
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
