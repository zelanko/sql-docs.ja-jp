---
title: IF-WHILE EXISTS のシミュレーション - ネイティブ コンパイル モジュール
description: SQL Server のネイティブ コンパイル ストアド プロシージャでサポートされていない条件付きステートメントで EXISTS 句をシミュレートする方法について説明します。
ms.custom: seo-dt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0438806d15caf806c4598f3d2b3882011d77d0f5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97485204"
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>ネイティブ コンパイル モジュールでの IF-WHILE EXISTS ステートメントのシミュレーション
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  ネイティブ コンパイル ストアド プロシージャは、条件ステートメント (IF や WHILE など) の **EXISTS** 句をサポートしていません。  
  
 次の例は、SELECT ステートメントで BIT 変数を使用して EXISTS 句をシミュレートするための回避策を表しています。  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](./a-guide-to-query-processing-for-memory-optimized-tables.md)   
 [インメモリ OLTP でサポートされていない Transact-SQL の構造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
