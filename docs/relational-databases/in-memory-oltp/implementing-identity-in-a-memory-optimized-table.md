---
title: メモリ最適化テーブルへの IDENTITY の実装 | Microsoft Docs
description: SQL Server のメモリ最適化テーブルでの IDENTITY について説明します。 メモリ最適化テーブルでは、シードに対する IDENTITY と増分値 1 がサポートされています。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ef0fb83f092d2920ab36bf977edd18a6dda71e28
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460445"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>メモリ最適化テーブルへの IDENTITY の実装
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

シードと増分値がいずれも 1 (既定である) 限り、メモリ最適化テーブルでは IDENTITY がサポートされています。 IDENTITY(x, y) という定義を持つ ID 列で、x != 1 または y != 1 の場合は、メモリ最適化テーブルでサポートされません。   
    
IDENTITY シードを増やすには、セッション オプション `SET IDENTITY_INSERT table_name ON`を使用して、ID 列に対する明示的な値を指定して新しい行を挿入します。 行を挿入すると、IDENTITY シードは明示的に挿入された値 +1 に変更されます。 たとえば、シードを 1000 に増やすには ID 列に値 999 を含む行を挿入します。 生成される ID 値は、1000 から開始されます。     
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](./plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)  
  
