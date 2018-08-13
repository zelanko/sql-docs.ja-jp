---
title: ストアド プロシージャの呼び出しをバッチ処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 59b0ff710717f401cba9f7e6ae6fa44907ad3086
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553142"
---
# <a name="batching-stored-procedure-calls"></a>ストアド プロシージャ呼び出しのバッチ化
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ストアド プロシージャの呼び出し時に適切なサーバーに自動的にバッチ処理します。 これが行われるのは、ODBC CALL エスケープ シーケンスが使用されている場合のみです。[!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE ステートメントでは、この処理は行われません。 ストアド プロシージャ呼び出しをバッチにまとめると、サーバーとのやり取りの回数を削減できるので、パフォーマンスが大幅に向上します。  
  
 複数の ODBC CALL エスケープ シーケンスを含むバッチを実行すると、ドライバーによりサーバーへのプロシージャ呼び出しがバッチにまとめられます。 また、ODBC CALL エスケープ シーケンスでバインドされたパラメーター配列を使用するときも、プロシージャ呼び出しがバッチにまとめられます。 たとえば、5 つの要素を含む配列を ODBC CALL SQL ステートメントのパラメーターにバインドするか行方向または列方向のパラメーターのバインドを使用するときに**SQLExecute**または**SQLExecDirect**が呼び出され、ドライバーは、サーバーに 5 つのプロシージャ呼び出しで 1 つのバッチを送信します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
